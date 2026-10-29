# NativeDisplayManager_DisplaysInfo
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=494f31a35d1b25179fe202754d9ee44d527d8ab6 translatedAt=2026-10-10T10:28:28.872Z pushedAt=2026-10-15T01:41:44.644Z -->

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


