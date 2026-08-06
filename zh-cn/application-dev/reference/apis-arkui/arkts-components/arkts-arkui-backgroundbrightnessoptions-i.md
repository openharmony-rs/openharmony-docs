# BackgroundBrightnessOptions

背景亮度选项。 > **说明：** > > 对于组件背景内容，每个像素自身的亮度（灰阶值）的计算公式为： > > \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_（R、G、B分别表示像素红色、绿色和蓝色通道的值，Y表示灰阶值），通过上述公式将像素点的灰阶值归一化至0~1的范围。 > > 每个像素的亮度提升计算公式为：\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_。例如，当rate=0.5，lightUpDegree=0.5时，对于灰阶值为0.2的像素点，亮度增加值为 > \_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_，对于灰阶值为1的像素点，亮度增加值为\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface BackgroundBrightnessOptions--><!--Device-unnamed-declare interface BackgroundBrightnessOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lightUpDegree

```TypeScript
lightUpDegree: number
```

提亮程度。提亮程度越大，亮度提升程度越大。 默认值：0.0 取值范围：[-1.0, 1.0]

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundBrightnessOptions-lightUpDegree: number--><!--Device-BackgroundBrightnessOptions-lightUpDegree: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rate

```TypeScript
rate: number
```

亮度变化速率。亮度变化速率越大，提亮程度下降速度越快。若rate为0，则lightUpDegree将不生效，即不会产生任何提亮效果。 默认值：0.0 取值范围：(0.0, +∞)

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundBrightnessOptions-rate: number--><!--Device-BackgroundBrightnessOptions-rate: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

