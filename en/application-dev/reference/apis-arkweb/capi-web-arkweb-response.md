# ArkWeb_Response_
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=45c7180cb24e021bb9a06a985404826332a43fd8 translatedAt=2026-11-04T11:55:40.948Z pushedAt=2026-11-04T11:56:26.184Z nl=1 -->

```c
typedef struct ArkWeb_Response_ ArkWeb_Response
```

## Overview

ArkWeb_Response is a structure used to construct custom HTTP responses, defining core fields such as the response status code, response headers, and response body. Used together with ArkWeb_ResourceHandler, this structure provides complete HTTP response data for intercepted requests in Scheme request interception scenarios, enabling custom resource return capabilities.

**Since**: 12

**Related module**: [Web](capi-web.md)

**System capability**: SystemCapability.Web.Webview.Core

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)

