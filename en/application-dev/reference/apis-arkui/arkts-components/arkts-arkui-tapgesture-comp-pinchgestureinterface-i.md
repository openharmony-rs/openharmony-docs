# PinchGestureInterface

```TypeScript
interface PinchGestureInterface extends GestureInterface<PinchGestureInterface>
```

**PinchGesture** is used to trigger a pinch gesture, which requires two to five fingers with a minimum 5 vp distance between the fingers.

> **NOTE:** 
> 
> To trigger the pinch gesture again after successful recognition, all fingers must be lifted and then make
> contact again to satisfy the recognition criteria.

**Inheritance/Implementation:** PinchGestureInterface extends GestureInterface<PinchGestureInterface>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [[Call]]

```TypeScript
(value?: { fingers?: number; distance?: number }): PinchGestureInterface
```

Sets the parameters for the pinch gesture. Inherits from [GestureInterface&lt;T&gt;](arkts-arkui-tapgesture-comp-gestureinterface-i.md).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { fingers?: number; distance?: number } | No | Parameters for the pinch gesture.<br> - **fingers**: minimum number of fingers to trigger a pinch. The value ranges from 2 to 5.<br>Default value: **2** <br>Value range: [2, 5]. Values outside this range are automatically adjusted to the default value.<br>While more fingers than the minimum number can be pressed to trigger the gesture, only the first fingers of the minimum number participate in gesture calculation. <br> - **distance**: minimum recognition distance, in vp. This distance refers to the difference between the current average distance from the multiple finger positions to their center point and the average distance when the fingers first made contact. If this difference meets or exceeds the minimum recognition distance, the pinch gesture is recognized.<br>Default value: **5**<br>**NOTE:** <br>Value range: (0, +∞). If the value is less than or equal to 0, it will be converted to the default value. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-tapgesture-comp-pinchgestureinterface-i.md) |  |

<a id="call-1"></a>

## [[Call]]

```TypeScript
(options?: PinchGestureHandlerOptions): PinchGestureInterface
```

Sets the parameters for the pinch gesture. Compared with PinchGesture)}, this API adds the **isFingerCountLimited** parameter to **options**, which determines whether to enforce the exact number of fingers touching the screen.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PinchGestureHandlerOptions](arkts-arkui-tapgesture-comp-pinchgesturehandleroptions-i.md) | No | Parameters of the pinch gesture handler. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-tapgesture-comp-pinchgestureinterface-i.md) |  |

## onActionCancel

```TypeScript
onActionCancel(event: () => void): PinchGestureInterface
```

Triggered when a touch cancellation event occurs after successful pinch gesture recognition. No gesture event information is returned.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback for the pinch event. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-tapgesture-comp-pinchgestureinterface-i.md) |  |

<a id="onactioncancel-1"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): PinchGestureInterface
```

Triggered when a touch cancellation event occurs after successful pinch gesture recognition. Compared with [onActionCancel](#onactioncancel), this callback returns gesture event information.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback for the pinch event. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-tapgesture-comp-pinchgestureinterface-i.md) |  |

## onActionEnd

```TypeScript
onActionEnd(event: (event: GestureEvent) => void): PinchGestureInterface
```

Triggered when all fingers are lifted after successful pinch gesture recognition.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for the pinch event. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-tapgesture-comp-pinchgestureinterface-i.md) |  |

## onActionStart

```TypeScript
onActionStart(event: (event: GestureEvent) => void): PinchGestureInterface
```

Triggered after the pinch gesture is recognized.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for the pinch event. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-tapgesture-comp-pinchgestureinterface-i.md) |  |

## onActionUpdate

```TypeScript
onActionUpdate(event: (event: GestureEvent) => void): PinchGestureInterface
```

Triggered when the user moves the finger in the pinch gesture on the screen.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for the pinch event. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-tapgesture-comp-pinchgestureinterface-i.md) |  |
