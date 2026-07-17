# BatteryStatsInfo（系统接口）

设备的耗电信息。

**起始版本：** 8

<!--Device-batteryStats-interface BatteryStatsInfo--><!--Device-batteryStats-interface BatteryStatsInfo-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## power

```TypeScript
power: number
```

耗电的值，单位毫安时。

**类型：** number

**起始版本：** 8

<!--Device-BatteryStatsInfo-power: double--><!--Device-BatteryStatsInfo-power: double-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: ConsumptionType
```

耗电信息相关的类型。

**类型：** ConsumptionType

**起始版本：** 8

<!--Device-BatteryStatsInfo-type: ConsumptionType--><!--Device-BatteryStatsInfo-type: ConsumptionType-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: number
```

耗电信息相关的UID。

**类型：** number

**起始版本：** 8

<!--Device-BatteryStatsInfo-uid: int--><!--Device-BatteryStatsInfo-uid: int-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

