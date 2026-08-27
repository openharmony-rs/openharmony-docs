# @ohos.batteryStatistics

该模块提供软硬件耗电统计信息的查询接口，支持查询应用和硬件单元的耗电量与耗电百分比，适用于开发者需要监控和分析设备耗电情况的场景，便于定位高耗电应用或硬件组件，从而优化应用的能耗表现。

> **说明：**
> 
> - 本模块接口为系统接口。

**起始版本：** 8

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAppPowerPercent](arkts-basicservices-batterystats-getapppowerpercent-f-sys.md) | 获取应用的耗电百分比，该百分比表示应用耗电量占总耗电量的比例。 |
| [getAppPowerValue](arkts-basicservices-batterystats-getapppowervalue-f-sys.md) | 获取应用的耗电量，单位毫安时。适用于需要精确耗电数值的场景。如需比较不同应用耗电占比，请使用[getAppPowerPercent](arkts-basicservices-batterystats-getapppowerpercent-f-sys.md)获取相对百分比。 |
| [getBatteryStats](arkts-basicservices-batterystats-getbatterystats-f-sys.md) | 获取耗电信息列表，用于电池监控应用查看各应用及硬件的耗电情况。使用Promise异步回调。 |
| [getBatteryStats](arkts-basicservices-batterystats-getbatterystats-f-sys.md) | 获取耗电信息列表，用于电池监控应用查看各应用及硬件的耗电情况。使用callback异步回调。 |
| [getHardwareUnitPowerPercent](arkts-basicservices-batterystats-gethardwareunitpowerpercent-f-sys.md) | 根据耗电类型获取硬件单元的耗电百分比，该百分比表示指定硬件单元耗电量占总耗电量的比例。 |
| [getHardwareUnitPowerValue](arkts-basicservices-batterystats-gethardwareunitpowervalue-f-sys.md) | 根据耗电类型获取硬件单元的耗电量，单位毫安时。适用于需要精确耗电数值的场景。如需比较不同硬件单元耗电占比，请使用[getHardwareUnitPowerPercent](arkts-basicservices-batterystats-gethardwareunitpowerpercent-f-sys.md)获取相对百分比。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BatteryStatsInfo](arkts-basicservices-batterystats-batterystatsinfo-i-sys.md) | 设备软硬件的耗电信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ConsumptionType](arkts-basicservices-batterystats-consumptiontype-e-sys.md) | 表示电量消耗类型的枚举值。 |
<!--DelEnd-->
