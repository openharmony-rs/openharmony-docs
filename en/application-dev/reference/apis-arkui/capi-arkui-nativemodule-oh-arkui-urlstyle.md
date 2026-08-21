# OH_ArkUI_UrlStyle

 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=2c5ecf1461774eee81076a9dfbe0054fd9d94ff3 translatedAt=2026-08-21T04:08:36.065Z pushedAt=2026-08-21T06:58:33.931Z -->

```c
typedef struct OH_ArkUI_UrlStyle OH_ArkUI_UrlStyle
```

## Overview

Defines a URL style used to set a tappable URL effect for text in a styled string. It applies to scenarios where interactive links need to be embedded in text content, improving text interactivity and user experience.<br>Call [OH_ArkUI_UrlStyle_Create](capi-styled-string-h.md#oh_arkui_urlstyle_create) to create a URL style object.<br>Call [OH_ArkUI_UrlStyle_Destroy](capi-styled-string-h.md#oh_arkui_urlstyle_destroy) to destroy the URL style object.<br>After creating the URL style object, call [OH_ArkUI_UrlStyle_SetUrl](capi-styled-string-h.md#oh_arkui_urlstyle_seturl) to set the URL.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)