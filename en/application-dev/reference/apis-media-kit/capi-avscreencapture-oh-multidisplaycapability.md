# OH_MultiDisplayCapability
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7cb32cf558e3c75482fc3404f1f7c011a4ecb00a translatedAt=2026-09-15T16:55:04.284Z pushedAt=2026-09-20T06:47:06.136Z -->

```c
typedef struct OH_MultiDisplayCapability {...} OH_MultiDisplayCapability
```

## Overview

Defines a struct for the multi-screen recording capability. It includes whether the multi-screen supports joint recording and the width and height of the screen for joint recording. Joint recording refers to recording the content of multiple screens into one video file at the same time. This struct allows you to query the joint recording capability of a multi-screen device, helping you determine whether the current device supports recording multiple screens at the same time. It is applicable to scenarios that require cross-screen recording, such as conference presentations, game recording, and teaching. With the joint recording capability, users can capture the content of multiple screens at once, improving recording efficiency and content integrity.

**Since**: 24

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| bool isMultiDisplaySupport | Whether multi-screen joint recording is supported. The value **true** indicates it is supported. In this case, **width** and **height** indicate the dimensions of the joint recording area. The value **false** indicates it is not supported. In this case, **width** and **height** are invalid. |
| uint32_t width | Width of the screen area for multi-screen joint recording, in pixels. When **isMultiDisplaySupport** is set to **true**, this parameter indicates the width of the joint recording area for all selected screens. When **isMultiDisplaySupport** is set to **false**, this parameter is invalid. |
| uint32_t height | Height of the screen area for multi-screen joint recording, in pixels. When **isMultiDisplaySupport** is set to **true**, this parameter indicates the height of the joint recording area for all selected screens. When **isMultiDisplaySupport** is set to **false**, this parameter is invalid. |