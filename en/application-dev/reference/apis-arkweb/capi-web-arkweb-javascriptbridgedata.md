# ArkWeb_JavaScriptBridgeData
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T11:52:21.127Z pushedAt=2026-11-04T11:54:57.233Z nl=1 -->

```c
typedef struct {...} ArkWeb_JavaScriptBridgeData
```

## Overview

ArkWeb_JavaScriptBridgeData is a struct that defines JavaScript bridge data, used to transfer JavaScript bridge-related data between native code and web pages. This struct encapsulates the parameter data in bridge calls and serves as the basic data unit in the JavaScript bridge subsystem, working in conjunction with the JavaScript Proxy registration APIs in ArkWeb_ControllerAPI.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const uint8_t* buffer | Pointer to the transmitted data. Both String and ArrayBuffer types are supported. Other types are passed as String after JSON serialization. |
| size_t size | Length of the transmitted data. It is recommended to set this value appropriately based on the actual data size and keep it consistent with the buffer size to avoid performance or data issues caused by excessively large or small values. |


