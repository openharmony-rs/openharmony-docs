# OH_ArkUI_LineSpacingStyle

 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7a1ca9ecda174593f2f5bfe9776ee27ebc5c3110 translatedAt=2026-08-21T04:07:13.848Z pushedAt=2026-08-21T06:17:19.195Z -->

```c
typedef struct OH_ArkUI_LineSpacingStyle OH_ArkUI_LineSpacingStyle
```

## Overview

Defines a line spacing style, which is used to set the spacing between text lines to improve text readability and visual effect. It applies to scenarios that require fine-grained control over the line spacing of multi-line text layout, such as e-book readers, news and information applications, and editors for long documents.<br>Call [OH_ArkUI_LineSpacingStyle_Create](capi-styled-string-h.md#oh_arkui_linespacingstyle_create) to create a line spacing style object. The default line spacing value is **0**, and whether the line spacing takes effect only between lines defaults to **false**.<br>Call [OH_ArkUI_LineSpacingStyle_Destroy](capi-styled-string-h.md#oh_arkui_linespacingstyle_destroy) to destroy the line spacing style object.<br>After the object is created, call [OH_ArkUI_LineSpacingStyle_SetLineSpacing](capi-styled-string-h.md#oh_arkui_linespacingstyle_setlinespacing) to set the line spacing value. For details about the value range and constraints, see the description of this API.<br>Call [OH_ArkUI_LineSpacingStyle_SetOnlyBetweenLines](capi-styled-string-h.md#oh_arkui_linespacingstyle_setonlybetweenlines) to set whether the line spacing takes effect only between lines. For details about the value principle, see the description of this API.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)