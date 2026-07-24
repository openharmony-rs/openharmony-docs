# OH_ArkUI_LineSpacingStyle
 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_LineSpacingStyle OH_ArkUI_LineSpacingStyle
```

## 概述

定义行间距样式。 <br>        可以通过[OH_ArkUI_LineSpacingStyle_Create](capi-styled-string-h.md#oh_arkui_linespacingstyle_create)接口创建对应的行间距样式对象，通过[OH_ArkUI_LineSpacingStyle_Destroy](capi-styled-string-h.md#oh_arkui_linespacingstyle_destroy)接口销毁行间距样式对象。 <br>        对象创建后可以通过[OH_ArkUI_LineSpacingStyle_SetLineSpacing](capi-styled-string-h.md#oh_arkui_linespacingstyle_setlinespacing)接口设置具体的行间距值，通过[OH_ArkUI_LineSpacingStyle_SetOnlyBetweenLines](capi-styled-string-h.md#oh_arkui_linespacingstyle_setonlybetweenlines)接口设置行间距是否只在行间生效。

**起始版本：** 26.0.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [styled_string.h](capi-styled-string-h.md)