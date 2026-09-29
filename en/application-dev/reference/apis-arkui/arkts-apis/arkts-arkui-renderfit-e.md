# RenderFit

```TypeScript
declare enum RenderFit
```

Enumerates the modes in which the final state of the component's content is rendered during its width and height animation process.

> **NOTE:** 
> 
> - In the illustrative diagrams, the blue area indicates the content, and the orange area indicates the component content box.
> 
> - Different render fit modes create different effects during the width and height animation process. Choose the one that best fits your need.

**Since:** 10

<!--Device-unnamed-declare enum RenderFit--><!--Device-unnamed-declare enum RenderFit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CENTER

```TypeScript
CENTER = 0
```

The component's content stays at the final size and is always aligned with the center of the component.![renderfit_center](../../../reference/apis-arkui/arkui-ts/figures/renderfit_center.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-CENTER = 0--><!--Device-RenderFit-CENTER = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TOP

```TypeScript
TOP = 1
```

The component's content stays at the final size and is always aligned with the top center of the component.![renderfit_top](../../../reference/apis-arkui/arkui-ts/figures/renderfit_top.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-TOP = 1--><!--Device-RenderFit-TOP = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM

```TypeScript
BOTTOM = 2
```

The component's content stays at the final size and is always aligned with the bottom center of the component.![renderfit_bottom](../../../reference/apis-arkui/arkui-ts/figures/renderfit_bottom.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-BOTTOM = 2--><!--Device-RenderFit-BOTTOM = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LEFT

```TypeScript
LEFT = 3
```

The component's content stays at the final size and is always aligned with the left of the component.![renderfit_left](../../../reference/apis-arkui/arkui-ts/figures/renderfit_left.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-LEFT = 3--><!--Device-RenderFit-LEFT = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RIGHT

```TypeScript
RIGHT = 4
```

The component's content stays at the final size and is always aligned with the right of the component.![renderfit_right](../../../reference/apis-arkui/arkui-ts/figures/renderfit_right.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-RIGHT = 4--><!--Device-RenderFit-RIGHT = 4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TOP_LEFT

```TypeScript
TOP_LEFT = 5
```

The component's content stays at the final size and is always aligned with the upper left corner of the component.![renderfit_top_left](../../../reference/apis-arkui/arkui-ts/figures/renderfit_top_left.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-TOP_LEFT = 5--><!--Device-RenderFit-TOP_LEFT = 5-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TOP_RIGHT

```TypeScript
TOP_RIGHT = 6
```

The component's content stays at the final size and is always aligned with the upper right corner of the component.![renderfit_top_right](../../../reference/apis-arkui/arkui-ts/figures/renderfit_top_right.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-TOP_RIGHT = 6--><!--Device-RenderFit-TOP_RIGHT = 6-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM_LEFT

```TypeScript
BOTTOM_LEFT = 7
```

The component's content stays at the final size and is always aligned with the lower left corner of the component.![renderfit_bottom_left](../../../reference/apis-arkui/arkui-ts/figures/renderfit_bottom_left.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-BOTTOM_LEFT = 7--><!--Device-RenderFit-BOTTOM_LEFT = 7-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM_RIGHT

```TypeScript
BOTTOM_RIGHT = 8
```

The component's content stays at the final size and is always aligned with the lower right corner of the component.![renderfit_bottom_right](../../../reference/apis-arkui/arkui-ts/figures/renderfit_bottom_right.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-BOTTOM_RIGHT = 8--><!--Device-RenderFit-BOTTOM_RIGHT = 8-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_FILL

```TypeScript
RESIZE_FILL = 9
```

The component's content is always resized to fill the component's content box, without considering its aspect ratio in the final state.![renderfit_resize_fill](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_fill.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-RESIZE_FILL = 9--><!--Device-RenderFit-RESIZE_FILL = 9-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_CONTAIN

```TypeScript
RESIZE_CONTAIN = 10
```

While maintaining its aspect ratio in the final state, the component's content is scaled to fit within the component's content box. It is always aligned with the center of the component.![renderfit_resize_contain](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_contain.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-RESIZE_CONTAIN = 10--><!--Device-RenderFit-RESIZE_CONTAIN = 10-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_CONTAIN_TOP_LEFT

```TypeScript
RESIZE_CONTAIN_TOP_LEFT = 11
```

While maintaining its aspect ratio in the final state, the component's content is scaled to fit within the component's content box. When there is remaining space in the width direction of the component, the content is left -aligned with the component. When there is remaining space in the height direction of the component, the content is top-aligned with the component.![renderfit_resize_contain_top_left](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_contain_top_left.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-RESIZE_CONTAIN_TOP_LEFT = 11--><!--Device-RenderFit-RESIZE_CONTAIN_TOP_LEFT = 11-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_CONTAIN_BOTTOM_RIGHT

```TypeScript
RESIZE_CONTAIN_BOTTOM_RIGHT = 12
```

While maintaining its aspect ratio in the final state, the component's content is scaled to fit within the component's content box. When there is remaining space in the width direction of the component, the content is right-aligned with the component. When there is remaining space in the height direction of the component, the content is bottom-aligned with the component.![renderfit_resize_contain_bottom_right](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_contain_bottom_right.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-RESIZE_CONTAIN_BOTTOM_RIGHT = 12--><!--Device-RenderFit-RESIZE_CONTAIN_BOTTOM_RIGHT = 12-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_COVER

```TypeScript
RESIZE_COVER = 13
```

While maintaining its aspect ratio in the final state, the component's content is scaled to cover the component's entire content box. It is always aligned with the center of the component, so that its middle part is displayed.![renderfit_resize_cover](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_cover.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-RESIZE_COVER = 13--><!--Device-RenderFit-RESIZE_COVER = 13-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_COVER_TOP_LEFT

```TypeScript
RESIZE_COVER_TOP_LEFT = 14
```

While maintaining its aspect ratio in the final state, the component's content is scaled to cover the component's entire content box. When there is remaining space in the width direction, the content is left-aligned with the component, so that its left part is displayed. When there is remaining space in the height direction, the content is top-aligned with the component, so that its top part is displayed.![renderfit_resize_cover_top_left](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_cover_top_left.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-RESIZE_COVER_TOP_LEFT = 14--><!--Device-RenderFit-RESIZE_COVER_TOP_LEFT = 14-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_COVER_BOTTOM_RIGHT

```TypeScript
RESIZE_COVER_BOTTOM_RIGHT = 15
```

While maintaining its aspect ratio in the final state, the component's content is scaled to cover the component's entire content box. When there is remaining space in the width direction, the content is right-aligned with the component, so that its right part is displayed. When there is remaining space in the height direction, the content is bottom-aligned with the component, so that its bottom part is displayed.![renderfit_resize_cover_bottom_right](../../../reference/apis-arkui/arkui-ts/figures/renderfit_resize_cover_bottom_right.png)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RenderFit-RESIZE_COVER_BOTTOM_RIGHT = 15--><!--Device-RenderFit-RESIZE_COVER_BOTTOM_RIGHT = 15-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
