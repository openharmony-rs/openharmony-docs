# MouseHistoricalPoint

Mouse event historical point information.

Historical points are arranged in chronological order. The first historical point obtained is the earliest event, and the last is the most recent event. The number of historical points depends on the system event queue configuration and hardware performance. Historical points are mainly used for the following scenarios:

1. Smooth drawing: Historical points enable smoother drawing effects, especially when the mouse moves quickly.
2. Gesture recognition: By analyzing the trajectory of historical points, various mouse gestures can be recognized.
3. Performance optimization: Processing multiple historical points in one event callback reduces event processing
frequency and improves performance.
4. Trajectory analysis: Analyzing mouse movement trajectories for drawing applications or gesture control.
5. Data analysis: The **timestamp** in historical points can be used to calculate mouse movement speed.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX: number
```

X coordinate of the mouse pointer relative to the upper-left corner of the entire screen.

Unit: vp

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

Y coordinate of the mouse pointer relative to the upper-left corner of the entire screen.

Unit: vp

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX: number
```

X coordinate of the mouse position in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

Unit: vp

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY: number
```

Y coordinate of the mouse position in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

Unit: vp

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

Timestamp of the mouse event.

Unit: ns

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

X coordinate of the mouse pointer relative to the upper-left corner of the application window.

Unit: vp

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: number
```

Y coordinate of the mouse pointer relative to the upper-left corner of the application window.

Unit: vp

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: number
```

X coordinate of the mouse pointer relative to the upper-left corner of the clicked component.

Unit: vp

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

Y coordinate of the mouse pointer relative to the upper-left corner of the clicked component.

Unit: vp

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
