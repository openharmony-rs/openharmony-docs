# DraggingSizeChangeEffect

Enumerates the transition effects for switching between the floating image (set through [bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu)) and the drag preview when both are configured on a component.

**Since:** 19

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Direct transition from the menu preview to the final drag preview image upon drag initiation.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SIZE_TRANSITION

```TypeScript
SIZE_TRANSITION = 1
```

Smooth size transition from the menu preview to the final drag preview. Disabled when **DISABLE_SCALE** is set in [DragPreviewMode](arkts-arkui-dragpreviewmode-e.md). Used when the floating preview matches the drag preview.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SIZE_CONTENT_TRANSITION

```TypeScript
SIZE_CONTENT_TRANSITION = 2
```

Gradual transition from the menu preview to the final drag preview with opacity and size animations. Disabled when **DISABLE_SCALE** is set in [DragPreviewMode](arkts-arkui-dragpreviewmode-e.md). Suitable for significant visual differences between preview images.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
