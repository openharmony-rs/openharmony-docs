# ArkWeb_ErrorInfo_

```c
typedef struct ArkWeb_ErrorInfo_ ArkWeb_ErrorInfo
```

## Overview

ArkWeb_ErrorInfo is a structure that details response errors, used to set error information for responses in custom scheme request interception scenarios. Developers can use this structure to configure the error code, custom error code, and whether to automatically generate a response when no response is received. This structure is typically used in conjunction with ArkWeb_ResourceHandler to pass error information via OH_ArkWebResourceHandler_DidFailWithErrorInfo when a request fails.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 26.0.1

**Related module**: [Web](capi-others-web.md)

**Header file**: [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)

