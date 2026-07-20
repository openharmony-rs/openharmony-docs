# ButtonOptions

按钮的样式。

**起始版本：** 7

<!--Device-unnamed-declare interface ButtonOptions--><!--Device-unnamed-declare interface ButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonStyle

```TypeScript
buttonStyle?: ButtonStyleMode
```

按钮的样式和重要程度，根据设置枚举值的不同，系统自动会调整按钮的背景色和文字颜色。背景色和文字颜色也支持开发者通过[backgroundColor](arkts-arkui-commonmethod-c.md#backgroundcolor-1)、[fontColor](ButtonAttribute#fontColor)和[role](ButtonAttribute#role)接口设置，实际显示效果以最后一次设置为准。

默认值：ButtonStyleMode.EMPHASIZED

**说明：**

按钮重要程度：强调按钮>普通按钮>文字按钮。

**类型：** ButtonStyleMode

**默认值：** ButtonStyleMode.EMPHASIZED

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonOptions-buttonStyle?: ButtonStyleMode--><!--Device-ButtonOptions-buttonStyle?: ButtonStyleMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controlSize

```TypeScript
controlSize?: ControlSize
```

按钮的尺寸。

默认值：ControlSize.NORMAL

**类型：** ControlSize

**默认值：** ControlSize.NORMAL

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonOptions-controlSize?: ControlSize--><!--Device-ButtonOptions-controlSize?: ControlSize-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## role

```TypeScript
role?: ButtonRole
```

按钮的角色，根据设置枚举值的不同，系统自动会调整按钮的背景色和文字颜色。背景色和文字颜色也支持开发者通过[backgroundColor](arkts-arkui-commonmethod-c.md#backgroundcolor-1)、[fontColor](ButtonAttribute#fontColor)和[buttonStyle](ButtonAttribute#buttonStyle)接口设置，实际显示效果以最后一次设置为准。

默认值：ButtonRole.NORMAL

**类型：** ButtonRole

**默认值：** ButtonRole.NORMAL

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonOptions-role?: ButtonRole--><!--Device-ButtonOptions-role?: ButtonRole-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stateEffect

```TypeScript
stateEffect?: boolean
```

按钮按下时是否开启按压态显示效果。

true：开启按压效果；false：关闭按压效果。

默认值：true

**说明：**

当开启按压态显示效果，且开发者设置状态样式时，会基于状态样式设置完成后的背景色再进行颜色叠加。

**类型：** boolean

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonOptions-stateEffect?: boolean--><!--Device-ButtonOptions-stateEffect?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: ButtonType
```

按钮显示样式。

默认值：ButtonType.ROUNDED_RECTANGLE

API version 18及之后，ButtonType的默认值修改为ButtonType.ROUNDED_RECTANGLE。API version 18之前的版本，ButtonType的默认值为ButtonType.Capsule。

**类型：** ButtonType

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonOptions-type?: ButtonType--><!--Device-ButtonOptions-type?: ButtonType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

