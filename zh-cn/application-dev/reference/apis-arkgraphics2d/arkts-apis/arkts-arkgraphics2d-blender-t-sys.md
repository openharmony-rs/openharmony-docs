# Blender（系统接口）

```TypeScript
type Blender = BrightnessBlender | HdrBrightnessBlender | HdrDarkenBlender
```

混合器类型，用于描述混合效果。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| BrightnessBlender | 提亮混合器 |
| HdrBrightnessBlender | 支持HDR的提亮混合器 [since 20] |
| HdrDarkenBlender | 支持HDR的压暗混合器 [since 26.0.0] |

