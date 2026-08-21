# OH_ArkUI_BackgroundColorStyle

 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7a1ca9ecda174593f2f5bfe9776ee27ebc5c3110 translatedAt=2026-08-21T01:45:47.179Z pushedAt=2026-08-21T03:35:14.493Z -->

```c
typedef struct OH_ArkUI_BackgroundColorStyle OH_ArkUI_BackgroundColorStyle
```

## Overview

Defines a background color style, which supports customizing the background color and corner radius. It is used to set a background highlight effect for a styled string, for example, search result highlighting, key text marking, and label-style text display, to improve the visual hierarchy and recognizability of text.<br>Call [OH_ArkUI_BackgroundColorStyle_Create](capi-styled-string-h.md#oh_arkui_backgroundcolorstyle_create) to create a background color style object.<br>After the object is created, call [OH_ArkUI_BackgroundColorStyle_SetColor](capi-styled-string-h.md#oh_arkui_backgroundcolorstyle_setcolor) and [OH_ArkUI_BackgroundColorStyle_SetRadius](capi-styled-string-h.md#oh_arkui_backgroundcolorstyle_setradius) to set the background color and corner radius.<br>Call [OH_ArkUI_BackgroundColorStyle_GetColor](capi-styled-string-h.md#oh_arkui_backgroundcolorstyle_getcolor) and [OH_ArkUI_BackgroundColorStyle_GetRadius](capi-styled-string-h.md#oh_arkui_backgroundcolorstyle_getradius) to obtain the background color and corner radius.<br>After the object is used, call [OH_ArkUI_BackgroundColorStyle_Destroy](capi-styled-string-h.md#oh_arkui_backgroundcolorstyle_destroy) to destroy it.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)