# EdgeLightParams（系统接口）

Defines the parameters of the edge light effect.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface EdgeLightParams--><!--Device-unnamed-export declare interface EdgeLightParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## color

```TypeScript
color?: ResourceColor
```

The color of the light effect. <br>If not specified, the default color is white (#FFFFFF).

**类型：** [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md)

**默认值：** #FFFFFF

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EdgeLightParams-color?: ResourceColor--><!--Device-EdgeLightParams-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## intensity

```TypeScript
intensity?: double
```

The luminous intensity of the Edge Streamer effect. <br>Valid range: [0.0, 1.0].Default value is 1. <br>Value 0.0 means the light effect is completely invisible. <br>Value 1.0 means the light effect is at maximum brightness. <br>Values exceeding 1.0 will be clamped to 1.0. <br>Negative values are treated as 0.0.

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EdgeLightParams-intensity?: double--><!--Device-EdgeLightParams-intensity?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## length

```TypeScript
length: Length
```

Projection length of the edge streamer along the flow direction. <br>Negative values are treated as 0.

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EdgeLightParams-length: Length--><!--Device-EdgeLightParams-length: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## position

```TypeScript
position: EdgeLightPosition
```

The location of the edge light effect.

**类型：** [EdgeLightPosition](../../apis-arkui/arkts-apis/arkts-arkui-edgelightposition-e-sys.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EdgeLightParams-position: EdgeLightPosition--><!--Device-EdgeLightParams-position: EdgeLightPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## thickness

```TypeScript
thickness?: Length
```

The thickness (width) of the light effect line. <br>Negative values are treated as 0. <br>If not specified, the default value is 0vp.

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**默认值：** 0vp

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EdgeLightParams-thickness?: Length--><!--Device-EdgeLightParams-thickness?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

