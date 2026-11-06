# OH_ArkUI_BaselineOffsetStyle

 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7a1ca9ecda174593f2f5bfe9776ee27ebc5c3110 translatedAt=2026-08-21T01:45:49.190Z pushedAt=2026-08-21T03:38:52.537Z -->

```c
typedef struct OH_ArkUI_BaselineOffsetStyle OH_ArkUI_BaselineOffsetStyle
```

## Overview

Defines a baseline offset style, which is used to set the baseline offset of text in a styled string so that the text moves up or down relative to the baseline in the vertical direction, thereby achieving special typesetting effects such as superscripts and subscripts. The baseline offset style takes effect for the styled string only after a style object is created and the offset value is set.<br>Call [OH_ArkUI_BaselineOffsetStyle_Create](capi-styled-string-h.md#oh_arkui_baselineoffsetstyle_create) to create a baseline offset style object.<br>After the object is created, call [OH_ArkUI_BaselineOffsetStyle_SetBaselineOffset](capi-styled-string-h.md#oh_arkui_baselineoffsetstyle_setbaselineoffset) to set the baseline offset value.<br>Call [OH_ArkUI_BaselineOffsetStyle_GetBaselineOffset](capi-styled-string-h.md#oh_arkui_baselineoffsetstyle_getbaselineoffset) to obtain the baseline offset value.<br>After the object is used, call [OH_ArkUI_BaselineOffsetStyle_Destroy](capi-styled-string-h.md#oh_arkui_baselineoffsetstyle_destroy) to destroy it.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)