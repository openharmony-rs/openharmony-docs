# ArkUI_DragAction

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-19T04:17:35.816Z pushedAt=2026-08-19T07:18:45.266Z -->

```c
typedef struct ArkUI_DragAction ArkUI_DragAction
```

## Overview

Defines a drag action handle, which is used to proactively initiate dragging, where you proactively call an API to start dragging, as opposed to passively responding to drag events. This handle supports creating, configuring, executing, and destroying a drag action. You can set drag data and proactively start dragging.

The usage process of **ArkUI_DragAction** is as follows:

1. Create an object by calling [OH_ArkUI_CreateDragActionWithNode](capi-drag-and-drop-h.md#oh_arkui_createdragactionwithnode) or [OH_ArkUI_CreateDragActionWithContext](capi-drag-and-drop-h.md#oh_arkui_createdragactionwithcontext).

2. Set drag parameters by calling APIs such as **OH_ArkUI_DragAction_SetData**.

3. Start dragging by calling [OH_ArkUI_StartDrag](capi-drag-and-drop-h.md#oh_arkui_startdrag).

4. When the object is no longer needed, call [OH_ArkUI_DragAction_Dispose](capi-drag-and-drop-h.md#oh_arkui_dragaction_dispose) to destroy the object and release resources.

For details about the creation, configuration, and execution mechanisms, see [Binding Drag Events](../../ui/ndk-drag-event.md).

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [drag_and_drop.h](capi-drag-and-drop-h.md)