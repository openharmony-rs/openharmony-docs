# ArkWeb_ResourceHandler_
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=45c7180cb24e021bb9a06a985404826332a43fd8 translatedAt=2026-11-04T11:55:03.654Z pushedAt=2026-11-04T11:56:03.452Z nl=1 -->

```c
typedef struct ArkWeb_ResourceHandler_ ArkWeb_ResourceHandler
```

## Overview

The ArkWeb_ResourceHandler struct is a resource handler for processing intercepted scheme requests. After ArkWeb_SchemeHandler intercepts a request of a specified scheme, this struct can be used to return custom response data to the Web component, including the response status code, response headers, and response body. This struct is passed as a parameter in the onRequestStart callback, through which developers can implement fully custom responses to intercepted requests.

**Since**: 12

**Related module**: [Web](capi-web.md)

**System capability**: SystemCapability.Web.Webview.Core

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)

