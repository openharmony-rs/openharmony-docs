# ArkUI_DragAndDropInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_DragAndDropInfo ArkUI_DragAndDropInfo
```

## 概述

主动发起拖拽后，系统通过拖拽状态监听回调返回ArkUI_DragAndDropInfo。开发者可从该结构体获取拖拽开始或结束状态，以及拖拽结束时的拖拽事件数据，并根据状态进行后续处理。拖拽回调的注册方式请参见[drag_and_drop.h](capi-drag-and-drop-h.md)。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [drag_and_drop.h](capi-drag-and-drop-h.md)

