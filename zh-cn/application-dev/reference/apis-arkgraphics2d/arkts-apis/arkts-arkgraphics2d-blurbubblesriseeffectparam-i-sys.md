# BlurBubblesRiseEffectParam（系统接口）

模糊气泡上升效果的参数。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## blurIntensity

```TypeScript
blurIntensity: number
```

模糊气泡上升效果的高斯模糊强度。
取值范围[0, 1]，超出边界会在实现时自动截断。0表示无模糊，1表示最大模糊程度。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## maskImage

```TypeScript
maskImage: image.PixelMap
```

模糊气泡上升效果的遮罩图像，控制模糊气泡区域。
被遮罩的区域有模糊效果，未遮罩的区域无模糊效果。

**类型：** image.PixelMap

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## mixStrength

```TypeScript
mixStrength: number
```

原图与模糊图的混合强度。
取值范围[0, 1]，超出边界会在实现时自动截断。0对应原图，1对应模糊后的图像。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## progress

```TypeScript
progress: number
```

模糊气泡上升效果的动画进度。
取值范围[0, 1]，超出边界会在实现时自动截断。0对应动画开始，1对应动画结束。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

