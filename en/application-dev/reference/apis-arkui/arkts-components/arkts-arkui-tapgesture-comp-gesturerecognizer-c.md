# GestureRecognizer

```TypeScript
declare class GestureRecognizer
```

Gesture recognizer object.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getEventTargetInfo

```TypeScript
getEventTargetInfo(): EventTargetInfo
```

Obtains the information about the component corresponding to this gesture recognizer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the preset gesture will detect the number of fingers on the screen. **true** if the gesture event is bound and detects the number of fingers; **false** otherwise. |

## isHostBelongsTo

```TypeScript
isHostBelongsTo(uniqueId: number): boolean
```

Returns whether the node bound to the current gesture recognizer is a descendant of the specified component.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uniqueId | number | Yes | Unique ID of the component. This ID can be obtained via the [getUniqueId](arkts-arkui-tapgesture-comp-eventtargetinfo-c.md#getuniqueid) API. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the node bound to the current gesture recognizer is a descendant of the specified component. Returns **true** if the bound node is a descendant, and **false** otherwise. |

## isValid

```TypeScript
isValid(): boolean
```

Whether the current gesture recognizer is valid.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the current gesture recognizer is valid.<br>Returns **false** if the component bound to this recognizer is destroyed or if the recognizer is not on the response chain. <br>Returns **true** if the bound component exists and the recognizer is in the response chain. |

## preventBegin

```TypeScript
preventBegin(): void
```

Prevents a gesture recognizer from participating in the current gesture recognition before all fingers are lifted. If the system has already determined the result of the gesture recognizer (regardless of success or failure), calling this API will be ineffective. Unlike GestureRecognizer.[setEnabled](#setenabled)(isEnabled: boolean), which only affects callback execution, this API prevents the recognizer from participating in the recognition process entirely.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setEnabled

```TypeScript
setEnabled(isEnabled: boolean): void
```

Sets the enabled state of this gesture recognizer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Enabled state to set. The value **true** means that the gesture recognizer is enabled and will trigger events, and **false** means the opposite. |
