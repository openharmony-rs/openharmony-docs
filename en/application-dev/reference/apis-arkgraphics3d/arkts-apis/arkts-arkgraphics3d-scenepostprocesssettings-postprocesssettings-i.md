# PostProcessSettings

```TypeScript
export interface PostProcessSettings
```

Post-processing settings, which are used to configure the image processing effect after camera rendering, including tone mapping, bloom, vignetting, and chromatic aberration. This is used as the postProcess attribute of Camera.

@typedef PostProcessSettings

**Since:** 12

<!--Device-unnamed-export interface PostProcessSettings--><!--Device-unnamed-export interface PostProcessSettings-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## bloom

```TypeScript
bloom?: BloomSettings
```

Bloom settings. The default value is undefined.

**Type:** [BloomSettings](arkts-arkgraphics3d-scenepostprocesssettings-bloomsettings-i.md)

**Since:** 18

<!--Device-PostProcessSettings-bloom?: BloomSettings--><!--Device-PostProcessSettings-bloom?: BloomSettings-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## colorFringe

```TypeScript
colorFringe?: ColorFringeSettings
```

Color fringing settings. The default value is undefined.

**Type:** [ColorFringeSettings](arkts-arkgraphics3d-scenepostprocesssettings-colorfringesettings-i.md)

**Default:** undefined

**Since:** 22

<!--Device-PostProcessSettings-colorFringe?: ColorFringeSettings--><!--Device-PostProcessSettings-colorFringe?: ColorFringeSettings-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## toneMapping

```TypeScript
toneMapping?: ToneMappingSettings
```

Tone mapping settings. The default value is undefined.

**Type:** [ToneMappingSettings](arkts-arkgraphics3d-scenepostprocesssettings-tonemappingsettings-i.md)

**Since:** 12

<!--Device-PostProcessSettings-toneMapping?: ToneMappingSettings--><!--Device-PostProcessSettings-toneMapping?: ToneMappingSettings-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## vignette

```TypeScript
vignette?: VignetteSettings
```

Vignette settings. The default value is undefined.

**Type:** [VignetteSettings](arkts-arkgraphics3d-scenepostprocesssettings-vignettesettings-i.md)

**Default:** undefined

**Since:** 22

<!--Device-PostProcessSettings-vignette?: VignetteSettings--><!--Device-PostProcessSettings-vignette?: VignetteSettings-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D
