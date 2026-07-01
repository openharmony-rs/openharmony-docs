# Hid_RelAxesArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct Hid_RelAxesArray {...} Hid_RelAxesArray
```

## 概述

相对坐标属性数组。

**起始版本：** 11

**相关模块：** [HidDdk](capi-hidddk.md)

**所在头文件：** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Hid_RelAxes](capi-hid-ddk-types-h.md#hid_relaxes)* hidRelAxes | 相对坐标属性编码数组的指针。 |
| uint16_t length | 数组的有效长度。 |


