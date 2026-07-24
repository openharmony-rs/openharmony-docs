# xcomponent.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines the enumerations of the **XComponent** component.

**File to include:** <arkui/node_attributes/xcomponent.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample:** <!--RP1-->[xcomponent_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Native/XComponent3D)<!--RP1End-->

## Summary

### Enums

| Name                                                                 | typedef Keyword                     | Description                               |
|---------------------------------------------------------------------|---------------------------------|-----------------------------------|
| [ArkUI_XComponentType](#arkui_xcomponenttype)                       | ArkUI_XComponentType            | Enumerates the types of the **XComponent** component.               |

## Enumeration Description

### ArkUI_XComponentType

```c
enum ArkUI_XComponentType
```

**Description**

Enumerates the types of the **XComponent** component.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_XCOMPONENT_TYPE_SURFACE = 0 | The custom content of EGL/OpenGL ES and media data is displayed individually on the screen.|
| ARKUI_XCOMPONENT_TYPE_TEXTURE = 2 | The custom content of EGL/OpenGL ES and media data is grouped and displayed together with content of the component.|
