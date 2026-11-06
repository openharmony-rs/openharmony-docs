# OH_ArkUI_ImageAttachment

 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=2c5ecf1461774eee81076a9dfbe0054fd9d94ff3 translatedAt=2026-08-21T04:06:44.923Z pushedAt=2026-08-21T06:04:45.799Z -->

```c
typedef struct OH_ArkUI_ImageAttachment OH_ArkUI_ImageAttachment
```

## Overview

Defines an image object used to embed image content in a styled string. As a component of the styled string, the image can be attached to the styled string to implement mixed text and image layout after the image source and style attributes are set.<br>Call [OH_ArkUI_ImageAttachment_Create](capi-styled-string-h.md#oh_arkui_imageattachment_create) to create an image style object.<br>Call [OH_ArkUI_ImageAttachment_Destroy](capi-styled-string-h.md#oh_arkui_imageattachment_destroy) to destroy the image style object.<br>After the object is created, call the **OH_ArkUI_ImageAttachment_SetXXX** series APIs to set style attributes, for example, call [OH_ArkUI_ImageAttachment_SetPixelMap](capi-styled-string-h.md#oh_arkui_imageattachment_setpixelmap) to set the image source.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)