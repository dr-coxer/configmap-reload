# Kubernetes ConfigMap Reload

[![license](https://img.shields.io/github/license/jimmidyson/configmap-reload.svg?maxAge=2592000)](https://github.com/jimmidyson/configmap-reload)

**configmap-reload** is a simple binary to trigger a reload when Kubernetes ConfigMaps or Secrets, mounted into pods,
are updated.
It watches mounted volume dirs and notifies the target process that the config map has been changed.
It currently only supports sending an HTTP request, but in future it is expected to support sending OS
(e.g. SIGHUP) once Kubernetes supports pod PID namespaces.

### Usage

```
Usage of ./out/configmap-reload:
  -volume-dir value
        the config map volume directory to watch for updates; may be used multiple times
  -web.listen-address string
    	  address to listen on for web interface and telemetry. (default ":9533")
  -web.telemetry-path string
    	  path under which to expose metrics. (default "/metrics")
  -webhook-method string
        the HTTP method url to use to send the webhook (default "POST")
  -webhook-status-code int
        the HTTP status code indicating successful triggering of reload (default 200)
  -webhook-url string
        the url to send a request to when the specified config map volume directory has been updated
  -webhook-header-key
        the HTTP header key to use to send the webhook (GET method only)
  -webhook-header-value
        the HTTP header value to use to send the webhook (GET method only)
  -webhook-retries integer
        the amount of times to retry the webhook reload request
```

### License

This project is [Apache Licensed](LICENSE.txt)

