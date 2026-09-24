# Netstack

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4d1029d6dff030e016f628c7b2929658d13e09ce translatedAt=2026-09-23T01:34:48.508Z pushedAt=2026-09-24T06:00:14.137Z -->

## Overview

Provides C APIs for network-related modules, including SSL/TLS certificate chain verification, WebSocket client, HTTP request, and global HTTP interceptor.

Calling paradigm: taking an HTTP request as an example, the typical calling process is: create a request instance, set request parameters, initiate the request, obtain the response, and destroy the instance. For the WebSocket client, the APIs must be called in the order of creating an instance, connecting to the server, sending and receiving data, and closing the connection. For SSL/TLS certificate chain verification, the certificate chain must be loaded and verified before initiating a network request. The global HTTP interceptor must be registered before use and unregistered when no longer needed.

**Since**: 11
## Files

| Name| Description|
| -- | -- |
| [net_ssl_c.h](capi-net-ssl-c-h.md) | Defines the C APIs of the SSL/TLS certificate chain verification module.|
| [net_ssl_c_type.h](capi-net-ssl-c-type-h.md) | Defines data structures for the C APIs of the SSL/TLS certificate chain verification module.|
| [net_websocket.h](capi-net-websocket-h.md) | Defines the APIs of the WebSocket client module. |
| [net_websocket_type.h](capi-net-websocket-type-h.md) | Defines the C API data structures required by the WebSocket client module. |
| [net_http.h](capi-net-http-h.md) | Defines the APIs of the HTTP request module.|
| [net_http_type.h](capi-net-http-type-h.md) | Defines the data structures for the C APIs of the HTTP request module.|
| [http_interceptor.h](capi-net-http-interceptor-h.md) | Defines the APIs of the global HTTP interceptor module.|
| [http_interceptor_type.h](capi-net-http-interceptor-type-h.md) | Defines the data structures for the C APIs of the global HTTP interceptor module.|
