# ScenePostProcessSettings
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @zzhao0-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->

The module provides image post-processing methods (for example, tone mapping) in 3D graphics.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import
```ts
import { ToneMappingType, ToneMappingSettings, BloomSettings, PostProcessSettings } from '@kit.ArkGraphics3D';
```

## ToneMappingType
Enumerates the tone mapping types.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Value| Description|
| ---- | ---- | ---- |
| ACES | 0 | Academy Color Encoding System (ACES).|
| ACES_2020 | 1 | ACES_2020.|
| FILMIC | 2 | Filmic.|

## ToneMappingSettings
Describes the tone mapping settings.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| type | [ToneMappingType](#tonemappingtype) | No| Yes| Tone mapping type. The default value is undefined.|
| exposure | number | No| Yes| Exposure. The value must be greater than 0. The default value is undefined.|

## BloomSettings<sup>18+</sup>
Describes the settings for bloom effects. It is unavailable when [RenderingPipelineType](js-apis-inner-scene-types.md#renderingpipelinetype21) is set to **FORWARD_LIGHTWEIGHT**.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| thresholdHard | number | No| Yes| Hard threshold. The value is a non-negative number. The default value is **1.0**.|
| thresholdSoft | number | No| Yes| Soft threshold. The value is a non-negative number. The default value is **2.0**.|
| scaleFactor | number | No| Yes| Scale factor. The value must be greater than 0. The default value is **1.0**.|
| scatter | number | No| Yes| Scatter amount. The value must be greater than 0. The default value is **1.0**.|

## VignetteSettings<sup>22+</sup>
Describes the settings for vignette effects.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| roundness | number | No| Yes| Extent of the effect. The value ranges from 0 to 1. The value **1** means a global effect. The default is **0.707**.|
| intensity | number | No| Yes| Strength of the effect. The default value is **0.4**.|

## ColorFringeSettings<sup>22+</sup>
Describes the settings for color fringing. It is unavailable when [RenderingPipelineType](js-apis-inner-scene-types.md#renderingpipelinetype21) is set to **FORWARD_LIGHTWEIGHT**.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| intensity | number | No| Yes| Strength of the effect. The value ranges from 0 to 1. The default value is **0.2**.|

## PostProcessSettings
Describes the post-processing settings.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| toneMapping | [ToneMappingSettings](#tonemappingsettings) | No| Yes| Tone mapping settings. The default value is undefined.|
| bloom<sup>18+</sup> | [BloomSettings](#bloomsettings18) | No| Yes| Bloom settings. The default value is undefined.|
| vignette<sup>22+</sup> | [VignetteSettings](#vignettesettings22) | No| Yes| Vignette settings. The default value is undefined.|
| colorFringe<sup>22+</sup> | [ColorFringeSettings](#colorfringesettings22) | No| Yes| Color fringing settings. The default value is undefined.|
