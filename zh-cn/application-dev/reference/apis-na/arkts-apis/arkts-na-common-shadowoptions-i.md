# ShadowOptions

Define the options of shadow

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ShadowOptions--><!--Device-unnamed-export declare interface ShadowOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: Color | string | Resource | ColoringStrategy
```

Color of the shadow. Default value: **Black**

**类型：** [Color](../../apis-arkui/arkts-apis/arkts-arkui-color-e.md) \| string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| [ColoringStrategy](../../apis-arkui/arkts-apis/arkts-arkui-coloringstrategy-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-color?: Color | string | Resource | ColoringStrategy--><!--Device-ShadowOptions-color?: Color | string | Resource | ColoringStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill?: boolean
```

Whether to fill the inside of the component with shadow. **true**: Fill the inside of the component with shadow. <br>**false**: Do not fill the inside of the component with shadow. <br>The default value is **false**. <br>**NOTE：**<br>This attribute does not take effect in textShadow.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-fill?: boolean--><!--Device-ShadowOptions-fill?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetX

```TypeScript
offsetX?: double | Resource
```

Offset of the shadow along the x-axis. Unit is px. Default value is 0.

**类型：** double \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-offsetX?: double | Resource--><!--Device-ShadowOptions-offsetX?: double | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetY

```TypeScript
offsetY?: double | Resource
```

Offset of the shadow along the y-axis. Unit is px. Default value is 0.

**类型：** double \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-offsetY?: double | Resource--><!--Device-ShadowOptions-offsetY?: double | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: double | Resource | undefined
```

Blur radius of the shadow. Default value: 0px. undefined means setting to default value.

**类型：** double \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| undefined

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-radius: double | Resource | undefined--><!--Device-ShadowOptions-radius: double | Resource | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: ShadowType
```

Shadow type. <br>Default value: **COLOR**.

**类型：** [ShadowType](arkts-na-common-shadowtype-e.md)

**默认值：** ShadowType.COLOR

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShadowOptions-type?: ShadowType--><!--Device-ShadowOptions-type?: ShadowType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

