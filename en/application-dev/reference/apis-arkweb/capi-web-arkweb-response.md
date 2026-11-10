# ArkWeb_Response_
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=9335f9431a5527342362c84e826071649d8c2b39 translatedAt=2026-11-06T11:49:27.105Z pushedAt=2026-11-09T11:45:40.323Z nl=1 -->

```c
typedef struct ArkWeb_Response_ ArkWeb_Response
```

## Overview

ArkWeb_Response is a structure used to construct custom HTTP responses, defining core fields such as the response status code, response headers, and response body. Used together with ArkWeb_ResourceHandler, this structure provides complete HTTP response data for intercepted requests in Scheme request interception scenarios, enabling custom resource return capabilities.

**Since**: 12

**Related module**: [Web](capi-web.md)

**System capability**: SystemCapability.Web.Webview.Core

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)

