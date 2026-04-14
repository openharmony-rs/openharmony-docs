# Hid_EmitItem
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct Hid_EmitItem {...} Hid_EmitItem
```

## 概述

事件信息。

**起始版本：** 11

**相关模块：** [HidDdk](capi-hidddk.md)

**所在头文件：** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint16_t type | 事件类型，取值参考[Hid_EventType](capi-hid-ddk-types-h.md#hid_eventtype)。 |
| uint16_t code | 事件编码，取值取决于type字段的值：当type为HID_EV_SYN时，取值参考[Hid_SynEvent](capi-hid-ddk-types-h.md#hid_synevent)；当type为HID_EV_KEY时，取值参考[Hid_KeyCode](capi-hid-ddk-types-h.md#hid_keycode)；当type为HID_EV_ABS时，取值参考[Hid_AbsAxes](capi-hid-ddk-types-h.md#hid_absaxes)；当type为HID_EV_REL时，取值参考[Hid_RelAxes](capi-hid-ddk-types-h.md#hid_relaxes)；当type为HID_EV_MSC时，取值参考[Hid_MscEvent](capi-hid-ddk-types-h.md#hid_mscevent)。 |
| uint32_t value | 事件值，具体含义取决于事件类型和编码。 |


