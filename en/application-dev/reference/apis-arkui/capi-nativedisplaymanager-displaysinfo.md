# NativeDisplayManager_DisplaysInfo
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=b5bac46b123c8ef772e6a1f04f3d13c5b3c45368 translatedAt=2026-11-18T09:09:11.890Z pushedAt=2026-11-20T01:48:44.376Z nl=1 -->

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


