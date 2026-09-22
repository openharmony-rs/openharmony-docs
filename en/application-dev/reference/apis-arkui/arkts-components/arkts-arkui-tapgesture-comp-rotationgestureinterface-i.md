# RotationGestureInterface

```TypeScript
interface RotationGestureInterface extends GestureInterface<RotationGestureInterface>
```

**RotationGesture** is used to trigger a rotation gesture, which recognizes rotational movements using two to five fingers, with a minimum angular change of 1 degree. This gesture cannot be triggered using a two-finger rotation operation on a trackpad.

**Inheritance/Implementation:** RotationGestureInterface extends GestureInterface<RotationGestureInterface>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [[Call]]

```TypeScript
(value?: { fingers?: number; angle?: number }): RotationGestureInterface
```

Sets the parameters for the rotation gesture. Inherits from [GestureInterface&lt;T&gt;](arkts-arkui-tapgesture-comp-gestureinterface-i.md).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { fingers?: number; angle?: number } | No | Parameters for the rotation gesture.<br> - **fingers**: minimum number of fingers to trigger the rotation gesture.<br>Default value: **2** <br>Value range: [2, 5]. Values less than 2 or greater than 5 are automatically adjusted to the default value. <br>While more fingers than the minimum number can be pressed to trigger the gesture, only the first two fingers participate in gesture calculation. <br> - **angle**: minimum angular change required to trigger the rotation gesture; unit: deg.<br>Default value: **1**<br>**NOTE:** <br>If the value is less than or equal to 0 or greater than 360, it will be converted to the default value. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureInterface](arkts-arkui-tapgesture-comp-rotationgestureinterface-i.md) |  |

<a id="call-1"></a>

## [[Call]]

```TypeScript
(options?: RotationGestureHandlerOptions): RotationGestureInterface
```

Sets the parameters for the rotation gesture. Compared with RotationGesture)}, this API adds the **isFingerCountLimited** parameter to **options**, which determines whether to enforce the exact number of fingers touching the screen.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RotationGestureHandlerOptions](arkts-arkui-tapgesture-comp-rotationgesturehandleroptions-i.md) | No | Parameters of the rotation gesture handler. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureInterface](arkts-arkui-tapgesture-comp-rotationgestureinterface-i.md) |  |

## onActionCancel

```TypeScript
onActionCancel(event: () => void): RotationGestureInterface
```

Triggered when a tap cancellation event is received after the rotation gesture is recognized. This callback does not return gesture event information.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback for the gesture event. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureInterface](arkts-arkui-tapgesture-comp-rotationgestureinterface-i.md) |  |

<a id="onactioncancel-1"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): RotationGestureInterface
```

Triggered when a tap cancellation event is received after the rotation gesture is recognized. Compared with [onActionCancel](#onactioncancel), this callback returns gesture event information.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback for the gesture event. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureInterface](arkts-arkui-tapgesture-comp-rotationgestureinterface-i.md) |  |

## onActionEnd

```TypeScript
onActionEnd(event: (event: GestureEvent) => void): RotationGestureInterface
```

Triggered when the last finger used for the rotation gesture is lifted.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for the gesture event. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureInterface](arkts-arkui-tapgesture-comp-rotationgestureinterface-i.md) |  |

## onActionStart

```TypeScript
onActionStart(event: (event: GestureEvent) => void): RotationGestureInterface
```

Triggered when the rotation gesture is recognized successfully.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for the gesture event. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureInterface](arkts-arkui-tapgesture-comp-rotationgestureinterface-i.md) |  |

## onActionUpdate

```TypeScript
onActionUpdate(event: (event: GestureEvent) => void): RotationGestureInterface
```

Triggered during the movement of the rotation gesture.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for the gesture event. |

**Return value:**

| Type | Description |
| --- | --- |
| [RotationGestureInterface](arkts-arkui-tapgesture-comp-rotationgestureinterface-i.md) |  |
