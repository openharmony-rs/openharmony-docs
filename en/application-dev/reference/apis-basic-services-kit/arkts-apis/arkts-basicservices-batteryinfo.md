# @ohos.batteryInfo(Battery Information)

The **batteryInfo** module provides APIs for querying the charger type, battery health status, and battery charging status.

**Since:** 6

**System capability:** SystemCapability.PowerManager.BatteryManager.Core

## Modules to Import

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getBatteryConfig](arkts-basicservices-batteryinfo-getbatteryconfig-f-sys.md) | Obtains the battery configuration based on the specified scenario. |
| [isBatteryConfigSupported](arkts-basicservices-batteryinfo-isbatteryconfigsupported-f-sys.md) | Checks whether the battery configuration is enabled based on the specified scenario. |
| [setBatteryConfig](arkts-basicservices-batteryinfo-setbatteryconfig-f-sys.md) | Sets the battery configuration based on the specified scenario. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [BatteryCapacityLevel](arkts-basicservices-batteryinfo-batterycapacitylevel-e.md) | Enumerates battery levels. |
| [BatteryChargeState](arkts-basicservices-batteryinfo-batterychargestate-e.md) | Enumerates charging states. |
| [BatteryHealthState](arkts-basicservices-batteryinfo-batteryhealthstate-e.md) | Enumerates battery health states. |
| [BatteryPluggedType](arkts-basicservices-batteryinfo-batterypluggedtype-e.md) | Enumerates charger types. |
| [CommonEventBatteryChangedKey](arkts-basicservices-batteryinfo-commoneventbatterychangedkey-e.md) | Enumerates keys for querying the additional information about the **COMMON_EVENT_BATTERY_CHANGED** event. |

### Constants

| Name | Description |
| --- | --- |
| [batteryCapacityLevel](arkts-basicservices-batteryinfo-con.md#batterycapacitylevel) | Battery level of the device. |
| [batterySOC](arkts-basicservices-batteryinfo-con.md#batterysoc) | Battery state of charge (SoC) of the device, in unit of percentage, which ranges from 0 to 100. |
| [batteryTemperature](arkts-basicservices-batteryinfo-con.md#batterytemperature) | Battery temperature of the device, in unit of 0.1°C. |
| [chargingStatus](arkts-basicservices-batteryinfo-con.md#chargingstatus) | Battery charging state of the current device. |
| [healthStatus](arkts-basicservices-batteryinfo-con.md#healthstatus) | Battery health status of the device. |
| [isBatteryPresent](arkts-basicservices-batteryinfo-con.md#isbatterypresent) | Whether the battery is supported or present. The value **true** means that the battery is supported or present; **false** means the opposite. |
| [nowCurrent](arkts-basicservices-batteryinfo-con.md#nowcurrent) | Battery current of the device, in unit of mA. |
| [pluggedType](arkts-basicservices-batteryinfo-con.md#pluggedtype) | Charger type of the device. |
| [technology](arkts-basicservices-batteryinfo-con.md#technology) | Battery technology of the device. |
| [voltage](arkts-basicservices-batteryinfo-con.md#voltage) | Battery voltage of the device, in unit of microvolt. |

<!--Del-->
### Constants(System API)

| Name | Description |
| --- | --- |
| [estimatedRemainingChargeTime](arkts-basicservices-batteryinfo-con-sys.md#estimatedremainingchargetime) | Estimated time for fully charging the current device, in unit of milliseconds. This is a system API. |
| [remainingEnergy](arkts-basicservices-batteryinfo-con-sys.md#remainingenergy) | Remaining battery capacity of the device, in unit of mAh. This is a system API. |
| [totalEnergy](arkts-basicservices-batteryinfo-con-sys.md#totalenergy) | Total battery capacity of the device, in unit of mAh. This is a system API. |
<!--DelEnd-->
