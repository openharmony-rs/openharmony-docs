# @ohos.batteryStatistics

该模块提供软硬件耗电统计信息的查询接口。

> **说明：**
>
> - 本模块接口为系统接口。

**起始版本：** 8

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[getAppPowerPercent](arkts-basicservices-batterystats-getapppowerpercent-f-sys.md#getAppPowerPercent-1) | 获取应用的耗电百分比。<br/> |
| <!--DelRow-->[getAppPowerValue](arkts-basicservices-batterystats-getapppowervalue-f-sys.md#getAppPowerValue-1) | 获取应用的耗电量，单位毫安时。<br/> |
| <!--DelRow-->[getBatteryStats](arkts-basicservices-batterystats-getbatterystats-f-sys.md#getBatteryStats-1) | 获取耗电信息列表。使用Promise异步回调。<br/> |
| <!--DelRow-->[getBatteryStats](arkts-basicservices-batterystats-getbatterystats-f-sys.md#getBatteryStats-2) | 获取耗电信息列表。使用callback异步回调。<br/> |
| <!--DelRow-->[getHardwareUnitPowerPercent](arkts-basicservices-batterystats-gethardwareunitpowerpercent-f-sys.md#getHardwareUnitPowerPercent-1) | 根据耗电类型获取硬件单元的耗电百分比。<br/> |
| <!--DelRow-->[getHardwareUnitPowerValue](arkts-basicservices-batterystats-gethardwareunitpowervalue-f-sys.md#getHardwareUnitPowerValue-1) | 根据耗电类型获取硬件单元的耗电量。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[BatteryStatsInfo](arkts-basicservices-batterystats-batterystatsinfo-i-sys.md) | 设备的耗电信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[ConsumptionType](arkts-basicservices-batterystats-consumptiontype-e-sys.md) | 表示电量消耗类型的枚举值。<br/> |

