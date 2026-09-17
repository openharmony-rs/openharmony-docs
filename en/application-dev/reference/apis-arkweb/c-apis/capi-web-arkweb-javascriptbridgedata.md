# ArkWeb_JavaScriptBridgeData

```c
typedef struct ArkWeb_JavaScriptBridgeData {...} ArkWeb_JavaScriptBridgeData
```

## Overview

ArkWeb_JavaScriptBridgeData is a struct that defines JavaScript bridge data, used to transfer JavaScript bridge-related data between native code and web pages. This struct encapsulates the parameter data in bridge calls and serves as the basic data unit in the JavaScript bridge subsystem, working in conjunction with the JavaScript Proxy registration APIs in ArkWeb_ControllerAPI.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const uint8_t* buffer | Pointer to the transmitted data. Supports String and ArrayBuffer types. Other types are JSON-serialized and passed as String. |
| size_t size | Length of the transmitted data. It is recommended to set this value appropriately based on the actual data size and keep it consistent with the buffer size to avoid performance or data issues caused by excessively large or small values. |


