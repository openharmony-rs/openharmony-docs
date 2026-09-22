# TextContentControllerBase

```TypeScript
declare abstract class TextContentControllerBase
```

Represents the base controller for **TextInput**, **TextArea**, and **Search** components.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getText

```TypeScript
getText(range?: TextRange): string
```

Obtains the text content within a specified range.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [TextRange](../arkts-apis/arkts-arkui-textrange-i.md) | No | Range of the text content to obtain, defined by start and end positions.<br>If the range is not specified, the entire text is obtained by default. If the start position is not specified, it defaults to index 0. If the end position is not specified, it defaults to the end of the text. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Text content within the specified range. |
