# GetStatusOptions

```TypeScript
export interface GetStatusOptions
```

Object that contains the API calling result.

**Since:** 3

**Deprecated since:** 6

<!--Device-unnamed-export interface GetStatusOptions--><!--Device-unnamed-export interface GetStatusOptions-End-->

**System capability:** SystemCapability.PowerManager.BatteryManager.Lite

## Modules to Import

```TypeScript
import { Battery, BatteryResponse, GetStatusOptions } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

Called when an API call is complete.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-GetStatusOptions-complete?: () => void--><!--Device-GetStatusOptions-complete?: () => void-End-->

**System capability:** SystemCapability.PowerManager.BatteryManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-GetStatusOptions-fail?: (data: string, code: number) => void--><!--Device-GetStatusOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.PowerManager.BatteryManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: (data: BatteryResponse) => void
```

Called when an API call is successful. **data** is a return value of the [BatteryResponse](arkts-basicservices-system-battery-batteryresponse-i.md) type.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-GetStatusOptions-success?: (data: BatteryResponse) => void--><!--Device-GetStatusOptions-success?: (data: BatteryResponse) => void-End-->

**System capability:** SystemCapability.PowerManager.BatteryManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [BatteryResponse](arkts-basicservices-system-battery-batteryresponse-i.md) | Yes |  |
