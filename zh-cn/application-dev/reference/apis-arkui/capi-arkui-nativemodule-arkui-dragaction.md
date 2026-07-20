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

拖拽行为句柄，用于主动发起拖拽操作，即由开发者主动调用接口启动拖拽，区别于被动响应拖拽事件。开发者可结合主动拖拽流程了解ArkUI_DragAction的创建、配置和执行机制，相关说明请参见[绑定拖拽事件](../../ui/ndk-drag-event.md)。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [drag_and_drop.h](capi-drag-and-drop-h.md)

