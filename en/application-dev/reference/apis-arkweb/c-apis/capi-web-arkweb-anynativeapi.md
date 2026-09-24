# ArkWeb_AnyNativeAPI

```c
typedef struct ArkWeb_AnyNativeAPI {...} ArkWeb_AnyNativeAPI
```

## Overview

ArkWeb_AnyNativeAPI is the basic struct type of ArkWeb Native API, used to uniformly represent pointers to various Native API structs obtained through the {@link OH_ArkWeb_GetNativeAPI} API. This struct contains a size member of the size_t type, which records the size of the current struct.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_interface.h](capi-arkweb-interface-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t size | Size of the struct. |


