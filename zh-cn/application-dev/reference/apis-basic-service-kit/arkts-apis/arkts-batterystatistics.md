# @ohos.batteryStatistics

该模块提供软硬件耗电统计信息的查询接口。

> **说明：**  
>  
> - 本模块接口为系统接口。

**起始版本：** 8

<!--Device-unnamed-declare namespace batteryStats--><!--Device-unnamed-declare namespace batteryStats-End-->

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
| [getAppPowerPercent](arkts-basicservices-batterystats-getapppowerpercent-f-sys.md#getapppowerpercent-1) | 获取应用的耗电百分比。 |
| [getAppPowerValue](arkts-basicservices-batterystats-getapppowervalue-f-sys.md#getapppowervalue-1) | 获取应用的耗电量，单位毫安时。 |
| [getBatteryStats](arkts-basicservices-batterystats-getbatterystats-f-sys.md#getbatterystats-1) | 获取耗电信息列表。使用Promise异步回调。 |
| [getBatteryStats](arkts-basicservices-batterystats-getbatterystats-f-sys.md#getbatterystats-2) | 获取耗电信息列表。使用callback异步回调。 |
| [getHardwareUnitPowerPercent](arkts-basicservices-batterystats-gethardwareunitpowerpercent-f-sys.md#gethardwareunitpowerpercent-1) | 根据耗电类型获取硬件单元的耗电百分比。 |
| [getHardwareUnitPowerValue](arkts-basicservices-batterystats-gethardwareunitpowervalue-f-sys.md#gethardwareunitpowervalue-1) | 根据耗电类型获取硬件单元的耗电量，单位毫安时。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BatteryStatsInfo](arkts-basicservices-batterystats-batterystatsinfo-i-sys.md) | 设备的耗电信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ConsumptionType](arkts-basicservices-batterystats-consumptiontype-e-sys.md) | 表示电量消耗类型的枚举值。 |
<!--DelEnd-->

