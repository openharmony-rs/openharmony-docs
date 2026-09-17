# GestureInterface

Defines the gesture API.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowedTypes

```TypeScript
allowedTypes(types: Array<SourceTool>): T
```

Sets the input types that can trigger the gesture response.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| types | Array&lt;[SourceTool](arkts-arkui-sourcetool-e.md)&gt; | Yes | Input types that can trigger the gesture response. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## tag

```TypeScript
tag(tag: string): T
```

Sets a gesture tag.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tag | string | Yes | Gesture tag. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |
