# TouchRecognizer

Represents a touch gesture recognizer.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancelTouch

```TypeScript
cancelTouch(): void
```

Sends a touch cancellation event to this touch gesture recognizer.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getEventTargetInfo

```TypeScript
getEventTargetInfo(): EventTargetInfo
```

Obtains the information about the component corresponding to this touch gesture recognizer.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [EventTargetInfo](arkts-arkui-eventtargetinfo-c.md) | Information about the component corresponding to the current touch gesture recognizer. |

## isHostBelongsTo

```TypeScript
isHostBelongsTo(uniqueId: number): boolean
```

Returns whether the node bound to the current touch gesture recognizer is a descendant of the specified component.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uniqueId | number | Yes | Unique ID of the component. This ID can be obtained via the [getUniqueId](arkts-arkui-eventtargetinfo-c.md#getuniqueid) API. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the node bound to the current touch gesture recognizer is a descendant of the specified component. Returns **true** if the bound node is a descendant, and **false** otherwise. |
