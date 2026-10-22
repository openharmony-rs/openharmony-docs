# OH_ArkUI_GestureStyle

 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7a1ca9ecda174593f2f5bfe9776ee27ebc5c3110 translatedAt=2026-08-21T04:06:45.016Z pushedAt=2026-08-21T06:03:01.827Z -->

```c
typedef struct OH_ArkUI_GestureStyle OH_ArkUI_GestureStyle
```

## Overview

Defines a gesture style. It applies to scenarios where a gesture style needs to be configured and related event callbacks need to be received, making it easier for an application to manage gesture styles and event callbacks in a unified manner. <br>Call [OH_ArkUI_GestureStyle_Create](capi-styled-string-h.md#oh_arkui_gesturestyle_create) to create the corresponding gesture style object.<br>After the object is created, call the **OH_ArkUI_GestureStyle_RegisterOnXXXCallback** series APIs to register specific event callbacks, for example, call [OH_ArkUI_GestureStyle_RegisterOnClickCallback](capi-styled-string-h.md#oh_arkui_gesturestyle_registeronclickcallback) to register the click event callback.<br>After use, call [OH_ArkUI_GestureStyle_Destroy](capi-styled-string-h.md#oh_arkui_gesturestyle_destroy) to destroy the gesture style object.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)