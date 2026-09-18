# GestureHandler

Represents the base type for gesture handlers.

**Inheritance/Implementation:** GestureHandler implements GestureInterface<T>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowedTypes

```TypeScript
allowedTypes(types: Array<SourceTool>): T
```

Sets the event input sources supported by the gesture handler.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| types | Array&lt;[SourceTool](arkts-arkui-sourcetool-e.md)&gt; | Yes | Supported input source types. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## tag

```TypeScript
tag(tag: string): T
```

Sets the tag for the gesture handler.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tag | string | Yes | Gesture handler tag. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |
