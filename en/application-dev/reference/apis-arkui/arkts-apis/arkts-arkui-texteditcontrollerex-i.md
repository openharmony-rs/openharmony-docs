# TextEditControllerEx

```TypeScript
declare interface TextEditControllerEx extends TextBaseController
```

Implements an extended text editing controller.

Inherits [TextBaseController](arkts-arkui-textbasecontroller-i.md).

**Inheritance/Implementation:** TextEditControllerEx extends [TextBaseController](arkts-arkui-textbasecontroller-i.md)

**Since:** 12

<!--Device-unnamed-declare interface TextEditControllerEx extends TextBaseController--><!--Device-unnamed-declare interface TextEditControllerEx extends TextBaseController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getCaretOffset

```TypeScript
getCaretOffset(): number
```

Obtains the current position of the caret.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextEditControllerEx-getCaretOffset(): number--><!--Device-TextEditControllerEx-getCaretOffset(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Position of the caret. |

## getPreviewText

```TypeScript
getPreviewText?(): PreviewText
```

Obtains the preview text.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextEditControllerEx-getPreviewText?(): PreviewText--><!--Device-TextEditControllerEx-getPreviewText?(): PreviewText-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PreviewText](arkts-arkui-previewtext-i.md) | Preview text information, including the start position index and text content of the preview text. |

## isEditing

```TypeScript
isEditing(): boolean
```

Obtains the editing status of the rich text.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextEditControllerEx-isEditing(): boolean--><!--Device-TextEditControllerEx-isEditing(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Editing status of the rich text. **true** means that the text is in editable state, and **false** means the opposite. |

## setCaretOffset

```TypeScript
setCaretOffset(offset: number): boolean
```

Sets the offset of the caret.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextEditControllerEx-setCaretOffset(offset: number): boolean--><!--Device-TextEditControllerEx-setCaretOffset(offset: number): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Caret offset position. The value ranges from 0 to the text length. If the value exceeds the content range, the setting fails. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the cursor is set successfully.<br>The value **true** indicates that the cursor is set successfully, and **false** indicates the opposite. |

## stopEditing

```TypeScript
stopEditing(): void
```

Stops editing.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextEditControllerEx-stopEditing(): void--><!--Device-TextEditControllerEx-stopEditing(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
