# AdvancedDialogV2ButtonOptions

用于初始化AdvancedDialogV2Button对象。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## action

```TypeScript
action?: AdvancedDialogV2ButtonAction
```

按钮的点击事件。默认无事件。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## background

```TypeScript
background?: ColorMetrics
```

按钮的背景。当buttonStyle和role为默认值时生效。默认值跟随buttonStyle。

**类型：** ColorMetrics

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonStyle

```TypeScript
buttonStyle?: ButtonStyleMode
```

按钮的样式。默认值：2in1设备为ButtonStyleMode.NORMAL，其他设备为ButtonStyleMode.TEXTUAL。

**类型：** [ButtonStyleMode](../arkts-components/arkts-arkui-buttonstylemode-e.md)

**默认值：** ButtonStyleMode.TEXTUAL

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ResourceStr
```

按钮的内容。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

是否为默认焦点。true：按钮是默认焦点。false：按钮不是默认焦点。默认值：false

**类型：** boolean

**默认值：** { false }

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

是否可用。true：按钮可用。false：按钮不可用。默认值：true

**类型：** boolean

**默认值：** { true }

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

按钮的字体颜色。当buttonStyle和role为默认值时生效。默认值跟随buttonStyle。

**类型：** ColorMetrics

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## role

```TypeScript
role?: ButtonRole
```

按钮的角色。默认值：ButtonRole.NORMAL

**类型：** [ButtonRole](../arkts-components/arkts-arkui-buttonrole-e.md)

**默认值：** ButtonRole.NORMAL

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

按钮文本的对齐方式。默认值：TextAlign.Start

**类型：** TextAlign

**默认值：** { TextAlign.Start }

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
