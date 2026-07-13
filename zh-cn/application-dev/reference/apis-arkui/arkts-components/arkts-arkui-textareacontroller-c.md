# TextAreaController

TextArea组件的控制器继承自[TextContentControllerBase](arkts-arkui-textcontentcontrollerbase-c.md)，涉及的接口有
[getTextContentRect](arkts-arkui-textcontentcontrollerbase-c.md#gettextcontentrect-1)、
[getTextContentLineCount](arkts-arkui-textcontentcontrollerbase-c.md#gettextcontentlinecount-1)、
[getCaretOffset](arkts-arkui-textcontentcontrollerbase-c.md#getcaretoffset-1)、[addText](arkts-arkui-textcontentcontrollerbase-c.md#addtext-1)、
[deleteText](arkts-arkui-textcontentcontrollerbase-c.md#deletetext-1)、[getSelection](arkts-arkui-textcontentcontrollerbase-c.md#getselection-1)
、[clearPreviewText](arkts-arkui-textcontentcontrollerbase-c.md#clearpreviewtext-1)、
[setStyledPlaceholder](arkts-arkui-textcontentcontrollerbase-c.md#setstyledplaceholder-1)、
[deleteBackward](arkts-arkui-textcontentcontrollerbase-c.md#deletebackward-1)<!--Del-->以及系统接口
[getText](arkts-arkui-textcontentcontrollerbase-c-sys.md#gettext-1)<!--DelEnd-->。

**继承/实现关系：** TextAreaController extends [TextContentControllerBase](arkts-arkui-textcontentcontrollerbase-c.md)

**起始版本：** 8

**系统能力：** 
- API版本10+：SystemCapability.ArkUI.ArkUI.Full

## caretPosition

```TypeScript
caretPosition(value: number): void
```

设置输入光标的位置。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 从字符串开始到光标所在位置的字符长度。&lt;/br&gt;当value&lt;0时，按照0处理。当value&gt;字符串长度时，按照字符串长度处理。 |

## constructor

```TypeScript
constructor()
```

TextAreaController的构造函数。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

组件在获焦状态下，调用该接口设置文本选择区域并高亮显示，且只有在selectionStart小于selectionEnd时，文字才会被选取、高亮显示。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number | 是 | 文本选择区域起始位置，文本框中文字的起始位置为0。<br/>当selectionStart小于0时，按0处理；当selectionStart大于文字最大长度时，按照文字最大长度处理。<br/> |
| selectionEnd | number | 是 | 文本选择区域结束位置。<br/>当selectionEnd小于0时，按0处理；当selectionEnd大于文字最大长度时，按照文字最大长度处理。<br/> |
| options | SelectionOptions | 否 | 选中文字时的配置。<br />默认值：MenuPolicy.DEFAULT<br/><br>**起始版本：** 12 |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

