# ArkWeb_ErrorInfo_
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=ce754e12ad79ec009dd688c2e7abc9ae3f194d2c translatedAt=2026-11-04T11:48:54.307Z pushedAt=2026-11-04T11:54:39.651Z nl=1 -->

```c
typedef struct ArkWeb_ErrorInfo_ ArkWeb_ErrorInfo
```

## Overview

ArkWeb_ErrorInfo is a response error detail structure used to set response error information in custom scheme request interception scenarios. Developers can use this structure to set the error code, custom error code, and whether to automatically generate a response when no response is received. This structure is typically used together with ArkWeb_ResourceHandler to pass error information through OH_ArkWebResourceHandler_DidFailWithErrorInfo when a request fails.

**Since:** 26.0.1

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)
