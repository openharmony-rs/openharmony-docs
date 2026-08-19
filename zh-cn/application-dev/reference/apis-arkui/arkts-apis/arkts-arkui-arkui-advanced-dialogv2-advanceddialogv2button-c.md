# AdvancedDialogV2Button

弹出框操作区按钮。 > **说明：** > > buttonStyle和role优先级高于fontColor和background。如果buttonStyle和role设置的是默认值，那么fontColor和background可生效。 > > 若同时给多个按钮设置defaultFocus，那么默认焦点为设置defaultFocus按钮显示顺序的第一个。

**起始版本：** 18

<!--Device-unnamed-export declare class AdvancedDialogV2Button--><!--Device-unnamed-export declare class AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: AdvancedDialogV2ButtonOptions)
```

AdvancedDialogV2Button的构造函数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2Button-constructor(options: AdvancedDialogV2ButtonOptions)--><!--Device-AdvancedDialogV2Button-constructor(options: AdvancedDialogV2ButtonOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AdvancedDialogV2ButtonOptions](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2buttonoptions-i.md) | 是 | 按钮配置信息。 |

## action

```TypeScript
@Trace
  action?: AdvancedDialogV2ButtonAction
```

按钮的点击事件。 默认无事件。

**类型：** [AdvancedDialogV2ButtonAction](arkts-arkui-advanceddialogv2buttonaction-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2Button-@Trace  action?: AdvancedDialogV2ButtonAction--><!--Device-AdvancedDialogV2Button-@Trace  action?: AdvancedDialogV2ButtonAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## background

```TypeScript
@Trace
  background?: ColorMetrics
```

按钮的背景。当buttonStyle和role为默认值时生效。 默认值跟随buttonStyle。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2Button-@Trace  background?: ColorMetrics--><!--Device-AdvancedDialogV2Button-@Trace  background?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonStyle

```TypeScript
@Trace
  buttonStyle?: ButtonStyleMode
```

按钮的样式。 默认值：2in1设备为ButtonStyleMode.NORMAL，其他设备为ButtonStyleMode.TEXTUAL。

**类型：** ButtonStyleMode

**默认值：** ButtonStyleMode.TEXTUAL

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2Button-@Trace  buttonStyle?: ButtonStyleMode--><!--Device-AdvancedDialogV2Button-@Trace  buttonStyle?: ButtonStyleMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
@Trace
  content: ResourceStr
```

按钮的内容。

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2Button-@Trace  content: ResourceStr--><!--Device-AdvancedDialogV2Button-@Trace  content: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
@Trace
  defaultFocus?: boolean
```

是否为默认焦点。 true：按钮是默认焦点。 false：按钮不是默认焦点。 默认值：false

**类型：** boolean

**默认值：** { false }

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2Button-@Trace  defaultFocus?: boolean--><!--Device-AdvancedDialogV2Button-@Trace  defaultFocus?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
@Trace
  enabled?: boolean
```

是否可用。 true：按钮可用。 false：按钮不可用。 默认值：true

**类型：** boolean

**默认值：** { true }

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2Button-@Trace  enabled?: boolean--><!--Device-AdvancedDialogV2Button-@Trace  enabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
@Trace
  fontColor?: ColorMetrics
```

按钮的字体颜色。当buttonStyle和role为默认值时生效。 默认值跟随buttonStyle。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2Button-@Trace  fontColor?: ColorMetrics--><!--Device-AdvancedDialogV2Button-@Trace  fontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## role

```TypeScript
@Trace
  role?: ButtonRole
```

按钮的角色。 默认值：ButtonRole.NORMAL

**类型：** ButtonRole

**默认值：** ButtonRole.NORMAL

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2Button-@Trace  role?: ButtonRole--><!--Device-AdvancedDialogV2Button-@Trace  role?: ButtonRole-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
@Trace
  textAlign?: TextAlign
```

按钮文本的对齐方式。 默认值：TextAlign.Start

**类型：** TextAlign

**默认值：** { TextAlign.Start }

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AdvancedDialogV2Button-@Trace  textAlign?: TextAlign--><!--Device-AdvancedDialogV2Button-@Trace  textAlign?: TextAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

