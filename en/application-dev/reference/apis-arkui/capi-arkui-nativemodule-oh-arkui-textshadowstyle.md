# OH_ArkUI_TextShadowStyle

 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=2c5ecf1461774eee81076a9dfbe0054fd9d94ff3 translatedAt=2026-08-21T04:08:16.992Z pushedAt=2026-08-21T06:53:28.802Z -->

```c
typedef struct OH_ArkUI_TextShadowStyle OH_ArkUI_TextShadowStyle
```

## Overview

Defines a text shadow style, which includes attributes such as the shadow offset, blur radius, and color. It is used to add shadow effects to text, such as highlighting title text and enhancing text on a dark background.<br>Call [OH_ArkUI_TextShadowStyle_Create](capi-styled-string-h.md#oh_arkui_textshadowstyle_create) to create a text shadow style object.<br>Call [OH_ArkUI_TextShadowStyle_Destroy](capi-styled-string-h.md#oh_arkui_textshadowstyle_destroy) to destroy the text shadow style object.<br>After creating the text shadow style object, call [OH_ArkUI_TextShadowStyle_SetTextShadow](capi-styled-string-h.md#oh_arkui_textshadowstyle_settextshadow) to set the specific text shadow style.<br>Call [OH_ArkUI_TextShadowStyle_GetTextShadow](capi-styled-string-h.md#oh_arkui_textshadowstyle_gettextshadow) to obtain the text shadow style that has been set.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)