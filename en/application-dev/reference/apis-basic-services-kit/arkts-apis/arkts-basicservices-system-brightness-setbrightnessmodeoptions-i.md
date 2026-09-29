# SetBrightnessModeOptions

```TypeScript
export interface SetBrightnessModeOptions
```

Options for setting the screen brightness mode.

**Since:** 3

**Deprecated since:** 7

<!--Device-unnamed-export interface SetBrightnessModeOptions--><!--Device-unnamed-export interface SetBrightnessModeOptions-End-->

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

<!--Device-SetBrightnessModeOptions-complete?: () => void--><!--Device-SetBrightnessModeOptions-complete?: () => void-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SetBrightnessModeOptions-fail?: (data: string, code: number) => void--><!--Device-SetBrightnessModeOptions-fail?: (data: string, code: number) => void-End-->

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

<!--Device-SetBrightnessModeOptions-success?: () => void--><!--Device-SetBrightnessModeOptions-success?: () => void-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

## mode

```TypeScript
mode: number
```

The value **0** indicates the manual adjustment mode, and the value **1** indicates the automatic adjustment mode.

**Type:** number

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SetBrightnessModeOptions-mode: number--><!--Device-SetBrightnessModeOptions-mode: number-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite
