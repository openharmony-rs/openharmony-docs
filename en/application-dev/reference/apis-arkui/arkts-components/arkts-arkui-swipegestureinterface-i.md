# SwipeGestureInterface

**SwipeGesture** is used to trigger a swipe gesture. This gesture is successfully recognized when the swipe speed exceeds the specified threshold, which is 100 vp/s by default.

**Inheritance/Implementation:** SwipeGestureInterface extends GestureInterface<SwipeGestureInterface>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [[Call]]

```TypeScript
(value?: { fingers?: number; direction?: SwipeDirection; speed?: number }): SwipeGestureInterface
```

Sets the parameters for the swipe gesture. Inherits from [GestureInterface&lt;T&gt;](arkts-arkui-gestureinterface-i.md).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { fingers?: number; direction?: SwipeDirection; speed?: number } | No | Parameters for the swipe gesture.<br> - **fingers**: minimum number of fingers to trigger the swipe gesture.<br>Default value: **1** <br>Value range: [1, 10]. <br> - **direction**: direction in which the swipe gesture can be recognized. <br>Default value: **SwipeDirection.All** <br> - **speed**: minimum speed of the swipe gesture.<br>Default value: 100 vp/s<br>Value range: (0, +∞). <br>**NOTE:** <br>If the value is less than or equal to 0, it will be converted to the default value. |

**Return value:**

| Type | Description |
| --- | --- |
| [SwipeGestureInterface](arkts-arkui-swipegestureinterface-i.md) |  |

## [[Call]]

```TypeScript
(options?: SwipeGestureHandlerOptions): SwipeGestureInterface
```

Sets the parameters for the swipe gesture. Compared with SwipeGesture)}, this API adds the **isFingerCountLimited** parameter to **options**, which determines whether to enforce the exact number of fingers touching the screen.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SwipeGestureHandlerOptions](arkts-arkui-swipegesturehandleroptions-i.md) | No | Parameters of the swipe gesture handler. |

**Return value:**

| Type | Description |
| --- | --- |
| [SwipeGestureInterface](arkts-arkui-swipegestureinterface-i.md) |  |

## onAction

```TypeScript
onAction(event: (event: GestureEvent) => void): SwipeGestureInterface
```

Triggered when the swipe gesture is recognized.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for the gesture event. |

**Return value:**

| Type | Description |
| --- | --- |
| [SwipeGestureInterface](arkts-arkui-swipegestureinterface-i.md) |  |
