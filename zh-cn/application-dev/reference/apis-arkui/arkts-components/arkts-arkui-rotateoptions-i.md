# RotateOptions

组件旋转参数。

**起始版本：** 7

<!--Device-unnamed-declare interface RotateOptions--><!--Device-unnamed-declare interface RotateOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: number | string
```

旋转角度。取值为正时相对于旋转轴方向顺时针转动，取值为负时相对于旋转轴方向逆时针转动。取值可为string类型，如'90deg'。

**类型：** number \| string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RotateOptions-angle: number | string--><!--Device-RotateOptions-angle: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerX

```TypeScript
centerX?: number | string
```

变换中心点x轴坐标。表示组件变换中心点（即锚点）的x方向坐标。取值可为string类型，如'50'，'50%'。

单位：vp

**类型：** number \| string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RotateOptions-centerX?: number | string--><!--Device-RotateOptions-centerX?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: number | string
```

变换中心点y轴坐标。表示组件变换中心点（即锚点）的y方向坐标。取值可为string类型，如'50'，'50%'。

单位：vp

**类型：** number \| string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-RotateOptions-centerY?: number | string--><!--Device-RotateOptions-centerY?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerZ

```TypeScript
centerZ?: number
```

z轴锚点，即3D旋转中心点的z轴分量。

默认值：0

单位：px

**类型：** number

**默认值：** 0

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-RotateOptions-centerZ?: number--><!--Device-RotateOptions-centerZ?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## perspective

```TypeScript
perspective?: number
```

相机放置的z轴坐标。数值大小表示视距，即相机到z=0平面的距离。取值的正负决定了相机观察的方向。当perspective=0，系统会自动计算适合的相机z轴位置，取值为负数。

旋转轴和旋转中心点都基于[组件坐标系](../../../ui/arkui-glossary.md#组件坐标系)设定，组件发生位移时，坐标系不会随之移动。

默认值：0

单位：px

**类型：** number

**默认值：** 0

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-RotateOptions-perspective?: number--><!--Device-RotateOptions-perspective?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: number
```

旋转轴向量x坐标。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RotateOptions-x?: number--><!--Device-RotateOptions-x?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: number
```

旋转轴向量y坐标。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RotateOptions-y?: number--><!--Device-RotateOptions-y?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## z

```TypeScript
z?: number
```

旋转轴向量z坐标。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RotateOptions-z?: number--><!--Device-RotateOptions-z?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

