# GestureRecognizer

```TypeScript
declare class GestureRecognizer
```

Defines the gesture recognizer object, which supports querying gesture tag, type, state, and target component information, controlling the enabled state of the recognizer, blocking the current recognition process, and determining whether the bound node belongs to a specified component subtree. It is applicable to gesture recognition state management and gesture competition handling scenarios.

**Since:** 12

<!--Device-unnamed-declare class GestureRecognizer--><!--Device-unnamed-declare class GestureRecognizer-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getEventTargetInfo

```TypeScript
getEventTargetInfo(): EventTargetInfo
```

Obtains the information about the component corresponding to this gesture recognizer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureRecognizer-getEventTargetInfo(): EventTargetInfo--><!--Device-GestureRecognizer-getEventTargetInfo(): EventTargetInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [EventTargetInfo](arkts-arkui-tapgesture-comp-eventtargetinfo-c.md) | Information about the component corresponding to the current gesture recognizer. |

## getFingerCount

```TypeScript
getFingerCount(): number
```

Obtains the number of fingers required to trigger the preset gesture.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-GestureRecognizer-getFingerCount(): number--><!--Device-GestureRecognizer-getFingerCount(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of fingers required to trigger the preset gesture.<br>Value range: an integer from 1 to 10. |

## getState

```TypeScript
getState(): GestureRecognizerState
```

Obtains the state of this gesture recognizer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureRecognizer-getState(): GestureRecognizerState--><!--Device-GestureRecognizer-getState(): GestureRecognizerState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [GestureRecognizerState](arkts-arkui-tapgesture-comp-gesturerecognizerstate-e.md) | State of the gesture recognizer. |

## getTag

```TypeScript
getTag(): string
```

Obtains the tag of this gesture recognizer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureRecognizer-getTag(): string--><!--Device-GestureRecognizer-getTag(): string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Tag of the current gesture recognizer. |

## getType

```TypeScript
getType(): GestureControl.GestureType
```

Obtains the type of this gesture recognizer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureRecognizer-getType(): GestureControl.GestureType--><!--Device-GestureRecognizer-getType(): GestureControl.GestureType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [GestureControl.GestureType](arkts-arkui-tapgesture-comp-gesturetype-e.md) | Type of the current gesture recognizer. |

## isBuiltIn

```TypeScript
isBuiltIn(): boolean
```

Obtains whether this gesture recognizer is a built-in gesture.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureRecognizer-isBuiltIn(): boolean--><!--Device-GestureRecognizer-isBuiltIn(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the current gesture recognizer is a built-in gesture. The value **true** means that the gesture recognizer is a built-in gesture, and **false** means the opposite. |

## isEnabled

```TypeScript
isEnabled(): boolean
```

Obtains the enabled state of this gesture recognizer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureRecognizer-isEnabled(): boolean--><!--Device-GestureRecognizer-isEnabled(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Enabled state of the gesture recognizer. The value **true** means that the gesture recognizer is enabled and will trigger events, and **false** means the opposite. |

## isFingerCountLimit

```TypeScript
isFingerCountLimit(): boolean
```

Checks whether the preset gesture detects the number of fingers on the screen.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-GestureRecognizer-isFingerCountLimit(): boolean--><!--Device-GestureRecognizer-isFingerCountLimit(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the preset gesture will detect the number of fingers on the screen. **true** if the gesture event is bound and detects the number of fingers; **false** otherwise. |

## isHostBelongsTo

```TypeScript
isHostBelongsTo(uniqueId: number): boolean
```

Returns whether the node bound to the current gesture recognizer is a descendant node of the passed-in component. It is applicable to scenarios where it is determined whether an event comes from the target component subtree during touch processing or gesture distribution.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-GestureRecognizer-isHostBelongsTo(uniqueId: int): boolean--><!--Device-GestureRecognizer-isHostBelongsTo(uniqueId: int): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uniqueId | number | Yes | Unique ID of the component. This ID can be obtained via the [getUniqueId](arkts-arkui-tapgesture-comp-eventtargetinfo-c.md#getuniqueid) API.<br>If the value is abnormal, **false** is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the node bound to the current gesture recognizer is a descendant node of the passed-in component. The value **true** indicates that the current bound node is a descendant node of the passed-in component, and **false** indicates the opposite. |

## isValid

```TypeScript
isValid(): boolean
```

Whether the current gesture recognizer is valid.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-GestureRecognizer-isValid(): boolean--><!--Device-GestureRecognizer-isValid(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the current gesture recognizer is valid.<br>Returns **false** if the component bound to this recognizer is destroyed or if the recognizer is not on the response chain. <br>Returns **true** if the bound component exists and the recognizer is in the response chain. |

## preventBegin

```TypeScript
preventBegin(): void
```

Blocks the gesture recognizer from participating in the current gesture recognition before all fingers are lifted. It is applicable to scenarios such as custom gesture competition or temporarily giving up the current gesture recognition based on business conditions. If the system has already determined the result of this gesture recognizer (whether successful or not), calling this API has no effect. This method differs from GestureRecognizer.[setEnabled](#setenabled)(isEnabled: boolean). [setEnabled](#setenabled) does not block the gesture recognizer object from participating in the gesture recognition process, but only affects whether the callback function corresponding to the gesture is executed.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-GestureRecognizer-preventBegin(): void--><!--Device-GestureRecognizer-preventBegin(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setEnabled

```TypeScript
setEnabled(isEnabled: boolean): void
```

Sets the enabled state of this gesture recognizer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureRecognizer-setEnabled(isEnabled: boolean): void--><!--Device-GestureRecognizer-setEnabled(isEnabled: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Enabled status of the gesture recognizer. The value **true** indicates that the current gesture recognizer can call back app events, and **false** indicates that it does not call back app events.<br>Currently, this takes effect only when set for [PanRecognizer](arkts-arkui-tapgesture-comp-panrecognizer-c.md). |
