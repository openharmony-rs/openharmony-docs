# BaseEvent

```TypeScript
declare interface BaseEvent
```

Basic event type.

**Since:** 8

<!--Device-unnamed-declare interface BaseEvent--><!--Device-unnamed-declare interface BaseEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getModifierKeyState

```TypeScript
getModifierKeyState?(keys: Array<string>): boolean
```

Obtains the pressed state of modifier keys. It can be used to determine whether the Ctrl, Alt, and Shift modifier keys are pressed during gesture event handling, so as to process combined-key interaction logic. For error information, see the error codes below. Supported modifier keys: 'Ctrl'|'Alt'|'Shift'.

> **NOTE:** 
> 
> This API is not supported in stylus scenarios.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaseEvent-getModifierKeyState?(keys: Array<string>): boolean--><!--Device-BaseEvent-getModifierKeyState?(keys: Array<string>): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | Yes | List of modifier keys. The array elements support 'Ctrl', 'Alt', and 'Shift', and are used to query whether the specified modifier keys are all pressed. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Pressed status of modifier keys. Returns **true** if all modifier keys are pressed; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. 2. Parameter verification failed. |

## axisHorizontal

```TypeScript
axisHorizontal?: number
```

Horizontal axis value.

Default value: **0**

**NOTE:** 

This value is available only when the pan gesture is triggered by mouse wheel scrolling or two-finger touchpad sliding, or when the pinch gesture is triggered by Ctrl + mouse wheel scrolling.

For the horizontal scrolling scenario triggered by Shift + mouse wheel, axisHorizontal is 0, and the scroll value is reflected in axisVertical.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-BaseEvent-axisHorizontal?: number--><!--Device-BaseEvent-axisHorizontal?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## axisPinch

```TypeScript
axisPinch?: number
```

Two-finger pinch scaling ratio.

Default value: **0**

**NOTE:** 

This value is available only when a pinch gesture is triggered by a two-finger scaling operation on a touchpad or during axis events.

In other scenarios, the default value is returned. The scaling ratio represents the ratio of the current two-finger distance to the initial two-finger distance when first pressed during a pinch gesture.

Value range: [0, +∞).

**Type:** number

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

<!--Device-BaseEvent-axisPinch?: number--><!--Device-BaseEvent-axisPinch?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## axisVertical

```TypeScript
axisVertical?: number
```

Vertical axis value.

Default value: **0**

**NOTE:** 

This value is available only when the pan gesture is triggered by mouse wheel scrolling or two-finger touchpad sliding, or when the pinch gesture is triggered by Ctrl + mouse wheel scrolling.

For the horizontal scrolling scenario triggered by Shift + mouse wheel, the scroll value is reflected in axisVertical.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-BaseEvent-axisVertical?: number--><!--Device-BaseEvent-axisVertical?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## deviceId

```TypeScript
deviceId?: number
```

ID of the input device that triggers the event.

Default value: **0**

Value range: [0, +∞).

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaseEvent-deviceId?: number--><!--Device-BaseEvent-deviceId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pressure

```TypeScript
pressure: number
```

Press pressure.

Default value: **0**

Value range: [0, 1], typical value 0.913168, where higher values indicate greater pressure. On some devices, the return value may be greater than 1 due to different hardware parameter configurations.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BaseEvent-pressure: number--><!--Device-BaseEvent-pressure: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rollAngle

```TypeScript
rollAngle?: number
```

Angle of rotation of the stylus around the long axis of the pen body, similar to the rotation angle when using a screwdriver.

Unit: deg

Value range: [-179, 179], where [0, 179] corresponds to positive angle values [0, 179], and the actual values for the [-179, -1] part are [65357, 65535]. 0 is the hardware reference baseline and does not mean the pen body has no rotation. A positive value indicates clockwise rotation from the baseline direction (that is, from the pen body toward the pen tip, the rotation direction determined by the right-hand rule is clockwise), and a negative value indicates counterclockwise rotation from the baseline direction. When continuous rotation exceeds ±179, the value jumps to the opposite boundary and continues to change.

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**Widget capability:** This API can be used in ArkTS widgets since API version 17.

<!--Device-BaseEvent-rollAngle?: number--><!--Device-BaseEvent-rollAngle?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## source

```TypeScript
source: SourceType
```

Type of the event input device.

**Type:** [SourceType](arkts-arkui-common-comp-sourcetype-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BaseEvent-source: SourceType--><!--Device-BaseEvent-source: SourceType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sourceTool

```TypeScript
sourceTool: SourceTool
```

Event input source type.

**Type:** [SourceTool](arkts-arkui-common-comp-sourcetool-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BaseEvent-sourceTool: SourceTool--><!--Device-BaseEvent-sourceTool: SourceTool-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## target

```TypeScript
target: EventTarget
```

Element object that triggers the gesture event.

**Type:** [EventTarget](arkts-arkui-common-comp-eventtarget-i.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BaseEvent-target: EventTarget--><!--Device-BaseEvent-target: EventTarget-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## targetDisplayId

```TypeScript
targetDisplayId?: number
```

ID of the screen where the event occurs.

Default value: **0**

Value range: [0, +∞).

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-BaseEvent-targetDisplayId?: number--><!--Device-BaseEvent-targetDisplayId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tiltX

```TypeScript
tiltX: number
```

Angle between the projection of the stylus on the device plane and the x-axis.

Unit: deg

Default value: **0**

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BaseEvent-tiltX: number--><!--Device-BaseEvent-tiltX: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tiltY

```TypeScript
tiltY: number
```

Angle between the projection of the stylus on the device plane and the y-axis.

Unit: deg

Default value: **0**

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BaseEvent-tiltY: number--><!--Device-BaseEvent-tiltY: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

Timestamp of the event. It is the interval between the time when the event is triggered and the time when the system starts.

Unit: ns

Value range: [0, +∞).

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BaseEvent-timestamp: number--><!--Device-BaseEvent-timestamp: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
