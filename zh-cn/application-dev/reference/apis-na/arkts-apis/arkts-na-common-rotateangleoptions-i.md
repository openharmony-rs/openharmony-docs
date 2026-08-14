# RotateAngleOptions

指定各轴旋转角的旋转参数选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface RotateAngleOptions--><!--Device-unnamed-export declare interface RotateAngleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angleX

```TypeScript
angleX?: double | string
```

X轴方向上的旋转角。取值为正时相对于旋转轴方向顺时针转动，取值为负时逆时针转动。取值可为string类型，如'90deg'。 默认值：0 取值范围：(-∞, +∞)

**类型：** double \| string

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateAngleOptions-angleX?: double | string--><!--Device-RotateAngleOptions-angleX?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angleY

```TypeScript
angleY?: double | string
```

Y轴方向上的旋转角。取值为正时相对于旋转轴方向顺时针转动，取值为负时逆时针转动。取值可为string类型，如'90deg'。 默认值：0 取值范围：(-∞, +∞)

**类型：** double \| string

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateAngleOptions-angleY?: double | string--><!--Device-RotateAngleOptions-angleY?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angleZ

```TypeScript
angleZ?: double | string
```

Z轴方向上的旋转角。取值为正时相对于旋转轴方向顺时针转动，取值为负时逆时针转动。取值可为string类型，如'90deg'。 默认值：0 取值范围：(-∞, +∞)

**类型：** double \| string

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateAngleOptions-angleZ?: double | string--><!--Device-RotateAngleOptions-angleZ?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerX

```TypeScript
centerX?: double | string
```

变换中心点x轴坐标。表示组件变换中心点（即锚点）的x方向坐标。 单位：vp 默认值：'50%' 取值范围：(-∞, +∞)

**类型：** double \| string

**默认值：** '50%'

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateAngleOptions-centerX?: double | string--><!--Device-RotateAngleOptions-centerX?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: double | string
```

变换中心点y轴坐标。表示组件变换中心点（即锚点）的y方向坐标。 单位：vp 默认值：'50%' 取值范围：(-∞, +∞)

**类型：** double \| string

**默认值：** '50%'

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateAngleOptions-centerY?: double | string--><!--Device-RotateAngleOptions-centerY?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerZ

```TypeScript
centerZ?: double
```

z轴锚点，即3D旋转中心点的z轴分量。 默认值：0 单位：px 取值范围：(-∞, +∞)

**类型：** double

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateAngleOptions-centerZ?: double--><!--Device-RotateAngleOptions-centerZ?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## perspective

```TypeScript
perspective?: double
```

相机放置的z轴坐标。数值大小表示视距，即相机到z=0平面的距离。取值的正负决定了相机观察的方向。当perspective=0，系统会自动计算适合的相机z轴位置，取值为负数。 默认值：0 单位：px 取值范围：(-∞, +∞)

**类型：** double

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateAngleOptions-perspective?: double--><!--Device-RotateAngleOptions-perspective?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

