# InvertOptions

```TypeScript
declare interface InvertOptions
```

前景智能取反色。基于灰度阈值区间决定反色取值，参见[invert](arkts-arkui-common-comp-commonmethod-c.md#invert)中的详细机制说明。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## high

```TypeScript
high: number
```

背景颜色灰度值小于阈值区间时的取值。

取值范围：[0, 1]。设置小于0的值时，按值为0处理。设置大于1的值时，按值为1处理。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## low

```TypeScript
low: number
```

背景颜色灰度值大于阈值区间时的取值。

取值范围：[0, 1]。设置小于0的值时，按值为0处理。设置大于1的值时，按值为1处理。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## threshold

```TypeScript
threshold: number
```

灰度阈值。与thresholdRange配合使用，灰度阈值上下偏移thresholdRange构成阈值区间。

取值范围：[0, 1]

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## thresholdRange

```TypeScript
thresholdRange: number
```

阈值范围。

取值范围：[0, 1]。设置小于0的值时，按值为0处理；设置大于1的值时，按值为1处理。

**说明：** 

灰度阈值上下偏移thresholdRange构成阈值区间，背景颜色灰度值在区间内取值由high线性渐变到low。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
