# @ohos.batteryStatistics(Battery Statistics)

The **batteryStatistics** module provides APIs for querying software and hardware power consumption statistics.

> **NOTE:** 
> 
> - The APIs provided by this module are system APIs.

**Since:** 8

**System capability:** SystemCapability.PowerManager.BatteryStatistics

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getAppPowerPercent](arkts-basicservices-batterystats-getapppowerpercent-f-sys.md) | Obtains the proportion of the power consumption of an application. |
| [getAppPowerValue](arkts-basicservices-batterystats-getapppowervalue-f-sys.md) | Obtains the power consumption of an application, in unit of mAh. |
| [getBatteryStats](arkts-basicservices-batterystats-getbatterystats-f-sys.md#getbatterystats) | Obtains the power consumption information list. This API uses a promise to return the result. |
| [getBatteryStats](arkts-basicservices-batterystats-getbatterystats-f-sys.md#getbatterystats-1) | Obtains the power consumption information list. This API uses an asynchronous callback to return the result. |
| [getHardwareUnitPowerPercent](arkts-basicservices-batterystats-gethardwareunitpowerpercent-f-sys.md) | Obtains the proportion of the power consumption of a hardware unit according to the power consumption type. |
| [getHardwareUnitPowerValue](arkts-basicservices-batterystats-gethardwareunitpowervalue-f-sys.md) | Obtains the power consumption of a hardware unit according to the consumption type, in unit of mAh. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BatteryStatsInfo](arkts-basicservices-batterystats-batterystatsinfo-i-sys.md) | Describes the device power consumption information. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ConsumptionType](arkts-basicservices-batterystats-consumptiontype-e-sys.md) | Enumerates power consumption types. |
<!--DelEnd-->
