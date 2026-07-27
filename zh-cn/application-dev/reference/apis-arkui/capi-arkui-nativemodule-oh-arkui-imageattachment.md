# OH_ArkUI_ImageAttachment
 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_ImageAttachment OH_ArkUI_ImageAttachment
```

## 概述

定义图片样式对象。 <br>        可以通过[OH_ArkUI_ImageAttachment_Create](capi-styled-string-h.md#oh_arkui_imageattachment_create)接口创建对应的图片样式对象。 <br>        可以通过[OH_ArkUI_ImageAttachment_Destroy](capi-styled-string-h.md#oh_arkui_imageattachment_destroy)接口销毁图片样式对象。 <br>        对象创建后通过OH_ArkUI_ImageAttachment_SetXXX系列接口设置生效的具体样式，例如通过[OH_ArkUI_ImageAttachment_SetPixelMap](capi-styled-string-h.md#oh_arkui_imageattachment_setpixelmap)设置图片源。

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [styled_string.h](capi-styled-string-h.md)