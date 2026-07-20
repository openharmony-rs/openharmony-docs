# DisturbanceFieldOptions

设置粒子扰动场参数。

**起始版本：** 12

<!--Device-unnamed-declare interface DisturbanceFieldOptions--><!--Device-unnamed-declare interface DisturbanceFieldOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## feather

```TypeScript
feather?: number
```

羽化值，表示场从中心点到场边缘的衰减程度，取值范围0到100的整数，如果0则表示场是一个刚体，所有范围内的粒子都被排斥在外。羽化值越大场的缓和程度越大，场范围内出现越多靠近中心点的粒子。

默认值为0。

**类型：** number

**默认值：** 0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisturbanceFieldOptions-feather?: number--><!--Device-DisturbanceFieldOptions-feather?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## noiseAmplitude

```TypeScript
noiseAmplitude?: number
```

噪声振幅，噪声的波动的范围，振幅越大噪音之间差异越大。取值大于等于0。

默认值1。

**类型：** number

**默认值：** 1

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisturbanceFieldOptions-noiseAmplitude?: number--><!--Device-DisturbanceFieldOptions-noiseAmplitude?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## noiseFrequency

```TypeScript
noiseFrequency?: number
```

噪声频率，频率越大噪声越细腻，取值大于等于0。

默认值1。

**类型：** number

**默认值：** 1

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisturbanceFieldOptions-noiseFrequency?: number--><!--Device-DisturbanceFieldOptions-noiseFrequency?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## noiseScale

```TypeScript
noiseScale?: number
```

噪声尺度，用于控制噪声图案的整体大小，取值大于等于0。

默认值1。

**类型：** number

**默认值：** 1

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisturbanceFieldOptions-noiseScale?: number--><!--Device-DisturbanceFieldOptions-noiseScale?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: PositionT<number>
```

场的位置。

默认值{x:0，y:0}。

x、y的取值范围：(-∞, +∞)。

**类型：** PositionT&lt;number&gt;

**默认值：** {x:0,y:0}

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisturbanceFieldOptions-position?: PositionT<number>--><!--Device-DisturbanceFieldOptions-position?: PositionT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: DisturbanceFieldShape
```

场的形状。

默认为DisturbanceFieldShape.RECT。

**类型：** DisturbanceFieldShape

**默认值：** DisturbanceFieldShape.RECT

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisturbanceFieldOptions-shape?: DisturbanceFieldShape--><!--Device-DisturbanceFieldOptions-shape?: DisturbanceFieldShape-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<number>
```

场的大小。

默认值 {width:0，height:0}。

width和height的取值范围：[0, +∞)。

**类型：** SizeT&lt;number&gt;

**默认值：** {width:0,height:0}

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisturbanceFieldOptions-size?: SizeT<number>--><!--Device-DisturbanceFieldOptions-size?: SizeT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strength

```TypeScript
strength?: number
```

场强，表示场从中心向外的排斥力的强度，默认值0。正数表示排斥力方向朝外，负数表示吸引力，方向朝内。

取值范围：(-∞, +∞)。

**类型：** number

**默认值：** 0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisturbanceFieldOptions-strength?: number--><!--Device-DisturbanceFieldOptions-strength?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

