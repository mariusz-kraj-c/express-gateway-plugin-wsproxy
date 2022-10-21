# express-gateway-plugin-wsproxy

This plugin for [Express Gateway](https://express-gateway.io) makes it possible to proxy WebSocket connection to the specific WebSocket based on
[Express Paths](https://expressjs.com/en/guide/routing.html) or RegExp Rules.

## Installation

Simply type from your shell environment:

```bash
eg plugin install express-gateway-plugin-wsproxy
```

## Quick start

1. Make sure the plugin is listed in [system.config.yml file](https://www.express-gateway.io/docs/configuration/system.config.yml/).
   This is done automatically for you if you used the command above.

2. Add the configuration keys to [gateway.config.yml file](https://www.express-gateway.io/docs/configuration/gateway.config.yml/).

```yaml
  telemetry_ws:
    apiEndpoints:
      - ws_endpoint
    policies:
      - cors:
          - action:
              origin: '*'
              credentials: true
      - jwt:
          action:
            secretOrPublicKeyFile: public.pem
            checkCredentialExistence: false
            jwtExtractor: 'query'
            jwtExtractorField: 'token'
      - wsproxy:
          - action:
              serviceEndpoint: ws_endpoint
```
