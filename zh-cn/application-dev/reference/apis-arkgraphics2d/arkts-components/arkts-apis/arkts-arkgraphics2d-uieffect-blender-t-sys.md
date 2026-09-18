# Blender（系统接口）

```TypeScript
type Blender = BrightnessBlender | HdrBrightnessBlender | HdrDarkenBlender | ColorfulBrightnessBlender
```

混合器类型，用于描述混合效果。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| [BrightnessBlender](arkts-arkgraphics2d-uieffect-brightnessblender-i-sys.md) | 提亮混合器 |
| [HdrBrightnessBlender](arkts-arkgraphics2d-uieffect-hdrbrightnessblender-i-sys.md) | 支持HDR的提亮混合器 [since 20] |
| [HdrDarkenBlender](arkts-arkgraphics2d-uieffect-hdrdarkenblender-i-sys.md) | 支持HDR的压暗混合器 [since 26.0.0] |
| [ColorfulBrightnessBlender](arkts-arkgraphics2d-uieffect-colorfulbrightnessblender-i-sys.md) | 具有提亮压暗效果的混合器（保持色相） [since 26.2.0] |
