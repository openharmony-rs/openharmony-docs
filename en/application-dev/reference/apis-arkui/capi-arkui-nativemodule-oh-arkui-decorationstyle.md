# OH_ArkUI_DecorationStyle

 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7a1ca9ecda174593f2f5bfe9776ee27ebc5c3110 translatedAt=2026-08-21T01:46:13.511Z pushedAt=2026-08-21T03:42:58.123Z -->

```c
typedef struct OH_ArkUI_DecorationStyle OH_ArkUI_DecorationStyle
```

## Overview

Defines a text decoration style, supporting decorative line effects such as underline and strikethrough for text. It applies to scenarios where the appearance of text decorative lines needs to be customized, helping you flexibly control the type, color, and style of text decorative lines.<br>Call [OH_ArkUI_DecorationStyle_Create](capi-styled-string-h.md#oh_arkui_decorationstyle_create) to create a text decoration style object.<br>After the object is created, call the **OH_ArkUI_DecorationStyle_SetXXX** series APIs to set specific styles. For example, call [OH_ArkUI_DecorationStyle_SetTextDecorationType](capi-styled-string-h.md#oh_arkui_decorationstyle_settextdecorationtype) to set the decorative line type.<br>After the object is used, call [OH_ArkUI_DecorationStyle_Destroy](capi-styled-string-h.md#oh_arkui_decorationstyle_destroy) to destroy it.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)