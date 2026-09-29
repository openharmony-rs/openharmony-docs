# GetBrightnessModeOptions

```TypeScript
export interface GetBrightnessModeOptions
```

Options for obtaining the screen brightness mode.

**Since:** 3

**Deprecated since:** 7

<!--Device-unnamed-export interface GetBrightnessModeOptions--><!--Device-unnamed-export interface GetBrightnessModeOptions-End-->

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

<!--Device-GetBrightnessModeOptions-complete?: () => void--><!--Device-GetBrightnessModeOptions-complete?: () => void-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Called when an API call has failed. **data** indicates the error information, and **code** indicates the error code.

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-GetBrightnessModeOptions-fail?: (data: string, code: number) => void--><!--Device-GetBrightnessModeOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: (data: BrightnessModeResponse) => void
```

Called when an API call is successful. **data** is a return value of the [BrightnessModeResponse](arkts-basicservices-system-brightness-brightnessmoderesponse-i.md) type.

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-GetBrightnessModeOptions-success?: (data: BrightnessModeResponse) => void--><!--Device-GetBrightnessModeOptions-success?: (data: BrightnessModeResponse) => void-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [BrightnessModeResponse](arkts-basicservices-system-brightness-brightnessmoderesponse-i.md) | Yes |  |
