# ArkWeb_ResourceRequest_
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=45c7180cb24e021bb9a06a985404826332a43fd8 translatedAt=2026-11-04T11:55:20.433Z pushedAt=2026-11-04T11:56:12.044Z nl=1 -->

```c
typedef struct ArkWeb_ResourceRequest_ ArkWeb_ResourceRequest
```

## Overview

ArkWeb_ResourceRequest is a struct that contains detailed information about an intercepted scheme request, including the request URL, HTTP method, request headers, and other metadata. This struct is passed as a parameter in the onRequestStart callback of ArkWeb_SchemeHandler and is applicable to scenarios such as custom protocol handling and resource interception. It helps developers implement features like cross-origin request control and local resource mapping, thereby enhancing security and performance. Developers can use it to obtain complete information about the intercepted request and decide whether to intercept it and how to construct a custom response.

**Since**: 12

**Related module**: [Web](capi-web.md)

**System capability**: SystemCapability.Web.Webview.Core

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)
