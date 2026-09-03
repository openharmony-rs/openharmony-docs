# ScenePostProcessSettings

<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @jason_stark-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=8bb9848b7b451305a97994d9b8833fe195588c67 translatedAt=2026-08-20T12:26:11.705Z pushedAt=2026-08-21T07:08:14.940Z -->

This module provides image post-processing methods such as tone mapping in ArkGraphics 3D.

> **NOTE**
> 
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { ToneMappingType, ToneMappingSettings, BloomSettings, VignetteSettings, ColorFringeSettings, PostProcessSettings } from '@kit.ArkGraphics3D';
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
| roundness | number | No | Yes | Roundness of the vignette. The value range is [0, 1]. When the value is 0, the vignette shape approaches a rectangle; when the value is 1, the vignette shape approaches a circle. The default value is sqrt(0.5) (about 0.707). |
| intensity | number | No| Yes| Effect strength. The value range is [0, 1]. The value **0** indicates no vignetting effect, and the value **1** indicates maximum vignetting intensity. The default value is **0.4**.|

## ColorFringeSettings<sup>22+</sup>

Describes the settings for color fringing. It is unavailable when [RenderingPipelineType](js-apis-inner-scene-types.md#renderingpipelinetype21) is set to **FORWARD_LIGHTWEIGHT**.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| intensity | number | No | Yes | Effect intensity. The value range is [0, 1], and the default value is 0.2. |

## PostProcessSettings

Post-processing settings, which are used to configure the image processing effect after camera rendering, including tone mapping, bloom, vignetting, and chromatic aberration. This is used as the postProcess attribute of [Camera](js-apis-inner-scene-nodes.md#camera).

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Type| Read Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| toneMapping | [ToneMappingSettings](#tonemappingsettings) | No| Yes| Tone mapping settings. The default value is undefined.|
| bloom<sup>18+</sup> | [BloomSettings](#bloomsettings18) | No| Yes| Bloom settings. The default value is undefined.|
| vignette<sup>22+</sup> | [VignetteSettings](#vignettesettings22) | No| Yes| Vignette settings. The default value is undefined.|
| colorFringe<sup>22+</sup> | [ColorFringeSettings](#colorfringesettings22) | No| Yes| Color fringing settings. The default value is undefined.|