# AdvancedDialogV2ButtonOptions

用于初始化AdvancedDialogV2Button对象。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-export declare interface AdvancedDialogV2ButtonOptions--><!--Device-unnamed-export declare interface AdvancedDialogV2ButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: AdvancedDialogV2ButtonAction
```

按钮的点击事件。 默认无事件。

**类型：** [AdvancedDialogV2ButtonAction](arkts-arkui-advanceddialogv2buttonaction-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2ButtonOptions-action?: AdvancedDialogV2ButtonAction--><!--Device-AdvancedDialogV2ButtonOptions-action?: AdvancedDialogV2ButtonAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## background

```TypeScript
background?: ColorMetrics
```

按钮的背景。当buttonStyle和role为默认值时生效。 默认值跟随buttonStyle。

**类型：** [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2ButtonOptions-background?: ColorMetrics--><!--Device-AdvancedDialogV2ButtonOptions-background?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonStyle

```TypeScript
buttonStyle?: ButtonStyleMode
```

按钮的样式。 默认值：2in1设备为ButtonStyleMode.NORMAL，其他设备为ButtonStyleMode.TEXTUAL。

**类型：** ButtonStyleMode

**默认值：** ButtonStyleMode.TEXTUAL

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2ButtonOptions-buttonStyle?: ButtonStyleMode--><!--Device-AdvancedDialogV2ButtonOptions-buttonStyle?: ButtonStyleMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ResourceStr
```

按钮的内容。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2ButtonOptions-content: ResourceStr--><!--Device-AdvancedDialogV2ButtonOptions-content: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

是否为默认焦点。 true：按钮是默认焦点。 false：按钮不是默认焦点。 默认值：false

**类型：** boolean

**默认值：** { false }

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2ButtonOptions-defaultFocus?: boolean--><!--Device-AdvancedDialogV2ButtonOptions-defaultFocus?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

是否可用。 true：按钮可用。 false：按钮不可用。 默认值：true

**类型：** boolean

**默认值：** { true }

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2ButtonOptions-enabled?: boolean--><!--Device-AdvancedDialogV2ButtonOptions-enabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

按钮的字体颜色。当buttonStyle和role为默认值时生效。 默认值跟随buttonStyle。

**类型：** [ColorMetrics](../../apis-na/arkts-apis/arkts-na-graphics-colormetrics-c.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2ButtonOptions-fontColor?: ColorMetrics--><!--Device-AdvancedDialogV2ButtonOptions-fontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## role

```TypeScript
role?: ButtonRole
```

按钮的角色。 默认值：ButtonRole.NORMAL

**类型：** ButtonRole

**默认值：** ButtonRole.NORMAL

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2ButtonOptions-role?: ButtonRole--><!--Device-AdvancedDialogV2ButtonOptions-role?: ButtonRole-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

按钮文本的对齐方式。 默认值：TextAlign.Start

**类型：** TextAlign

**默认值：** { TextAlign.Start }

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2ButtonOptions-textAlign?: TextAlign--><!--Device-AdvancedDialogV2ButtonOptions-textAlign?: TextAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

