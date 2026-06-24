# TextAreaController

TextArea组件的控制器继承自[TextContentControllerBase](arkts-arkui-common-textcontentcontrollerbase-c.md#TextContentControllerBase)，涉及的接口有
[getTextContentRect](arkts-arkui-textcontentcontrollerbase-c.md#getTextContentRect-1)、
[getTextContentLineCount](arkts-arkui-textcontentcontrollerbase-c.md#getTextContentLineCount-1)、
[getCaretOffset](arkts-arkui-textcontentcontrollerbase-c.md#getCaretOffset-1)、[addText](arkts-arkui-textcontentcontrollerbase-c.md#addText-1)、
[deleteText](arkts-arkui-textcontentcontrollerbase-c.md#deleteText-1)、[getSelection](arkts-arkui-textcontentcontrollerbase-c.md#getSelection-1)
、[clearPreviewText](arkts-arkui-textcontentcontrollerbase-c.md#clearPreviewText-1)、
[setStyledPlaceholder](arkts-arkui-textcontentcontrollerbase-c.md#setStyledPlaceholder-1)、
[deleteBackward](arkts-arkui-textcontentcontrollerbase-c.md#deleteBackward-1)<!--Del-->以及系统接口
[getText](arkts-arkui-textcontentcontrollerbase-c-sys.md#getText-1)<!--DelEnd-->。

**继承/实现关系：** TextAreaController extends [TextContentControllerBase](arkts-arkui-common-textcontentcontrollerbase-c.md#TextContentControllerBase)

**起始版本：** 8

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## caretPosition

```TypeScript
caretPosition(value: number): void
```

设置输入光标的位置。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 从字符串开始到光标所在位置的字符长度。当value字符串长度时，按照字符串长度处理。 |

## constructor

```TypeScript
constructor()
```

TextAreaController的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

组件在获焦状态下，调用该接口设置文本选择区域并高亮显示，且只有在selectionStart小于selectionEnd时，文字才会被选取、高亮显示。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number | 是 | 文本选择区域起始位置，文本框中文字的起始位置为0。<br/>当selectionStart小于0时，按0处理；当selectionStart大于文字最大长度时，<br/>按照文字最大长度处理。 |
| selectionEnd | number | 是 | 文本选择区域结束位置。<br/>当selectionEnd小于0时，按0处理；当selectionEnd大于文字最大长度时，按照文字最大长度处理。 |
| options | SelectionOptions | 否 | 选中文字时的配置。<br/>默认值：MenuPolicy.DEFAULT<br/>[since 12] |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

