# Hid_EventProperties
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct Hid_EventProperties {...} Hid_EventProperties
```

## 概述

设备关注事件属性。

**起始版本：** 11

**相关模块：** [HidDdk](capi-hidddk.md)

**所在头文件：** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| struct [Hid_EventTypeArray](capi-hidddk-hid-eventtypearray.md) hidEventTypes | 事件类型属性编码数组 |
| struct [Hid_KeyCodeArray](capi-hidddk-hid-keycodearray.md) hidKeys | 键值属性编码数组 |
| struct [Hid_AbsAxesArray](capi-hidddk-hid-absaxesarray.md) hidAbs | 绝对坐标属性编码数组 |
| struct [Hid_RelAxesArray](capi-hidddk-hid-relaxesarray.md) hidRelBits | 相对坐标属性编码数组 |
| struct [Hid_MscEventArray](capi-hidddk-hid-msceventarray.md) hidMiscellaneous | 其它特殊事件属性编码数组 |
| int32_t hidAbsMax[64] | 绝对坐标属性最大值 |
| int32_t hidAbsMin[64] | 绝对坐标属性最小值 |
| int32_t hidAbsFuzz[64] | 绝对坐标属性模糊值 |
| int32_t hidAbsFlat[64] | 绝对坐标属性固定值 |


