# BatteryResponse

Defines a response that returns the charging status and remaining power of the device.

**Since:** 3

**Deprecated since:** 6

**System capability:** SystemCapability.PowerManager.BatteryManager.Lite

## Modules to Import

```TypeScript
import { Battery, BatteryResponse, GetStatusOptions } from '@kit.BasicServicesKit';
```

## charging

```TypeScript
charging: boolean
```

Whether the battery is being charged. The value **true** indicates that the battery is being charged; **false** indicates the opposite. The default value is **false**.

Note: This API is no longer maintained since API version 6 except for lite wearables. You are advised to use [batteryInfo.chargingStatus](../../../reference/apis-basic-services-kit/js-apis-battery-info.md#constants) instead.

**Type:** boolean

**Since:** 3

**Deprecated since:** 6

**Substitutes:** [chargingStatus](arkts-basicservices-batteryinfo-con.md#chargingstatus)

**System capability:** SystemCapability.PowerManager.BatteryManager.Lite

## level

```TypeScript
level: number
```

Current battery level in percent, which ranges from **0.00** to **1.00**.

Note: This API is no longer maintained since API version 6 except for lite wearables. You are advised to use [batteryInfo.batterySOC](../../../reference/apis-basic-services-kit/js-apis-battery-info.md#constants) instead.

**Type:** number

**Since:** 3

**Deprecated since:** 6

**Substitutes:** [batterySOC](arkts-basicservices-batteryinfo-con.md#batterysoc)

**System capability:** SystemCapability.PowerManager.BatteryManager.Lite
