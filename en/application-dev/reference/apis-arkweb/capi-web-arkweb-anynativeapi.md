# ArkWeb_AnyNativeAPI
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @csliutt-private-->
<!--Designer: @ringking0-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=6bdb047b06c2b1518e79c4920c7da48a0febf49c translatedAt=2026-11-04T11:42:30.842Z pushedAt=2026-11-04T11:50:39.113Z nl=1 -->

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


