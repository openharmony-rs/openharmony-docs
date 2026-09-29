# GestureGroupInterface

```TypeScript
interface GestureGroupInterface
```

Combined gestures integrate two or more gestures into a compound gesture, supporting sequential recognition, parallel recognition, and exclusive recognition.

**Since:** 7

<!--Device-unnamed-interface GestureGroupInterface--><!--Device-unnamed-interface GestureGroupInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [[Call]]

```TypeScript
(mode: GestureMode, ...gesture: GestureType[]): GestureGroupInterface
```

Return to Obtain GestureGroup.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GestureGroupInterface-(mode: GestureMode, ...gesture: GestureType[]): GestureGroupInterface--><!--Device-GestureGroupInterface-(mode: GestureMode, ...gesture: GestureType[]): GestureGroupInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [GestureMode](arkts-arkui-tapgesture-comp-gesturemode-e.md) | Yes |  |
| gesture | [GestureType](arkts-arkui-tapgesture-comp-gesturetype-t.md)[] | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [GestureGroupInterface](arkts-arkui-tapgesture-comp-gesturegroupinterface-i.md) |  |

## onCancel

```TypeScript
onCancel(event: () => void): GestureGroupInterface
```

Triggered when a tap cancellation event is received after a gesture is recognized.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GestureGroupInterface-onCancel(event: () => void): GestureGroupInterface--><!--Device-GestureGroupInterface-onCancel(event: () => void): GestureGroupInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback for the gesture event. |

**Return value:**

| Type | Description |
| --- | --- |
| [GestureGroupInterface](arkts-arkui-tapgesture-comp-gesturegroupinterface-i.md) |  |
