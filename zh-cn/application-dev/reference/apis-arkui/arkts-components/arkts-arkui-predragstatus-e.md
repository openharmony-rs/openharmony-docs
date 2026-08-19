# PreDragStatus

定义拖拽手势触发前的各阶段状态。

**起始版本：** 12

<!--Device-unnamed-declare enum PreDragStatus--><!--Device-unnamed-declare enum PreDragStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ACTION_DETECTING_STATUS

```TypeScript
ACTION_DETECTING_STATUS = 0
```

拖拽手势启动阶段。(按下50ms时触发)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PreDragStatus-ACTION_DETECTING_STATUS = 0--><!--Device-PreDragStatus-ACTION_DETECTING_STATUS = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## READY_TO_TRIGGER_DRAG_ACTION

```TypeScript
READY_TO_TRIGGER_DRAG_ACTION = 1
```

拖拽准备完成，可发起拖拽阶段。(按下500ms时触发)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PreDragStatus-READY_TO_TRIGGER_DRAG_ACTION = 1--><!--Device-PreDragStatus-READY_TO_TRIGGER_DRAG_ACTION = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PREVIEW_LIFT_STARTED

```TypeScript
PREVIEW_LIFT_STARTED = 2
```

拖拽浮起动效发起阶段。(按下800ms时触发)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PreDragStatus-PREVIEW_LIFT_STARTED = 2--><!--Device-PreDragStatus-PREVIEW_LIFT_STARTED = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PREVIEW_LIFT_FINISHED

```TypeScript
PREVIEW_LIFT_FINISHED = 3
```

拖拽浮起动效结束阶段。(浮起动效完全结束时触发)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PreDragStatus-PREVIEW_LIFT_FINISHED = 3--><!--Device-PreDragStatus-PREVIEW_LIFT_FINISHED = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PREVIEW_LANDING_STARTED

```TypeScript
PREVIEW_LANDING_STARTED = 4
```

拖拽落回动效发起阶段。(落回动效发起时触发)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PreDragStatus-PREVIEW_LANDING_STARTED = 4--><!--Device-PreDragStatus-PREVIEW_LANDING_STARTED = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PREVIEW_LANDING_FINISHED

```TypeScript
PREVIEW_LANDING_FINISHED = 5
```

拖拽落回动效结束阶段。(落回动效结束时触发)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PreDragStatus-PREVIEW_LANDING_FINISHED = 5--><!--Device-PreDragStatus-PREVIEW_LANDING_FINISHED = 5-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ACTION_CANCELED_BEFORE_DRAG

```TypeScript
ACTION_CANCELED_BEFORE_DRAG = 6
```

拖拽浮起落位动效中断。(已满足READY_TO_TRIGGER_DRAG_ACTION状态后，未达到动效阶段，手指抬手时触发)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PreDragStatus-ACTION_CANCELED_BEFORE_DRAG = 6--><!--Device-PreDragStatus-ACTION_CANCELED_BEFORE_DRAG = 6-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PREPARING_FOR_DRAG_DETECTION

```TypeScript
PREPARING_FOR_DRAG_DETECTION = 7
```

拖拽准备完成，可发起拖拽阶段。(按下350ms时触发)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PreDragStatus-PREPARING_FOR_DRAG_DETECTION = 7--><!--Device-PreDragStatus-PREPARING_FOR_DRAG_DETECTION = 7-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

