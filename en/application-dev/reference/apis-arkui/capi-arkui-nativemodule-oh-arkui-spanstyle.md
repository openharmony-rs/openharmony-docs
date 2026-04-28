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

## Overview

Defines a styled string style.<br>        [OH_ArkUI_SpanStyle_Create](capi-styled-string-h.md#oh_arkui_spanstyle_create) can be used to create a styled string style object.<br>        [OH_ArkUI_SpanStyle_Destroy](capi-styled-string-h.md#oh_arkui_spanstyle_destroy) can be used to destroy the styled string style object.<br>        After the object is created, [OH_ArkUI_SpanStyle_SetStart](capi-styled-string-h.md#oh_arkui_spanstyle_setstart) and [OH_ArkUI_SpanStyle_SetLength](capi-styled-string-h.md#oh_arkui_spanstyle_setlength) can be used to set the usage scope of the style.<br>        After the object is created, the **OH_ArkUI_SpanStyle_SetXXXStyle** series APIs can be used to set the specific styles that take effect. For example, you can use [OH_ArkUI_SpanStyle_SetTextStyle](capi-styled-string-h.md#oh_arkui_spanstyle_settextstyle) to set the font style.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)

<!--no_check-->