# TextAreaController

Provides the method of switching the cursor position.

**继承/实现关系：** TextAreaController extends TextContentControllerBase

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class TextAreaController--><!--Device-unnamed-export declare class TextAreaController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## caretPosition

```TypeScript
caretPosition(value: int): void
```

Called when the position of the insertion cursor is set.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaController-caretPosition(value: int): void--><!--Device-TextAreaController-caretPosition(value: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int | 是 | Length from the start of the string to the position where the caret is located. |

## constructor

```TypeScript
constructor()
```

constructor. A constructor used to create a TextAreaController object.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaController-constructor()--><!--Device-TextAreaController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void
```

Text selection is achieved by specifying the start and end positions of the text. &lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;: <br>If &lt;em&gt;selectionMenuHidden&lt;/em&gt; is set to &lt;em&gt;true&lt;/em&gt; or a 2-in-1 device is used, calling setTextSelection does not display the context menu even when options is set to &lt;em&gt;MenuPolicy.SHOW&lt;/em&gt;. <br>If the selected text contains an emoji, the emoji is selected when its start position is within the text selection range. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaController-setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void--><!--Device-TextAreaController-setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | int | 是 | The start position of the selected text. The start position of text in the text box is 0. A value less than 0 is handled as 0. A value greater than the maximum text length is handled as the maximum text length. |
| selectionEnd | int | 是 | The end position of the selected text. A value less than 0 is handled as the value 0. A value greater than the maximum text length is handled as the maximum text length. |
| options | [SelectionOptions](../arkts-components/arkts-arkui-selectionoptions-i.md) | 否 | Indicates the options of the text selection. Default value is MenuPolicy.DEFAULT. |

## stopEditing

```TypeScript
stopEditing(): void
```

Exit edit state.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaController-stopEditing(): void--><!--Device-TextAreaController-stopEditing(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

