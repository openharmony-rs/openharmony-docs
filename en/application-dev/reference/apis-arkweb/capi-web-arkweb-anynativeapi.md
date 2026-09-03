# ArkWeb_AnyNativeAPI

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @csliutt-private-->
<!--Designer: @ringking0-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=9c41f9fad7f6d910dff2a356347531b943719c3e translatedAt=2026-08-03T09:47:02.365Z pushedAt=2026-08-05T10:12:00.053Z -->

```c
typedef struct {...} ArkWeb_AnyNativeAPI
```

## Overview

ArkWeb_AnyNativeAPI is the basic struct type of ArkWeb Native API, used to uniformly represent pointers to various Native API structs obtained through the [OH_ArkWeb_GetNativeAPI](capi-arkweb-interface-h.md#oh_arkweb_getnativeapi) API. This struct contains a size member of the size_t type, which records the size of the current struct.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_interface.h](capi-arkweb-interface-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| size_t size | Size of the struct.|