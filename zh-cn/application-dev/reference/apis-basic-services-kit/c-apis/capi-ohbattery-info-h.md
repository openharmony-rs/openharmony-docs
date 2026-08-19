# ohbattery_info.h

## 概述

声明电池API以获取设备当前剩余的电池电量百分比和连接的充电器类型，定义电池相关常见事件等。

**库：** libohbattery_info.so

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**起始版本：** 13

**相关模块：** [OH_BatteryInfo](capi-oh-batteryinfo.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [BatteryInfo_BatteryPluggedType](#batteryinfo_batterypluggedtype) | BatteryInfo_BatteryPluggedType | 定义连接的充电器类型。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [int32_t OH_BatteryInfo_GetCapacity()](#oh_batteryinfo_getcapacity) | 返回当前电池电量百分比。可用于电池监控应用显示电量信息、低电量提醒功能判断是否需要提示用户、省电模式触发判断等场景。 |
| [BatteryInfo_BatteryPluggedType OH_BatteryInfo_GetPluggedType()](#oh_batteryinfo_getpluggedtype) | 返回连接的充电器类型。可用于充电状态检测应用判断当前充电方式、充电提醒功能展示充电类型图标、省电策略根据充电类型调整等场景。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| static const char * COMMON_EVENT_KEY_CAPACITY = "soc" | 标识剩余电池电量百分比变化后发送的常见事件。<br>**起始版本：** 13<br>**系统能力：** SystemCapability.PowerManager.BatteryManager.Core |
| static const char * COMMON_EVENT_KEY_CHARGE_STATE = "chargeState" | 标识充电状态更改后发送的常见事件。<br>**起始版本：** 13 |
| static const char * COMMON_EVENT_KEY_PLUGGED_TYPE = "pluggedType" | 标识连接的充电器类型更改后发送的常见事件。<br>**起始版本：** 13 |

## 枚举类型说明

### BatteryInfo_BatteryPluggedType

```c
enum BatteryInfo_BatteryPluggedType
```

**描述**

定义连接的充电器类型。

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

返回当前电池电量百分比。可用于电池监控应用显示电量信息、低电量提醒功能判断是否需要提示用户、省电模式触发判断等场景。

**起始版本：** 13

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 表示当前电池电量百分比，取值范围为0到100之间的整数（包含0和100）。 |

### OH_BatteryInfo_GetPluggedType()

```c
BatteryInfo_BatteryPluggedType OH_BatteryInfo_GetPluggedType()
```

**描述**

返回连接的充电器类型。可用于充电状态检测应用判断当前充电方式、充电提醒功能展示充电类型图标、省电策略根据充电类型调整等场景。

**起始版本：** 13

**返回：**

| 类型 | 说明 |
| -- | -- |
| [BatteryInfo_BatteryPluggedType](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) | <ul>          <li>[PLUGGED_TYPE_NONE](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) 如果电源被拔下。</li>          <li>[PLUGGED_TYPE_AC](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) 如果电源是交流充电。</li>          <li>[PLUGGED_TYPE_USB](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) 如果电源是USB充电。</li>          <li>[PLUGGED_TYPE_WIRELESS](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) 如果电源是无线充电。</li>          <li>[PLUGGED_TYPE_BUTT](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) 如果电源类型未知。</li>          </ul> |


