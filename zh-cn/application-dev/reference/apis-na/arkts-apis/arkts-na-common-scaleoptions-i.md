# ScaleOptions

> **说明：** > > 当组件同时设置了[rotate](arkts-na-common-commonmethod-i.md#rotate)和[scale](arkts-na-common-commonmethod-i.md#scale)属性时，centerX和centerY的取值会发生冲突，此时centerX和 > centerY的值以最后设定的属性的值为准。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ScaleOptions--><!--Device-unnamed-export declare interface ScaleOptions-End-->

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

<!--Device-ScaleOptions-centerX?: double | string--><!--Device-ScaleOptions-centerX?: double | string-End-->

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

<!--Device-ScaleOptions-centerY?: double | string--><!--Device-ScaleOptions-centerY?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: double
```

x轴的缩放倍数。x>1时以x轴方向放大，0&lt;x&lt;1时以x轴方向缩小，x&lt;0时沿x轴反向并缩放。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScaleOptions-x?: double--><!--Device-ScaleOptions-x?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: double
```

y轴的缩放倍数。y>1时以y轴方向放大，0&lt;y&lt;1时以y轴方向缩小，y&lt;0时沿y轴反向并缩放。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScaleOptions-y?: double--><!--Device-ScaleOptions-y?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## z

```TypeScript
z?: double
```

z轴的缩放倍数。z>1时以z轴方向放大，0&lt;z&lt;1时以z轴方向缩小，z&lt;0时沿z轴反向并缩放。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScaleOptions-z?: double--><!--Device-ScaleOptions-z?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

