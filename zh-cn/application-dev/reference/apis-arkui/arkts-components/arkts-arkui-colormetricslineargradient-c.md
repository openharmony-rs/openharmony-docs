# ColorMetricsLinearGradient

滑轨轨道的线性渐变背景颜色。

**起始版本：** 23

<!--Device-unnamed-declare class ColorMetricsLinearGradient--><!--Device-unnamed-declare class ColorMetricsLinearGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(colorStops: ColorMetricsStop[])
```

ColorMetricsLinearGradient的构造函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetricsLinearGradient-constructor(colorStops: ColorMetricsStop[])--><!--Device-ColorMetricsLinearGradient-constructor(colorStops: ColorMetricsStop[])-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorStops | [ColorMetricsStop](arkts-arkui-colormetricsstop-i.md)[] | 是 | 线性渐变颜色断点数组。每个元素用于描述一个颜色及其在渐变中的断点值。 |

