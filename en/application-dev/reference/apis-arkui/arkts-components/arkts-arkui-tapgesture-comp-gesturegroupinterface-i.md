# GestureGroupInterface

```TypeScript
interface GestureGroupInterface
```

Combined gestures integrate two or more gestures into a compound gesture, supporting sequential recognition, parallel recognition, and exclusive recognition. They are suitable for scenarios where multiple basic gestures need to be combined on the same component and their recognition order, parallel relationship, or exclusive relationship needs to be controlled, helping developers implement more complex gesture interaction logic.

**Since:** 7

<!--Device-unnamed-interface GestureGroupInterface--><!--Device-unnamed-interface GestureGroupInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [[Call]]

```TypeScript
(mode: GestureMode, ...gesture: GestureType[]): GestureGroupInterface
```

Creates a combined gesture.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GestureGroupInterface-(mode: GestureMode, ...gesture: GestureType[]): GestureGroupInterface--><!--Device-GestureGroupInterface-(mode: GestureMode, ...gesture: GestureType[]): GestureGroupInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [GestureMode](arkts-arkui-tapgesture-comp-gesturemode-e.md) | Yes | Gesture group recognition mode. If the recognition mode is not explicitly set, **GestureMode.Sequence** is used by default. |
| gesture | [GestureType](arkts-arkui-tapgesture-comp-gesturetype-t.md)[] | Yes | When two or more basic gesture types are set, these gestures are recognized as a gesture group. If this parameter is not set, the gesture group recognition function does not take effect. <br>**NOTE:** <br>When you need to add both a single-tap gesture and a double-tap gesture to a component, you can add two [TapGesture](arkts-arkui-gesturecontrol-n.md#tapgesture) gestures in the gesture group. The double-tap gesture must be placed before the single-tap gesture; otherwise, the gestures do not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [GestureGroupInterface](arkts-arkui-tapgesture-comp-gesturegroupinterface-i.md) |  |

## onCancel

```TypeScript
onCancel(event: () => void): GestureGroupInterface
```

Invoked when a touch cancel event is received after gesture recognition.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GestureGroupInterface-onCancel(event: () => void): GestureGroupInterface--><!--Device-GestureGroupInterface-onCancel(event: () => void): GestureGroupInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback for the gesture event, invoked when a touch cancel event is received after combined gesture recognition succeeds. The callback has no parameters and no return value. |

**Return value:**

| Type | Description |
| --- | --- |
| [GestureGroupInterface](arkts-arkui-tapgesture-comp-gesturegroupinterface-i.md) |  |
