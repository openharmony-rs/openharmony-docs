# ColorMetricsStop

线性渐变颜色断点类型，用于描述渐进色颜色断点。

**起始版本：** 23

<!--Device-unnamed-declare interface ColorMetricsStop--><!--Device-unnamed-declare interface ColorMetricsStop-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color: ColorMetrics
```

线性渐变颜色断点的颜色值。

**类型：** ColorMetrics

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetricsStop-color: ColorMetrics--><!--Device-ColorMetricsStop-color: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: Length
```

线性渐变颜色断点的断点值，取值为0~1之间的比例值，如果数据值小于0则置为0，如果数据值大于1则置为1。

**说明：**

如果传入字符串类型且内容为数字，则转换为对应的数值。例如'10vp'转换为10，'10%'转换为0.1。

**类型：** Length

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ColorMetricsStop-offset: Length--><!--Device-ColorMetricsStop-offset: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

