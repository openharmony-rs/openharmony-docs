# Hid_RawDevInfo
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct Hid_RawDevInfo {...} Hid_RawDevInfo
```

## 概述

原始设备信息定义。该结构体用于描述HID原始设备的基本信息，包括总线类型、供应商ID和产品ID等关键参数。

**起始版本：** 18

**相关模块：** [HidDdk](capi-hidddk.md)

**所在头文件：** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t busType | 总线类型 |
| uint16_t vendor | 供应商ID |
| uint16_t product | 产品ID |


