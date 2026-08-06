# TextAreaController

Provides the method of switching the cursor position.

**继承/实现关系：** TextAreaController extends [TextContentControllerBase](../../../apis-na/arkts-apis/arkts-na-component/common-textcontentcontrollerbase-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class TextAreaController extends TextContentControllerBase--><!--Device-unnamed-export declare class TextAreaController extends TextContentControllerBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## caretPosition

```TypeScript
caretPosition(value: int): void
```

Called when the position of the insertion cursor is set.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaController-constructor()--><!--Device-TextAreaController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void
```

Text selection is achieved by specifying the start and end positions of the text. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_: \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_If \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_selectionMenuHidden\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_ is set to \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_true\_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_ or a 2-in-1 device is used, calling setTextSelection does not display the context menu even when options is set to \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_MenuPolicy.SHOW\_\_\_HTML\_TAG\_DESC\_USD\_9\_\_\_. \_\_\_HTML\_TAG\_DESC\_USD\_10\_\_\_If the selected text contains an emoji, the emoji is selected when its start position is within the text selection range. \_\_\_HTML\_TAG\_DESC\_USD\_11\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaController-setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void--><!--Device-TextAreaController-setTextSelection(selectionStart: int, selectionEnd: int, options?: SelectionOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | int | 是 | The start position of the selected text.The start position of text in the text box is 0.A value less than 0 is handled as 0.A value greater than the maximum text length is handled as the maximum text length. |
| selectionEnd | int | 是 | The end position of the selected text.A value less than 0 is handled as the value 0.A value greater than the maximum text length is handled as the maximum text length. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Indicates the options of the text selection.Default value is MenuPolicy.DEFAULT. |

## stopEditing

```TypeScript
stopEditing(): void
```

Exit edit state.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextAreaController-stopEditing(): void--><!--Device-TextAreaController-stopEditing(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

