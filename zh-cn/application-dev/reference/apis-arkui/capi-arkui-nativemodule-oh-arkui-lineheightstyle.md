# OH_ArkUI_LineHeightStyle
 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_LineHeightStyle OH_ArkUI_LineHeightStyle
```

## 概述

定义行高样式。 <br>        可以通过[OH_ArkUI_LineHeightStyle_Create](capi-styled-string-h.md#oh_arkui_lineheightstyle_create)接口创建对应的行高样式对象。 <br>        可以通过[OH_ArkUI_LineHeightStyle_Destroy](capi-styled-string-h.md#oh_arkui_lineheightstyle_destroy)接口销毁行高样式对象。 <br>        对象创建后可以通过[OH_ArkUI_LineHeightStyle_SetLineHeight](capi-styled-string-h.md#oh_arkui_lineheightstyle_setlineheight)接口设置具体的固定行高值。<br>        从API版本26.0.0开始，对象创建后可以通过[OH_ArkUI_LineHeightStyle_SetLineHeightMultiple](capi-styled-string-h.md#oh_arkui_lineheightstyle_setlineheightmultiple)接口设置具体的行高的倍数值。

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [styled_string.h](capi-styled-string-h.md)