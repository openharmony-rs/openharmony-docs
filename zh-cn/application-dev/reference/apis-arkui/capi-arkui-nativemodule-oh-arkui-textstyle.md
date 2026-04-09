# OH_ArkUI_TextStyle
 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_TextStyle OH_ArkUI_TextStyle
```

## 概述

定义文本字体样式。 <br>        可以通过[OH_ArkUI_TextStyle_Create](capi-styled-string-h.md#oh_arkui_textstyle_create)接口创建对应的文本字体样式对象。 <br>        可以通过[OH_ArkUI_TextStyle_Destroy](capi-styled-string-h.md#oh_arkui_textstyle_destroy)接口销毁文本字体样式对象。 <br>        对象创建后通过OH_ArkUI_TextStyle_SetXXX系列接口设置生效的具体样式，例如通过[OH_ArkUI_TextStyle_SetFontColor](capi-styled-string-h.md#oh_arkui_textstyle_setfontcolor)设置字体颜色。

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [styled_string.h](capi-styled-string-h.md)