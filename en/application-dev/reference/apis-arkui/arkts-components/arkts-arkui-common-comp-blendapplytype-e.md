# BlendApplyType

```TypeScript
declare enum BlendApplyType
```

Defines how to apply the specified blend mode to the content of a view.

**Since:** 11

<!--Device-unnamed-declare enum BlendApplyType--><!--Device-unnamed-declare enum BlendApplyType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FAST

```TypeScript
FAST = 0
```

The content of the view is blended in sequence on the target image.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-BlendApplyType-FAST = 0--><!--Device-BlendApplyType-FAST = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OFFSCREEN

```TypeScript
OFFSCREEN = 1
```

The content of the component and its child components are drawn on the offscreen canvas, and then blended with the existing content on the canvas.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-BlendApplyType-OFFSCREEN = 1--><!--Device-BlendApplyType-OFFSCREEN = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
