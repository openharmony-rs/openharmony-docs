# GestureHandler

```TypeScript
declare class GestureHandler<T> implements GestureInterface<T>
```

Represents the base type for gesture handlers.

**Inheritance/Implementation:** GestureHandler implements GestureInterface<T>

**Since:** 12

<!--Device-unnamed-declare class GestureHandler<T> implements GestureInterface<T>--><!--Device-unnamed-declare class GestureHandler<T> implements GestureInterface<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowedTypes

```TypeScript
allowedTypes(types: Array<SourceTool>): T
```

Sets the event input sources supported by the gesture handler.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-GestureHandler-allowedTypes(types: Array<SourceTool>): T--><!--Device-GestureHandler-allowedTypes(types: Array<SourceTool>): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| types | Array&lt;[SourceTool](arkts-arkui-common-comp-sourcetool-e.md)&gt; | Yes | Supported input source types. |

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

<!--Device-GestureHandler-tag(tag: string): T--><!--Device-GestureHandler-tag(tag: string): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tag | string | Yes | Gesture handler tag. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |
