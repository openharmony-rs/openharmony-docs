# DragStartRequestStatus

Enumerates the states defining whether an application can initiate a drag operation. This API is effective only when onDragStart is called.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## WAITING

```TypeScript
WAITING = 0
```

The application is preparing data and cannot initiate a drag operation yet.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## READY

```TypeScript
READY = 1
```

The application has completed data preparation and is ready to initiate a drag operation.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
