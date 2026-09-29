# BrightnessModeResponse

```TypeScript
export interface BrightnessModeResponse
```

Defines a response that returns the screen brightness mode.

**Since:** 3

**Deprecated since:** 7

<!--Device-unnamed-export interface BrightnessModeResponse--><!--Device-unnamed-export interface BrightnessModeResponse-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite

## Modules to Import

```TypeScript
import { Brightness, BrightnessModeResponse, BrightnessResponse, GetBrightnessModeOptions, GetBrightnessOptions, SetBrightnessModeOptions, SetBrightnessOptions, SetKeepScreenOnOptions } from '@kit.BasicServicesKit';
```

## mode

```TypeScript
mode: number
```

The value **0** indicates the manual adjustment mode, and the value **1** indicates the automatic adjustment mode.

**Type:** number

**Since:** 3

**Deprecated since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-BrightnessModeResponse-mode: number--><!--Device-BrightnessModeResponse-mode: number-End-->

**System capability:** SystemCapability.PowerManager.DisplayPowerManager.Lite
