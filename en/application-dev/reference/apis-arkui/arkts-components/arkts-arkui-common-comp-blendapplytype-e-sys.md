# BlendApplyType

```TypeScript
declare enum BlendApplyType
```

Defines how to apply the specified blend mode to the content of a view.

**Since:** 11

<!--Device-unnamed-declare enum BlendApplyType--><!--Device-unnamed-declare enum BlendApplyType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OFFSCREEN_WITH_BACKGROUND

```TypeScript
OFFSCREEN_WITH_BACKGROUND = 2
```

When an offscreen canvas is created, an initial background canvas is copied first, and then the content of this component and its child components is drawn on the offscreen canvas. The content is then blended on the canvas.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-BlendApplyType-OFFSCREEN_WITH_BACKGROUND = 2--><!--Device-BlendApplyType-OFFSCREEN_WITH_BACKGROUND = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
