# TextInputController

TextInput组件的控制器继承自[TextContentControllerBase](arkts-arkui-common-textcontentcontrollerbase-c.md#TextContentControllerBase)，涉及的接口有
[getTextContentRect](arkts-arkui-textcontentcontrollerbase-c.md#getTextContentRect-1)、
[getTextContentLineCount](arkts-arkui-textcontentcontrollerbase-c.md#getTextContentLineCount-1)、
[getCaretOffset](arkts-arkui-textcontentcontrollerbase-c.md#getCaretOffset-1)、[addText](arkts-arkui-textcontentcontrollerbase-c.md#addText-1)、
[deleteText](arkts-arkui-textcontentcontrollerbase-c.md#deleteText-1)、[getSelection](arkts-arkui-textcontentcontrollerbase-c.md#getSelection-1)
、[clearPreviewText](arkts-arkui-textcontentcontrollerbase-c.md#clearPreviewText-1)、
[setStyledPlaceholder](arkts-arkui-textcontentcontrollerbase-c.md#setStyledPlaceholder-1)、
[deleteBackward](arkts-arkui-textcontentcontrollerbase-c.md#deleteBackward-1)<!--Del-->以及系统接口
[getText](arkts-arkui-textcontentcontrollerbase-c-sys.md#getText-1)<!--DelEnd-->。

**继承/实现关系：** TextInputController extends [TextContentControllerBase](arkts-arkui-common-textcontentcontrollerbase-c.md#TextContentControllerBase)

**起始版本：** 8

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## caretPosition

```TypeScript
caretPosition(value: number): void
```

设置输入光标的位置。当取值小于0时，取0，大于文本长度时，显示在文本末尾。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 从字符串开始到光标所在位置的字符长度。 |

## constructor

```TypeScript
constructor()
```

TextInputController的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

设置文本选择区域并高亮显示。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number | 是 | 文本选择区域起始位置，文本框中文字的起始位置为0。 |
| selectionEnd | number | 是 | 文本选择区域结束位置。当selectionEnd&lt;0时，按照0处理；当selectionEnd大于文本长度时，按照文本长度处理。 |
| options | SelectionOptions | 否 | 选中文字时的配置。<br/>默认值：MenuPolicy.DEFAULT<br/>从API version 12开始，该接口中的options参数支<br/>持在原子化服务中使用。 [since 12] |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

