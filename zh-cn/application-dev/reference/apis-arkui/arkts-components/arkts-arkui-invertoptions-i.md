# InvertOptions

前景智能取反色。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## high

```TypeScript
high: number
```

背景颜色灰度值小于阈值区间时的取值。

取值范围：[0, 1]

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## low

```TypeScript
low: number
```

背景颜色灰度值大于阈值区间时的取值。

取值范围：[0, 1]

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## threshold

```TypeScript
threshold: number
```

灰度阈值。

取值范围：[0, 1]

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## thresholdRange

```TypeScript
thresholdRange: number
```

阈值范围。

取值范围：[0, 1]

**说明：**

灰度阈值上下偏移thresholdRange构成阈值区间，背景颜色灰度值在区间内取值由high线性渐变到low。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

