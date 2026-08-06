# ShadowOptions

Define the options of shadow

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ShadowOptions--><!--Device-unnamed-export declare interface ShadowOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: Color | string | Resource | ColoringStrategy
```

Color of the shadow. Default value: **Black**

**类型：** Color \| string \| Resource \| ColoringStrategy

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-color?: Color | string | Resource | ColoringStrategy--><!--Device-ShadowOptions-color?: Color | string | Resource | ColoringStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill?: boolean
```

Whether to fill the inside of the component with shadow. **true**: Fill the inside of the component with shadow. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_**false**: Do not fill the inside of the component with shadow. \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_The default value is **false**. \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_**NOTE**\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_This attribute does not take effect in textShadow.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-fill?: boolean--><!--Device-ShadowOptions-fill?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetX

```TypeScript
offsetX?: double | Resource
```

Offset of the shadow along the x-axis. Unit is px. Default value is 0.

**类型：** double \| Resource

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-offsetX?: double | Resource--><!--Device-ShadowOptions-offsetX?: double | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetY

```TypeScript
offsetY?: double | Resource
```

Offset of the shadow along the y-axis. Unit is px. Default value is 0.

**类型：** double \| Resource

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-offsetY?: double | Resource--><!--Device-ShadowOptions-offsetY?: double | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: double | Resource | undefined
```

Blur radius of the shadow. Default value: 0px.

**类型：** double \| Resource \| undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-radius: double | Resource | undefined--><!--Device-ShadowOptions-radius: double | Resource | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: ShadowType
```

Shadow type. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_Default value: **COLOR**.

**类型：** ShadowType

**默认值：** ShadowType.COLOR

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-type?: ShadowType--><!--Device-ShadowOptions-type?: ShadowType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

