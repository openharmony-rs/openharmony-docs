# TextInputController

TextInput组件的控制器继承自 [TextContentControllerBase](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md#textcontentcontrollerbase)， 涉及的接口有 [getTextContentRect](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md#gettextcontentrect) 、 [getTextContentLineCount](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md#gettextcontentlinecount) 、[getCaretOffset](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md#getcaretoffset11)、 [addText](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md#addtext15)、 [deleteText](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md#deletetext15)、 [getSelection](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md#getselection15)、 [clearPreviewText](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md#clearpreviewtext17)、 [setStyledPlaceholder](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md#setstyledplaceholder22) 、[deleteBackward](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md#deletebackward23)、 [scrollToVisible](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md#scrolltovisible23)&lt;!- -Del--&gt;以及系统接口[getText](../../../reference/apis-arkui/arkui-ts/ts-text-common-sys.md#gettext19)&lt;!--DelEnd--&gt;。

**继承/实现关系：** TextInputController extends TextContentControllerBase

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class TextInputController--><!--Device-unnamed-export declare class TextInputController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## caretPosition

```TypeScript
caretPosition(value: int): void
```

设置输入光标的位置。当取值小于0时，取0，大于文本长度时，显示在文本末尾。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextInputController-caretPosition(value: int): void--><!--Device-TextInputController-caretPosition(value: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int | 是 |  |

## constructor

```TypeScript
constructor()
```

TextInputController的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextInputController-constructor()--><!--Device-TextInputController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void
```

设置文本选择区域并高亮显示。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextInputController-setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void--><!--Device-TextInputController-setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | int | 是 | 文本选择区域起始位置，文本框中文字的起始位置为0。 |
| selectionEnd | int | 是 | 文本选择区域结束位置。当selectionEnd<0时，按照0处理；当selectionEnd大于文本长度时，按照文本长度处理。 |
| options | [SelectionOptions](../arkts-components/arkts-arkui-selectionoptions-i.md) | 否 | 选中文字时的配置。&lt;br /&gt;默认值：MenuPolicy.DEFAULT |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextInputController-stopEditing(): void--><!--Device-TextInputController-stopEditing(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

