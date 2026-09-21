# TextEditControllerEx

```TypeScript
declare interface TextEditControllerEx extends TextBaseController
```

Implements an extended text editing controller.

Inherits [TextBaseController](arkts-arkui-textbasecontroller-i.md).

**Inheritance/Implementation:** TextEditControllerEx extends [TextBaseController](arkts-arkui-textbasecontroller-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getCaretOffset

```TypeScript
getCaretOffset(): number
```

Obtains the current position of the caret.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PreviewText](arkts-arkui-previewtext-i.md) | Preview text. |

## isEditing

```TypeScript
isEditing(): boolean
```

Obtains the editing status of the rich text.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Offset of the caret. If the offset is outside the range of all content, the setting fails. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the caret offset is set successfully.<br>Returns **true** if it is set successfully; returns **false** otherwise. |

## stopEditing

```TypeScript
stopEditing(): void
```

Stops editing.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
