# DisturbanceFieldOptions

```TypeScript
declare interface DisturbanceFieldOptions
```

设置粒子扰动场参数。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## feather

```TypeScript
feather?: number
```

羽化值，表示场从中心点到场边缘的衰减程度，取值范围为0到100的整数。取值为0时表示场是一个刚体，所有范围内的粒子都被排斥在外。羽化值越大场的缓和程度越大，场范围内出现越多靠近中心点的粒子。设置为负值或大于100时取默认值，设置为非整数时截断取整。

默认值为0。

**类型：** number

**默认值：** 0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## noiseAmplitude

```TypeScript
noiseAmplitude?: number
```

噪声振幅，表示噪声值的波动范围，振幅越大波动范围越大。取值大于等于0。

默认值1。传入负值时取默认值1。

**类型：** number

**默认值：** 1

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## noiseFrequency

```TypeScript
noiseFrequency?: number
```

噪声频率，频率越大噪声越细腻，取值大于等于0。

默认值1。传入负值时取默认值1。

**类型：** number

**默认值：** 1

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## noiseScale

```TypeScript
noiseScale?: number
```

噪声尺度，用于控制噪声图案的整体大小，取值大于等于0。

默认值1。传入负值时取默认值1。

**类型：** number

**默认值：** 1

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: PositionT<number>
```

场的位置，单位：vp。

默认值{x:0, y:0}。

x、y的取值范围：(-∞, +∞)。

**类型：** [PositionT](arkts-arkui-particle-comp-positiont-t.md)&lt;number&gt;

**默认值：** {x:0,y:0}

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: DisturbanceFieldShape
```

场的形状。

默认为DisturbanceFieldShape.RECT。

**类型：** [DisturbanceFieldShape](arkts-arkui-particle-comp-disturbancefieldshape-e.md)

**默认值：** DisturbanceFieldShape.RECT

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<number>
```

场的大小，单位：vp。

默认值 {width:0, height:0}。

width和height的取值范围：[0, +∞)。

**类型：** [SizeT](arkts-arkui-particle-comp-sizet-t.md)&lt;number&gt;

**默认值：** {width:0,height:0}

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
