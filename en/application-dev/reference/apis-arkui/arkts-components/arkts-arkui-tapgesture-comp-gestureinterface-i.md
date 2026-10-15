# GestureInterface

```TypeScript
interface GestureInterface<T>
```

Configures common attributes of gestures, supporting setting gesture tags and input types for gesture responses.

**Since:** 11

<!--Device-unnamed-interface GestureInterface<T>--><!--Device-unnamed-interface GestureInterface<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowedTypes

```TypeScript
allowedTypes(types: Array<SourceTool>): T
```

Sets the input types that can trigger the gesture response.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-GestureInterface-allowedTypes(types: Array<SourceTool>): T--><!--Device-GestureInterface-allowedTypes(types: Array<SourceTool>): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| types | Array&lt;[SourceTool](arkts-arkui-common-comp-sourcetool-e.md)&gt; | Yes | Input types that can trigger the gesture response. |

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

<!--Device-GestureInterface-tag(tag: string): T--><!--Device-GestureInterface-tag(tag: string): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tag | string | Yes | Gesture tag. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |
