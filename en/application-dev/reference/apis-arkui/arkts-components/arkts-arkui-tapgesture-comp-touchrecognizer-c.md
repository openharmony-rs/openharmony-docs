# TouchRecognizer

```TypeScript
declare class TouchRecognizer
```

Defines the touch gesture recognizer object, which supports obtaining touch target information, canceling the current touch interaction, and determining whether the bound node belongs to a specified component subtree. It is applicable to touch processing and event distribution control scenarios.

**Since:** 20

<!--Device-unnamed-declare class TouchRecognizer--><!--Device-unnamed-declare class TouchRecognizer-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancelTouch

```TypeScript
cancelTouch(): void
```

Sends a touch cancellation event to the current touch gesture recognizer. It is applicable to scenarios such as page state changes, dialog box interruptions, or business logic that needs to actively terminate the current touch interaction.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TouchRecognizer-cancelTouch(): void--><!--Device-TouchRecognizer-cancelTouch(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getEventTargetInfo

```TypeScript
getEventTargetInfo(): EventTargetInfo
```

Obtains the information about the component corresponding to this touch gesture recognizer.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TouchRecognizer-getEventTargetInfo(): EventTargetInfo--><!--Device-TouchRecognizer-getEventTargetInfo(): EventTargetInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [EventTargetInfo](arkts-arkui-tapgesture-comp-eventtargetinfo-c.md) | Information about the component corresponding to the current touch gesture recognizer. |

## isHostBelongsTo

```TypeScript
isHostBelongsTo(uniqueId: number): boolean
```

Returns whether the node bound to the current touch gesture recognizer is a descendant node of the passed-in component. It is applicable to scenarios where it is determined whether an event comes from the target component subtree during touch processing or gesture distribution.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TouchRecognizer-isHostBelongsTo(uniqueId: int): boolean--><!--Device-TouchRecognizer-isHostBelongsTo(uniqueId: int): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uniqueId | number | Yes | Unique ID of the component. This ID can be obtained via the [getUniqueId](arkts-arkui-tapgesture-comp-eventtargetinfo-c.md#getuniqueid) API.<br>If the value does not match any component unique ID, **false** is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the node bound to the current touch gesture recognizer is a descendant node of the passed-in component. The value **true** indicates that the current bound node is a descendant node of the passed-in component, and **false** indicates the opposite. |
