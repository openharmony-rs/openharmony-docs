# EdgeLightParams（系统接口）

Defines the parameters of the edge light effect.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface EdgeLightParams--><!--Device-unnamed-export declare interface EdgeLightParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## color

```TypeScript
color?: ResourceColor
```

The color of the light effect. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_If not specified, the default color is white (#FFFFFF).

**类型：** ResourceColor

**默认值：** #FFFFFF

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EdgeLightParams-color?: ResourceColor--><!--Device-EdgeLightParams-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## intensity

```TypeScript
intensity?: double
```

The luminous intensity of the Edge Streamer effect. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_Valid range: [0.0, 1.0].Default value is 1. \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_Value 0.0 means the light effect is completely invisible. \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_Value 1.0 means the light effect is at maximum brightness. \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_Values exceeding 1.0 will be clamped to 1.0. \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_Negative values are treated as 0.0.

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EdgeLightParams-intensity?: double--><!--Device-EdgeLightParams-intensity?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## length

```TypeScript
length: Length
```

Projection length of the edge streamer along the flow direction. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_Negative values are treated as 0.

**类型：** Length

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EdgeLightParams-length: Length--><!--Device-EdgeLightParams-length: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## position

```TypeScript
position: EdgeLightPosition
```

The location of the edge light effect.

**类型：** EdgeLightPosition

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EdgeLightParams-position: EdgeLightPosition--><!--Device-EdgeLightParams-position: EdgeLightPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## thickness

```TypeScript
thickness?: Length
```

The thickness (width) of the light effect line. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_Negative values are treated as 0. \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_If not specified, the default value is 0vp.

**类型：** Length

**默认值：** 0vp

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EdgeLightParams-thickness?: Length--><!--Device-EdgeLightParams-thickness?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

