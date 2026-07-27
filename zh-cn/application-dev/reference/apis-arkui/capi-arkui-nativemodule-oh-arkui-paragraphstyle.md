# OH_ArkUI_ParagraphStyle
 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_ParagraphStyle OH_ArkUI_ParagraphStyle
```

## 概述

定义段落样式。 <br>        可以通过[OH_ArkUI_ParagraphStyle_Create](capi-styled-string-h.md#oh_arkui_paragraphstyle_create)接口创建对应的段落样式对象。 <br>        可以通过[OH_ArkUI_ParagraphStyle_Destroy](capi-styled-string-h.md#oh_arkui_paragraphstyle_destroy)接口销毁段落样式对象。 <br>        对象创建后通过OH_ArkUI_ParagraphStyle_SetXXX系列接口设置生效的具体样式，例如通过[OH_ArkUI_ParagraphStyle_SetTextAlign](capi-styled-string-h.md#oh_arkui_paragraphstyle_settextalign)设置文本对齐方式。

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [styled_string.h](capi-styled-string-h.md)