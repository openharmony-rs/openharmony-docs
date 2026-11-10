# ArkWeb_ResourceHandler_
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=9335f9431a5527342362c84e826071649d8c2b39 translatedAt=2026-11-06T11:49:16.726Z pushedAt=2026-11-09T11:45:10.940Z nl=1 -->

```c
typedef struct ArkWeb_ResourceHandler_ ArkWeb_ResourceHandler
```

## Overview

The ArkWeb_ResourceHandler struct is a resource handler for processing intercepted scheme requests. After ArkWeb_SchemeHandler intercepts a request of a specified scheme, this struct can be used to return custom response data to the Web component, including the response status code, response headers, and response body. This struct is passed as a parameter in the onRequestStart callback, through which developers can implement fully custom responses to intercepted requests.

**Since**: 12

**Related module**: [Web](capi-web.md)

**System capability**: SystemCapability.Web.Webview.Core

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)

