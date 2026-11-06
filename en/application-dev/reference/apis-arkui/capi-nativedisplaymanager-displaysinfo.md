# NativeDisplayManager_DisplaysInfo
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @logn; @wulong158-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=00aa695a42976a3a58a556fb5c9c98adb86b2fa2 translatedAt=2026-08-27T08:38:20.295Z pushedAt=2026-08-27T12:03:37.083Z -->

```c
typedef struct {...} NativeDisplayManager_DisplaysInfo
```

## Overview

Describes the information about displays of a device with multiple screens.

**Since**: 14

**Related module**: [OH_DisplayManager](capi-oh-displaymanager.md)

**Header file**: [oh_display_info.h](capi-oh-display-info-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t displaysLength | Number of displays of a device with multiple screens.|
| [NativeDisplayManager_DisplayInfo](capi-nativedisplaymanager-displayinfo.md)* displaysInfo | Pointer to the array of **NativeDisplayManager_DisplayInfo** structs, each containing information about a display.|


