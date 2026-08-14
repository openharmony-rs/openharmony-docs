# ArkWeb_SchemeHandler_

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=3cf0e4d31df69a8bda793fe15a55a60676b46acc translatedAt=2026-08-03T09:54:38.702Z pushedAt=2026-08-06T11:56:10.357Z -->

```c
typedef struct ArkWeb_SchemeHandler_ ArkWeb_SchemeHandler
```

## Overview

ArkWeb_SchemeHandler is a struct used to register custom scheme (protocol) interceptors. It defines two function pointers: the onRequestStart callback for request start and the onRequestStop callback for request stop. With this struct, network requests of a specified scheme in the Web component can be intercepted, which is applicable to scenarios such as resource localization, data simulation, request filtering, and protocol extension: in onRequestStart, whether to intercept is determined and custom data is returned; in onRequestStop, resource cleanup is performed; and onRequestStart and onRequestStop are called sequentially in the order of the request lifecycle. This struct works with ArkWeb_ResourceHandler and ArkWeb_Response to implement a complete request interception and custom response process. The call sequence is: ArkWeb_SchemeHandler intercepts the request → ArkWeb_ResourceHandler processes the resource → ArkWeb_Response returns the response.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)