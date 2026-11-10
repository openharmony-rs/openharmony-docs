# SheetTitleBarBackgroundBlurOptions（系统接口）

```TypeScript
declare interface SheetTitleBarBackgroundBlurOptions
```

标题栏背景模糊效果层的自定义参数，所有子属性均为可选，未设置的属性使用系统默认值。

**起始版本：** 26.0.1

<!--Device-unnamed-declare interface SheetTitleBarBackgroundBlurOptions--><!--Device-unnamed-declare interface SheetTitleBarBackgroundBlurOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## blurStyle

```TypeScript
blurStyle?: SheetTitleBarBackgroundBlur
```

模糊效果层的模糊样式，设置为GRADIENT启用渐变模糊效果。

默认值：SheetTitleBarBackgroundBlur.NONE

**类型：** [SheetTitleBarBackgroundBlur](arkts-arkui-common-comp-sheettitlebarbackgroundblur-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SheetTitleBarBackgroundBlurOptions-blurStyle?: SheetTitleBarBackgroundBlur--><!--Device-SheetTitleBarBackgroundBlurOptions-blurStyle?: SheetTitleBarBackgroundBlur-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## effectiveDistance

```TypeScript
effectiveDistance?: LengthMetrics
```

模糊效果从完全隐藏到完全可见所需的滑动距离。

取值范围：大于等于0，小于0的值按0处理

默认值：8vp

**类型：** LengthMetrics

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SheetTitleBarBackgroundBlurOptions-effectiveDistance?: LengthMetrics--><!--Device-SheetTitleBarBackgroundBlurOptions-effectiveDistance?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## maskColor

```TypeScript
maskColor?: ResourceColor
```

模糊效果层的渐变基色，作为渐变顶部的最大颜色值，系统应用内置透明度曲线从顶部到底部逐渐将其淡化。

未设置时：浅色模式使用半透明白色效果，深色模式使用半透明黑色效果。

**类型：** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SheetTitleBarBackgroundBlurOptions-maskColor?: ResourceColor--><!--Device-SheetTitleBarBackgroundBlurOptions-maskColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## maskExtraHeight

```TypeScript
maskExtraHeight?: LengthMetrics
```

模糊效果层的额外高度，以标题栏高度为基础的额外效果高度。

默认值：32vp

当取值为0vp时，模糊效果层下边沿与标题栏等高。

**类型：** LengthMetrics

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SheetTitleBarBackgroundBlurOptions-maskExtraHeight?: LengthMetrics--><!--Device-SheetTitleBarBackgroundBlurOptions-maskExtraHeight?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
