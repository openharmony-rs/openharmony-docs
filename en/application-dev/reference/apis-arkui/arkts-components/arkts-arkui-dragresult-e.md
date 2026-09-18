# DragResult

Defines the result of a drag operation and the drop-selection state of a component.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## UNKNOWN

```TypeScript
UNKNOWN = -1
```

If the drag is not finished and the result is not set by receiver, return DragResult.UNKNOWN.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DRAG_SUCCESSFUL

```TypeScript
DRAG_SUCCESSFUL = 0
```

The drag is successful. This value applies to [onDrop](arkts-arkui-commonmethod-c.md#ondrop).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DRAG_FAILED

```TypeScript
DRAG_FAILED = 1
```

The drag fails. This value applies to [onDrop](arkts-arkui-commonmethod-c.md#ondrop).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DRAG_CANCELED

```TypeScript
DRAG_CANCELED = 2
```

The drag is canceled. This value applies to [onDrop](arkts-arkui-commonmethod-c.md#ondrop).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DROP_ENABLED

```TypeScript
DROP_ENABLED = 3
```

The component allows dropping. This value applies to [onDragEnter](arkts-arkui-commonmethod-c.md#ondragenter), [onDragMove](arkts-arkui-commonmethod-c.md#ondragmove), and [onDragLeave](arkts-arkui-commonmethod-c.md#ondragleave).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DROP_DISABLED

```TypeScript
DROP_DISABLED = 4
```

The component does not allow dropping. This value applies to [onDragEnter](arkts-arkui-commonmethod-c.md#ondragenter), [onDragMove](arkts-arkui-commonmethod-c.md#ondragmove), and [onDragLeave](arkts-arkui-commonmethod-c.md#ondragleave).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
