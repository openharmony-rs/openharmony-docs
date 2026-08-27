# PostProcessSettings

后处理设置，用于配置相机渲染后的图像处理效果，包括色调映射、泛光、边缘暗角和色晕等，作为Camera的postProcess属性来使用。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## bloom

```TypeScript
bloom?: BloomSettings
```

泛光，默认值为undefined。

**类型：** [BloomSettings](arkts-arkgraphics3d-scenepostprocesssettings-bloomsettings-i.md)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D

## colorFringe

```TypeScript
colorFringe?: ColorFringeSettings
```

色晕，默认值为undefined。

**类型：** [ColorFringeSettings](arkts-arkgraphics3d-scenepostprocesssettings-colorfringesettings-i.md)

**默认值：** undefined

**起始版本：** 22

**系统能力：** SystemCapability.ArkUi.Graphics3D

## toneMapping

```TypeScript
toneMapping?: ToneMappingSettings
```

色调映射，默认值为undefined。

**类型：** [ToneMappingSettings](arkts-arkgraphics3d-scenepostprocesssettings-tonemappingsettings-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## vignette

```TypeScript
vignette?: VignetteSettings
```

边缘暗角，默认值为undefined。

**类型：** [VignetteSettings](arkts-arkgraphics3d-scenepostprocesssettings-vignettesettings-i.md)

**默认值：** undefined

**起始版本：** 22

**系统能力：** SystemCapability.ArkUi.Graphics3D
