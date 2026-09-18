# DragBehavior

Describes the drag behavior. When [DragResult](arkts-arkui-dragresult-e.md) is set to **DROP_ENABLED**, you can define **DragBehavior** as either **COPY** or **MOVE**. When **DragBehavior** is set to **COPY**, a plus sign will be displayed in the badge of the dragged object. When **DragBehavior** is set to **MOVE**, the plus sign will not be displayed. **DragBehavior** is used to indicate the intended way of handling data (either copy or move) without governing the actual data processing. This behavior is reported back to the drag source through **onDragEnd**, enabling the drag initiator to distinguish whether the operation results in a copy or a move of the data.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COPY

```TypeScript
COPY = 0
```

The data is handled as a copy operation.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MOVE

```TypeScript
MOVE = 1
```

The data is handled as a move operation, effectively cutting it from its original location.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
