# DragResult

```TypeScript
declare enum DragResult
```

Enumerates the results of drag operations and the drop-enabled states of components.

**Since:** 10

<!--Device-unnamed-declare enum DragResult--><!--Device-unnamed-declare enum DragResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DRAG_CANCELED

```TypeScript
DRAG_CANCELED = 2
```

The drag is canceled. This value applies to [onDrop](arkts-arkui-common-comp-commonmethod-c.md#ondrop1).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DragResult-DRAG_CANCELED = 2--><!--Device-DragResult-DRAG_CANCELED = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DRAG_FAILED

```TypeScript
DRAG_FAILED = 1
```

The drag fails. This value applies to [onDrop](arkts-arkui-common-comp-commonmethod-c.md#ondrop1).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DragResult-DRAG_FAILED = 1--><!--Device-DragResult-DRAG_FAILED = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DRAG_SUCCESSFUL

```TypeScript
DRAG_SUCCESSFUL = 0
```

The drag is successful. This value applies to [onDrop](arkts-arkui-common-comp-commonmethod-c.md#ondrop1).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DragResult-DRAG_SUCCESSFUL = 0--><!--Device-DragResult-DRAG_SUCCESSFUL = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DROP_DISABLED

```TypeScript
DROP_DISABLED = 4
```

The component does not allow dropping. This value applies to [onDragEnter](arkts-arkui-common-comp-commonmethod-c.md#ondragenter), [onDragMove](arkts-arkui-common-comp-commonmethod-c.md#ondragmove), and [onDragLeave](arkts-arkui-common-comp-commonmethod-c.md#ondragleave).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DragResult-DROP_DISABLED = 4--><!--Device-DragResult-DROP_DISABLED = 4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DROP_ENABLED

```TypeScript
DROP_ENABLED = 3
```

The component allows dropping. This value applies to [onDragEnter](arkts-arkui-common-comp-commonmethod-c.md#ondragenter), [onDragMove](arkts-arkui-common-comp-commonmethod-c.md#ondragmove), and [onDragLeave](arkts-arkui-common-comp-commonmethod-c.md#ondragleave).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DragResult-DROP_ENABLED = 3--><!--Device-DragResult-DROP_ENABLED = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## UNKNOWN

```TypeScript
UNKNOWN = -1
```

The drag result has not been set. This value applies to [onDragStart](arkts-arkui-common-comp-commonmethod-c.md#ondragstart), [onDragEnter](arkts-arkui-common-comp-commonmethod-c.md#ondragenter), [onDragMove](arkts-arkui-common-comp-commonmethod-c.md#ondragmove), [onDragLeave](arkts-arkui-common-comp-commonmethod-c.md#ondragleave), and [onDrop](arkts-arkui-common-comp-commonmethod-c.md#ondrop1).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-DragResult-UNKNOWN = -1--><!--Device-DragResult-UNKNOWN = -1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
