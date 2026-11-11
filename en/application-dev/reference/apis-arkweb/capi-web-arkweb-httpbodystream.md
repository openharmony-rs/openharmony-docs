# ArkWeb_HttpBodyStream_
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=9335f9431a5527342362c84e826071649d8c2b39 translatedAt=2026-11-06T11:46:22.400Z pushedAt=2026-11-09T11:42:23.714Z nl=1 -->

```c
typedef struct ArkWeb_HttpBodyStream_ ArkWeb_HttpBodyStream
```

## Overview

ArkWeb_HttpBodyStream is an HTTP request body stream structure used to obtain the body data of an HTTP request in custom Scheme request interception scenarios. When an HTTP request containing a request body, such as POST, is intercepted, the raw byte stream data of the request body can be read through this structure. This structure is usually used together with ArkWeb_ResourceRequest to obtain complete request information in the callback of ArkWeb_SchemeHandler.

**Since**: 12

**Related module**: [Web](capi-web.md)

**System capability**: SystemCapability.Web.Webview.Core

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)

