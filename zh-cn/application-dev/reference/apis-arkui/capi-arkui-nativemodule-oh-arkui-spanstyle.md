# OH_ArkUI_SpanStyle
 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_SpanStyle OH_ArkUI_SpanStyle
```

## 概述

定义属性字符串样式对象。 <br>        可以通过[OH_ArkUI_SpanStyle_Create](capi-styled-string-h.md#oh_arkui_spanstyle_create)接口创建对应的属性字符串样式对象。 <br>        可以通过[OH_ArkUI_SpanStyle_Destroy](capi-styled-string-h.md#oh_arkui_spanstyle_destroy)接口销毁属性字符串样式对象。 <br>        对象创建后通过[OH_ArkUI_SpanStyle_SetStart](capi-styled-string-h.md#oh_arkui_spanstyle_setstart)和[OH_ArkUI_SpanStyle_SetLength](capi-styled-string-h.md#oh_arkui_spanstyle_setlength)指定样式作用的范围。 <br>        对象创建后通过OH_ArkUI_SpanStyle_SetXXXStyle系列接口设置生效的具体样式，例如通过[OH_ArkUI_SpanStyle_SetTextStyle](capi-styled-string-h.md#oh_arkui_spanstyle_settextstyle)设置字体样式效果。

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [styled_string.h](capi-styled-string-h.md)