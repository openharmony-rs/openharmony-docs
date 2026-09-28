# OH_ArkUI_CustomSpan
 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c5dd4bab7b6a1b4fcec6d309a7c458e4b5f07035 translatedAt=2026-09-22T09:21:31.105Z pushedAt=2026-09-22T11:49:38.770Z -->

```c
typedef struct OH_ArkUI_CustomSpan OH_ArkUI_CustomSpan
```

## Overview

Defines a custom span, which is used to implement custom measurement and drawing capabilities in a styled string. A custom span determines its placeholder size through the measurement callback and draws custom content in the corresponding area through the drawing callback, thereby embedding custom graphic elements into rich text.<br>Call [OH_ArkUI_CustomSpan_Create](capi-styled-string-h.md#oh_arkui_customspan_create) to create a custom span object.<br>After the object is created, call [OH_ArkUI_CustomSpan_RegisterOnMeasureCallback](capi-styled-string-h.md#oh_arkui_customspan_registeronmeasurecallback) to register the measurement callback.<br>Call [OH_ArkUI_CustomSpan_RegisterOnDrawCallback](capi-styled-string-h.md#oh_arkui_customspan_registerondrawcallback) to register the drawing callback.<br>Call [OH_ArkUI_CustomSpan_Destroy](capi-styled-string-h.md#oh_arkui_customspan_destroy) to destroy the custom span object.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)