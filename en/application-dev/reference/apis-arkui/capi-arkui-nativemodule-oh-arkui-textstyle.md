# OH_ArkUI_TextStyle
 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c5dd4bab7b6a1b4fcec6d309a7c458e4b5f07035 translatedAt=2026-09-22T09:29:28.015Z pushedAt=2026-09-22T12:00:01.435Z -->

```c
typedef struct OH_ArkUI_TextStyle OH_ArkUI_TextStyle
```

## Overview

Defines a text font style, which is used to set attributes such as the font color, size, and style of text. It is applicable to scenarios where text display effects need to be customized.<br>Call [OH_ArkUI_TextStyle_Create](capi-styled-string-h.md#oh_arkui_textstyle_create) to create a text font style object.<br>Call [OH_ArkUI_TextStyle_Destroy](capi-styled-string-h.md#oh_arkui_textstyle_destroy) to destroy the text font style object. After destruction, do not call the **OH_ArkUI_TextStyle_SetXXX** series APIs.<br>After the object is created successfully, call the **OH_ArkUI_TextStyle_SetXXX** series APIs to set specific styles. If creation fails, do not call the **SetXXX** series APIs. For example, call [OH_ArkUI_TextStyle_SetFontColor](capi-styled-string-h.md#oh_arkui_textstyle_setfontcolor) to set the font color.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)