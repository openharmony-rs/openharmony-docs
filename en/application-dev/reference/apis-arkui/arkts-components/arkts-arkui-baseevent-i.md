# BaseEvent

Basic event type.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getModifierKeyState

```TypeScript
getModifierKeyState?(keys: Array<string>): boolean
```

Obtains the pressed status of modifier keys. For details about the error message, see the following error codes. The Ctrl, Alt, and Shift keys are supported.

> **NOTE:** 
> 
> This API is not supported in stylus scenarios.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | Yes | Modifier key list. |

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

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## axisVertical

```TypeScript
axisVertical?: number
```

Vertical axis value.

Default value: **0**

**NOTE:** 

This value is available only when the pan gesture is triggered by mouse wheel scrolling or two-finger touchpad sliding, or when the pinch gesture is triggered by Ctrl + mouse wheel scrolling.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rollAngle

```TypeScript
rollAngle?: number
```

Angle between the stylus and the device's surface.

Unit: deg

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**Widget capability:** This API can be used in ArkTS widgets since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## source

```TypeScript
source: SourceType
```

Type of the event input device.

**Type:** [SourceType](arkts-arkui-sourcetype-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sourceTool

```TypeScript
sourceTool: SourceTool
```

Event input source type.

**Type:** [SourceTool](arkts-arkui-sourcetool-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## target

```TypeScript
target: EventTarget
```

Object that triggers the gesture event.

**Type:** [EventTarget](arkts-arkui-eventtarget-i.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

Timestamp of the event. It is the interval between the time when the event is triggered and the time when the system starts.

Unit: ns

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
