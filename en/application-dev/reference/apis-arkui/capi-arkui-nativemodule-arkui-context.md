# ArkUI_Context
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_Context ArkUI_Context
```

## Overview

Defines a context object of the ArkUI native UI, which is used to represent the UI context of the page where the component is located. The pointer type is [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md). You can obtain the context using [OH_ArkUI_GetContextByNode](capi-native-node-h.md#oh_arkui_getcontextbynode) and use it as the input parameter for APIs such as dragging, animation, and UI task scheduling.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [drag_and_drop.h](capi-drag-and-drop-h.md)
