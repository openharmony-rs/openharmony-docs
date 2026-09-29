# BatteryStatsInfo (System API)

```TypeScript
interface BatteryStatsInfo
```

Describes the device power consumption information.

**Since:** 8

<!--Device-batteryStats-interface BatteryStatsInfo--><!--Device-batteryStats-interface BatteryStatsInfo-End-->

**System capability:** SystemCapability.PowerManager.BatteryStatistics

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## power

```TypeScript
power: number
```

The power consumption, in unit of mAh.

**Type:** number

**Since:** 8

<!--Device-BatteryStatsInfo-power: double--><!--Device-BatteryStatsInfo-power: double-End-->

**System capability:** SystemCapability.PowerManager.BatteryStatistics

**System API:** This is a system API.

## type

```TypeScript
type: ConsumptionType
```

The power consumption type.

**Type:** [ConsumptionType](arkts-basicservices-batterystats-consumptiontype-e-sys.md)

**Since:** 8

<!--Device-BatteryStatsInfo-type: ConsumptionType--><!--Device-BatteryStatsInfo-type: ConsumptionType-End-->

**System capability:** SystemCapability.PowerManager.BatteryStatistics

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

The uid related with the power consumption info.

**Type:** number

**Since:** 8

<!--Device-BatteryStatsInfo-uid: int--><!--Device-BatteryStatsInfo-uid: int-End-->

**System capability:** SystemCapability.PowerManager.BatteryStatistics

**System API:** This is a system API.
