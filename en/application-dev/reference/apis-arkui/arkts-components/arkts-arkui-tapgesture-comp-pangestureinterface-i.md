# PanGestureInterface

```TypeScript
interface PanGestureInterface extends GestureInterface<PanGestureInterface>
```

PanGesture is used to trigger a pan gesture when the movement distance of a finger on the screen reaches the minimum value.

**Inheritance/Implementation:** PanGestureInterface extends GestureInterface<PanGestureInterface>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [[Call]]

```TypeScript
(value?: { fingers?: number; direction?: PanDirection; distance?: number } | PanGestureOptions): PanGestureInterface
```

Creates a pan gesture. Inherits from [GestureInterface&lt;T&gt;](arkts-arkui-tapgesture-comp-gestureinterface-i.md).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { fingers?: number; direction?: PanDirection; distance?: number } &#124; [PanGestureOptions](arkts-arkui-tapgesture-comp-pangestureoptions-c.md) | No | Parameters for the pan gesture. <br> - **fingers**: minimum number of fingers to trigger a pan gesture. The value ranges from 1 to 10. <br>Default value: **1**<br>Value range: [1, 10] <br>**NOTE:** <br>If the value is less than 1 or is not set, the default value is used. <br> - **direction**: pan direction. The value supports the AND (&amp;) and OR (\&#124;) operations. <br>Default value: **PanDirection.All** <br> - **distance**: minimum pan distance to trigger the gesture, in vp.<br>Value range: [0, +∞) <br>Default value: **8** for the stylus and **5** for other input sources. <br>**NOTE:** <br>If a pan gesture and a [tab](../../apis-avsession-kit/arkts-apis/arkts-avsession-avmusictemplate-customelement-i.md#tabs) swipe occur at the same time, set **distance** to **1** to make the gesture more easily recognizable.<br>If the value specified is less than **0**, the default value is used.<br>When the [scale](arkts-arkui-common-comp-commonmethod-c.md#scale) attribute is applied to the component, the actual pan distance is adjusted based on the **scale** ratio. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

<a id="call-1"></a>

## [[Call]]

```TypeScript
(options?: PanGestureHandlerOptions): PanGestureInterface
```

Creates a pan gesture. Compared with PanGesture | PanGestureOptions)}, this API adds the **isFingerCountLimited** and **distanceMap** parameters to **options**, which control whether to enforce the exact number of fingers touching the screen and specify the minimum pan distance required to trigger the gesture for different input sources, respectively.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PanGestureHandlerOptions](arkts-arkui-tapgesture-comp-pangesturehandleroptions-i.md) | No | Parameters of the swipe gesture handler. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

## onActionCancel

```TypeScript
onActionCancel(event: () => void): PanGestureInterface
```

Registers the callback for pan gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful pan gesture recognition. No gesture event information is returned.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback for pan gesture cancellation. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

<a id="onactioncancel-1"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): PanGestureInterface
```

Registers the callback for pan gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful pan gesture recognition. Gesture event information is returned.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback for pan gesture cancellation. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

## onActionEnd

```TypeScript
onActionEnd(event: (event: GestureEvent) => void): PanGestureInterface
```

Registers the callback for pan gesture completion. This callback is triggered when all fingers are lifted after successful pan gesture recognition.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for pan gesture completion. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

## onActionStart

```TypeScript
onActionStart(event: (event: GestureEvent) => void): PanGestureInterface
```

Registers the callback for successful pan gesture recognition.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for successful pan gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

## onActionUpdate

```TypeScript
onActionUpdate(event: (event: GestureEvent) => void): PanGestureInterface
```

Registers the callback for pan gesture updates. If **fingerList** contains multiple fingers, this callback updates the location information of only one finger each time.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for pan gesture updates. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |
