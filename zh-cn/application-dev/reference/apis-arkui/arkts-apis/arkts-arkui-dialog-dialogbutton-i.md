# DialogButton

固定样式对话框的按钮配置。

**起始版本：** 26.1.0

<!--Device-dialog-declare interface DialogButton--><!--Device-dialog-declare interface DialogButton-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DialogButtonOrientation, DialogState, DialogResult, DialogBaseController, DialogBaseAlignment, DialogDismissal } from '@kit.ArkUI';
```

## action

```TypeScript
action: VoidCallback
```

点击按钮时执行的回调。

**类型：** VoidCallback

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-DialogButton-action: VoidCallback--><!--Device-DialogButton-action: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

按钮背景色。

**类型：** ResourceColor

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-DialogButton-backgroundColor?: ResourceColor--><!--Device-DialogButton-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

按钮是否为默认焦点。

**类型：** boolean

**默认值：** false

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-DialogButton-defaultFocus?: boolean--><!--Device-DialogButton-defaultFocus?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

点击按钮时是否响应。

**类型：** boolean

**默认值：** true

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-DialogButton-enabled?: boolean--><!--Device-DialogButton-enabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

按钮文字颜色。

**类型：** ResourceColor

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-DialogButton-fontColor?: ResourceColor--><!--Device-DialogButton-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primary

```TypeScript
primary?: boolean
```

定义按钮是否默认响应回车/空格键。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-DialogButton-primary?: boolean--><!--Device-DialogButton-primary?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: DialogButtonStyle
```

按钮的样式。

**类型：** DialogButtonStyle

**默认值：** DialogButtonStyle.DEFAULT

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-DialogButton-style?: DialogButtonStyle--><!--Device-DialogButton-style?: DialogButtonStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

按钮的文本内容。

**类型：** ResourceStr

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-DialogButton-value: ResourceStr--><!--Device-DialogButton-value: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

