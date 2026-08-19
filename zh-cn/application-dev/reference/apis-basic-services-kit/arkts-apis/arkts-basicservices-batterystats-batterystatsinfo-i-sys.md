# BatteryStatsInfo（系统接口）

设备软硬件的耗电信息。

**起始版本：** 23

<!--Device-batteryStats-interface BatteryStatsInfo--><!--Device-batteryStats-interface BatteryStatsInfo-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## power

```TypeScript
power: double
```

耗电的值，单位毫安时。

**类型：** double

**起始版本：** 23

<!--Device-BatteryStatsInfo-power: double--><!--Device-BatteryStatsInfo-power: double-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: ConsumptionType
```

耗电信息的消耗类型。

**类型：** [ConsumptionType](arkts-basicservices-batterystats-consumptiontype-e-sys.md)

**起始版本：** 23

<!--Device-BatteryStatsInfo-type: ConsumptionType--><!--Device-BatteryStatsInfo-type: ConsumptionType-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: int
```

耗电信息对应的应用UID。

**类型：** int

**起始版本：** 23

<!--Device-BatteryStatsInfo-uid: int--><!--Device-BatteryStatsInfo-uid: int-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

