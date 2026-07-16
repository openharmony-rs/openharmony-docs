# Hid_EmitItem
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct Hid_EmitItem {...} Hid_EmitItem
```

## 概述

表示HID事件信息结构体，包含事件类型、事件编码和事件值，用于描述输入设备的上报事件。Hid_EmitItem用于描述HID事件的信息，包含事件类型、事件编码和事件值三个关键字段。在驱动开发场景中，该结构体用于传递和识别各类HID设备产生的事件。

**起始版本：** 11

**相关模块：** [HidDdk](capi-hidddk.md)

**所在头文件：** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint16_t type | 事件类型 |
| uint16_t code | 事件编码 |
| uint32_t value | 事件值 |


