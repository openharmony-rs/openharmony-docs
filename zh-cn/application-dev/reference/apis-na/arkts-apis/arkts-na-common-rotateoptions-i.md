# RotateOptions

组件旋转参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RotateOptions--><!--Device-unnamed-export declare interface RotateOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: double | string
```

旋转角度。取值为正时相对于旋转轴方向顺时针转动，取值为负时相对于旋转轴方向逆时针转动。取值可为string类型，如'90deg'。 默认值：0

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateOptions-angle: double | string--><!--Device-RotateOptions-angle: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerX

```TypeScript
centerX?: double | string
```

变换中心点x轴坐标。表示组件变换中心点（即锚点）的x方向坐标。取值可为string类型，如'50'，'50%'。 单位：vp 默认值：'50%'

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateOptions-centerX?: double | string--><!--Device-RotateOptions-centerX?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: double | string
```

变换中心点y轴坐标。表示组件变换中心点（即锚点）的y方向坐标。取值可为string类型，如'50'，'50%'。 单位：vp 默认值：'50%'

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateOptions-centerY?: double | string--><!--Device-RotateOptions-centerY?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerZ

```TypeScript
centerZ?: double
```

z轴锚点，即3D旋转中心点的z轴分量。 默认值：0 单位：px

**类型：** double

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateOptions-centerZ?: double--><!--Device-RotateOptions-centerZ?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## perspective

```TypeScript
perspective?: double
```

相机放置的z轴坐标。数值大小表示视距，即相机到z=0平面的距离。取值的正负决定了相机观察的方向。当perspective=0，系统会自动计算适合的相机z轴位置，取值为负数。 默认值：0 单位：px

**类型：** double

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateOptions-perspective?: double--><!--Device-RotateOptions-perspective?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: double
```

旋转轴向量x坐标。 默认值：0

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateOptions-x?: double--><!--Device-RotateOptions-x?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: double
```

旋转轴向量y坐标。 默认值：0

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateOptions-y?: double--><!--Device-RotateOptions-y?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## z

```TypeScript
z?: double
```

旋转轴向量z坐标。 默认值：0

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotateOptions-z?: double--><!--Device-RotateOptions-z?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

