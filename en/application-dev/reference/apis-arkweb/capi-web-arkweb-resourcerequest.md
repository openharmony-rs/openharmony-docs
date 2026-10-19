# ArkWeb_ResourceRequest_

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=3cf0e4d31df69a8bda793fe15a55a60676b46acc translatedAt=2026-08-03T09:53:59.630Z pushedAt=2026-08-06T11:52:18.734Z -->

```c
typedef struct ArkWeb_ResourceRequest_ ArkWeb_ResourceRequest
```

## Overview

ArkWeb_ResourceRequest is a struct that contains detailed information about an intercepted scheme request, including the request URL, HTTP method, request headers, and other metadata. This struct is passed as a parameter in the onRequestStart callback of ArkWeb_SchemeHandler and is applicable to scenarios such as custom protocol handling and resource interception. It helps developers implement features like cross-origin request control and local resource mapping, thereby enhancing security and performance. Developers can use it to obtain complete information about the intercepted request and decide whether to intercept it and how to construct a custom response.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)