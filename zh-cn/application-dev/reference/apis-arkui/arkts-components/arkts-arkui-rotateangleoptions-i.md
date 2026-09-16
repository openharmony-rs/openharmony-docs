# RotateAngleOptions

指定各轴旋转角的旋转参数选项。

> **说明：** 
> 
> 当组件同时设置了[rotate](arkts-arkui-commonmethod-c.md#rotate)和
> [scale](arkts-arkui-commonmethod-c.md#scale)属性时，centerX和centerY的取值会发生冲突，此时centerX和centerY的值以属性链中后设置的属性值为
> 准。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angleX

```TypeScript
angleX?: number | string
```

X轴方向上的旋转角。单位为度（°）。取值为正时相对于旋转轴方向顺时针转动，取值为负时逆时针转动。取值可为string类型，需符合角度值格式要求（如'90deg'）。

默认值：0

取值范围：(-∞, +∞)

**类型：** number &#124; string

**默认值：** 0

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angleY

```TypeScript
angleY?: number | string
```

Y轴方向上的旋转角。单位为度（°）。取值为正时相对于旋转轴方向顺时针转动，取值为负时逆时针转动。取值可为string类型，如'90deg'。

默认值：0

取值范围：(-∞, +∞)

**类型：** number &#124; string

**默认值：** 0

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angleZ

```TypeScript
angleZ?: number | string
```

Z轴方向上的旋转角。单位为度（°）。取值为正时相对于旋转轴方向顺时针转动，取值为负时逆时针转动。取值可为string类型，如'90deg'。

默认值：0

取值范围：(-∞, +∞)

**类型：** number &#124; string

**默认值：** 0

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerX

```TypeScript
centerX?: number | string
```

变换中心点x轴坐标。表示组件变换中心点（即锚点）的x方向坐标。类型为string时，形式参考[Length](../arkts-apis/arkts-arkui-length-t.md)的string类型。取值示例：'50'、'50%'。

单位：vp

默认值：'50%'

取值范围：(-∞, +∞)

**类型：** number &#124; string

**默认值：** '50%'

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: number | string
```

变换中心点y轴坐标。表示组件变换中心点（即锚点）的y方向坐标。类型为string时，形式参考[Length](../arkts-apis/arkts-arkui-length-t.md)的string类型。取值示例：'50'、'50%'。

单位：vp

默认值：'50%'

取值范围：(-∞, +∞)

**类型：** number &#124; string

**默认值：** '50%'

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerZ

```TypeScript
centerZ?: number
```

z轴锚点，即3D旋转中心点的z轴分量。

默认值：0

单位：vp

取值范围：(-∞, +∞)

**类型：** number

**默认值：** 0

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## perspective

```TypeScript
perspective?: number
```

相机放置的z轴坐标。数值大小表示视距，即相机到z=0平面的距离。取值的正负决定了相机观察的方向。当perspective=0，系统会自动计算相机z轴位置，计算得到的z轴位置为负数。

旋转轴和旋转中心点都基于[组件坐标系](../../../ui/arkui-glossary.md#组件坐标系)设定，组件发生位移时，坐标系不会随之移动。

默认值：0

单位：px

取值范围：(-∞, +∞)

**类型：** number

**默认值：** 0

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
