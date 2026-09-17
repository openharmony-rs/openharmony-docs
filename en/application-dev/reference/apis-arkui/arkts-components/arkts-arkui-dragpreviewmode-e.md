# DragPreviewMode

Sets the display mode of the drag preview.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 1
```

Enables the system to automatically change the position of the dragged point based on the scenario and apply scaling transformations to the drag preview based on set rules.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISABLE_SCALE

```TypeScript
DISABLE_SCALE = 2
```

Disables the system's scaling behavior for the drag preview.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_DEFAULT_SHADOW

```TypeScript
ENABLE_DEFAULT_SHADOW = 3
```

Enables the default shadow effect for non-text components.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_DEFAULT_RADIUS

```TypeScript
ENABLE_DEFAULT_RADIUS = 4
```

Enables a unified rounded corner effect for non-text components, with the default value of 12 vp. If the custom rounded corner value set by the application is greater than the default value or the value set by **modifier**, the custom value is used.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_DRAG_ITEM_GRAY_EFFECT

```TypeScript
ENABLE_DRAG_ITEM_GRAY_EFFECT = 5
```

Enables the grayscale effect for the original drag item, which does not apply to text content dragging. When the user starts dragging, the original item displays a grayscale effect. When released, the original item returns to its original appearance. After enabling the default grayscale effect, avoid manually modifying the opacity after dragging starts. Otherwise, the grayscale effect will be overridden, and the original opacity will not be correctly restored when dragging ends.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_MULTI_TILE_EFFECT

```TypeScript
ENABLE_MULTI_TILE_EFFECT = 6
```

Enables multi-tile display for mouse-dragged multi-selected objects, with each drag preview maintaining its original relative position. Requires multi-select mode with **isMultiSelectionEnabled** set to **true**. Takes precedence over [dragPreview](arkts-arkui-commonmethod-c.md#dragpreview). Does not support secondary dragging, rounded corners, or scaling effects.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW

```TypeScript
ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW = 7
```

Enables touch point calculation based on the initial drag preview size. Used when the floating image differs from the drag preview. Incompatible with mouse dragging and **DragPreviewMode.ENABLE_MULTI_TILE_EFFECT**.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
