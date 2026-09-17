# PreDragStatus

Defines the states before the drag gesture is triggered.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ACTION_DETECTING_STATUS

```TypeScript
ACTION_DETECTING_STATUS = 0
```

A drag gesture is being detected. (Triggered when the component is long pressed for 50 ms.)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## READY_TO_TRIGGER_DRAG_ACTION

```TypeScript
READY_TO_TRIGGER_DRAG_ACTION = 1
```

The component is ready to be dragged. (Triggered when the component is long pressed for 500 ms.)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PREVIEW_LIFT_STARTED

```TypeScript
PREVIEW_LIFT_STARTED = 2
```

A lift animation is started. (Triggered when the component is long pressed for 800 ms.)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PREVIEW_LIFT_FINISHED

```TypeScript
PREVIEW_LIFT_FINISHED = 3
```

A lift animation is finished. (Triggered at the completion of the lift animation.)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PREVIEW_LANDING_STARTED

```TypeScript
PREVIEW_LANDING_STARTED = 4
```

A drop animation is started. (Triggered when the drop animation starts.)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PREVIEW_LANDING_FINISHED

```TypeScript
PREVIEW_LANDING_FINISHED = 5
```

A drop animation is finished. (Triggered when the drop animation ends.)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ACTION_CANCELED_BEFORE_DRAG

```TypeScript
ACTION_CANCELED_BEFORE_DRAG = 6
```

A drop animation is terminated. (Triggered when the finger is lifted off the screen after the component enters the **READY_TO_TRIGGER_DRAG_ACTION** state.)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PREPARING_FOR_DRAG_DETECTION

```TypeScript
PREPARING_FOR_DRAG_DETECTION = 7
```

The component is ready to be dragged. (Triggered when the component is long pressed for 350 ms.)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
