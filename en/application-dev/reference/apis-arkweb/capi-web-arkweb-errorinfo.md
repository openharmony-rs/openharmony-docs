# ArkWeb_ErrorInfo_
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-11-02T14:05:14.879Z pushedAt=2026-11-03T03:45:49.440Z nl=1 -->

```c
typedef struct ArkWeb_ErrorInfo_ ArkWeb_ErrorInfo
```

## Overview

ArkWeb_ErrorInfo is a response error detail structure used to set response error information in custom scheme request interception scenarios. Developers can use this structure to set the error code, custom error code, and whether to automatically generate a response when no response is received. This structure is typically used together with ArkWeb_ResourceHandler to pass error information through OH_ArkWebResourceHandler_DidFailWithErrorInfo when a request fails.

**Since:** 26.0.1

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)
