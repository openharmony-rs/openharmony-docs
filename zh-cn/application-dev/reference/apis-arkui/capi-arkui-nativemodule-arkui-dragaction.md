# ArkUI_DragAction
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_DragAction ArkUI_DragAction
```

## 概述

拖拽行为句柄，用于主动发起拖拽操作，即由开发者主动调用接口启动拖拽，区别于被动响应拖拽事件。该句柄支持创建、配置、执行和销毁拖拽行为，可设置拖拽数据并主动启动拖拽。

ArkUI_DragAction的使用流程如下：

1. 通过[OH_ArkUI_CreateDragActionWithNode](capi-drag-and-drop-h.md#oh_arkui_createdragactionwithnode)或[OH_ArkUI_CreateDragActionWithContext](capi-drag-and-drop-h.md#oh_arkui_createdragactionwithcontext)创建对象。

2. 调用OH_ArkUI_DragAction_SetData等接口配置拖拽参数。

3. 调用[OH_ArkUI_StartDrag](capi-drag-and-drop-h.md#oh_arkui_startdrag)发起拖拽。

4. 不再使用时，调用[OH_ArkUI_DragAction_Dispose](capi-drag-and-drop-h.md#oh_arkui_dragaction_dispose)销毁对象并释放资源。

关于创建、配置和执行机制的详细说明，请参见[绑定拖拽事件](../../ui/ndk-drag-event.md)。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [drag_and_drop.h](capi-drag-and-drop-h.md)

