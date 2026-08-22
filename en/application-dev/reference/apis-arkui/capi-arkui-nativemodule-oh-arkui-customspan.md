# OH_ArkUI_CustomSpan

 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=2c5ecf1461774eee81076a9dfbe0054fd9d94ff3 translatedAt=2026-08-21T01:46:05.847Z pushedAt=2026-08-21T03:40:44.166Z -->

```c
typedef struct OH_ArkUI_CustomSpan OH_ArkUI_CustomSpan
```

## Overview

Defines a custom span, which is used to implement custom measurement and drawing capabilities in a styled string. A custom span determines its placeholder size through the measurement callback and draws custom content in the corresponding area through the drawing callback, thereby embedding custom graphic elements into rich text.<br>Call [OH_ArkUI_CustomSpan_Create](capi-styled-string-h.md#oh_arkui_customspan_create) to create a custom span object.<br>After the object is created, call [OH_ArkUI_CustomSpan_RegisterOnMeasureCallback](capi-styled-string-h.md#oh_arkui_customspan_registeronmeasurecallback) to register the measurement callback.<br>Call [OH_ArkUI_CustomSpan_RegisterOnDrawCallback](capi-styled-string-h.md#oh_arkui_customspan_registerondrawcallback) to register the drawing callback.<br>Call [OH_ArkUI_CustomSpan_Destroy](capi-styled-string-h.md#oh_arkui_customspan_destroy) to destroy the custom span object.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)