# Input_MouseEvent

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct Input_MouseEvent Input_MouseEvent;
```

## 概述

鼠标事件对象，用于表示用户鼠标操作产生的输入事件，包含点击信息、坐标、点击动作事件等信息，可用于处理鼠标事件输入和实现鼠标事件响应的功能。

**起始版本：** 12

**相关模块：** [input](capi-input.md)

**所在头文件：** [oh_input_manager.h](capi-oh-input-manager-h.md)

**相关接口：**

| 名称 | 描述 |
| -- | -- |
| [OH_Input_CreateMouseEvent](capi-oh-input-manager-h.md#oh_input_createmouseevent) | 创建鼠标事件对象。通过调用[OH_Input_DestroyMouseEvent](capi-oh-input-manager-h.md#oh_input_destroymouseevent)销毁鼠标事件对象。 |
| [OH_Input_DestroyMouseEvent](capi-oh-input-manager-h.md#oh_input_destroymouseevent) | 销毁鼠标事件对象。 |
