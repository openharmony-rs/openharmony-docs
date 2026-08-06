# ohbattery_info.h

## 概述

声明电池API以获取当前电池容量和电源类型的信息，定义电池相应常见事件。

**库：** libohbattery_info.so

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**起始版本：** 13

**相关模块：** [OH_BatteryInfo](capi-oh-batteryinfo.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [BatteryInfo_BatteryPluggedType](#batteryinfo_batterypluggedtype) | BatteryInfo_BatteryPluggedType | 定义插入类型。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [int32_t OH_BatteryInfo_GetCapacity()](#oh_batteryinfo_getcapacity) | 返回当前电池容量百分比。 |
| [BatteryInfo_BatteryPluggedType OH_BatteryInfo_GetPluggedType()](#oh_batteryinfo_getpluggedtype) | 返回当前插入的类型。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| static const char * COMMON_EVENT_KEY_CAPACITY = "soc" | 标识电池容量变化后发送的常见事件。<br>**起始版本：** 13<br>**系统能力：** SystemCapability.PowerManager.BatteryManager.Core |
| static const char * COMMON_EVENT_KEY_CHARGE_STATE = "chargeState" | 标识充电状态更改后发送的常见事件。<br>**起始版本：** 13 |
| static const char * COMMON_EVENT_KEY_PLUGGED_TYPE = "pluggedType" | 标识插入类型更改后发送的常见事件。<br>**起始版本：** 13 |

## 枚举类型说明

### BatteryInfo_BatteryPluggedType

```c
enum BatteryInfo_BatteryPluggedType
```

**描述**

定义插入类型。

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| PLUGGED_TYPE_NONE |  |
| PLUGGED_TYPE_AC |  |
| PLUGGED_TYPE_USB |  |
| PLUGGED_TYPE_WIRELESS |  |
| PLUGGED_TYPE_BUTT |  |


## 函数说明

### OH_BatteryInfo_GetCapacity()

```c
int32_t OH_BatteryInfo_GetCapacity()
```

**描述**

返回当前电池容量百分比。

**起始版本：** 13

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回介于0和100之间的数字。 |

### OH_BatteryInfo_GetPluggedType()

```c
BatteryInfo_BatteryPluggedType OH_BatteryInfo_GetPluggedType()
```

**描述**

返回当前插入的类型。

**起始版本：** 13

**返回：**

| 类型 | 说明 |
| -- | -- |
| [BatteryInfo_BatteryPluggedType](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) | <ul><br>         <li>[PLUGGED_TYPE_NONE](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) 如果电源被拔下。</li><br>         <li>[PLUGGED_TYPE_AC](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) 如果电源是AC充电。</li><br>         <li>[PLUGGED_TYPE_USB](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) 如果电源是USB DC充电。</li><br>         <li>[PLUGGED_TYPE_WIRELESS](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) 如果电源是无线充电。</li><br>         <li>[PLUGGED_TYPE_BUTT](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) 如果类型未知。</li><br>         </ul> |


