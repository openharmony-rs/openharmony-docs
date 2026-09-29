# SetKeepScreenOnOptions

```TypeScript
export interface SetKeepScreenOnOptions
```

Options for setting the screen to be steady on.

**Since:** 3

**Deprecated since:** 7

<!--Device-unnamed-export interface SetKeepScreenOnOptions--><!--Device-unnamed-export interface SetKeepScreenOnOptions-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

## Modules to Import

```TypeScript
import { Brightness, BrightnessModeResponse, BrightnessResponse, GetBrightnessModeOptions, GetBrightnessOptions, SetBrightnessModeOptions, SetBrightnessOptions, SetKeepScreenOnOptions } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

Called when an API call is complete.

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SetKeepScreenOnOptions-complete?: () => void--><!--Device-SetKeepScreenOnOptions-complete?: () => void-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SetKeepScreenOnOptions-fail?: (data: string, code: number) => void--><!--Device-SetKeepScreenOnOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: () => void
```

Called when an API call is successful.

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SetKeepScreenOnOptions-success?: () => void--><!--Device-SetKeepScreenOnOptions-success?: () => void-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

## keepScreenOn

```TypeScript
keepScreenOn: boolean
```

The value **true** means to keep the screen steady on, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SetKeepScreenOnOptions-keepScreenOn: boolean--><!--Device-SetKeepScreenOnOptions-keepScreenOn: boolean-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite
