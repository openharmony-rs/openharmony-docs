# SheetTitleBarHoverMode

```TypeScript
declare enum SheetTitleBarHoverMode
```

Enum of title bar hover modes.

**Since:** 26.0.1

<!--Device-unnamed-declare enum SheetTitleBarHoverMode--><!--Device-unnamed-declare enum SheetTitleBarHoverMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 0
```

Standard mode: The title bar and content are arranged vertically without overlapping.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-SheetTitleBarHoverMode-STANDARD = 0--><!--Device-SheetTitleBarHoverMode-STANDARD = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## STACK

```TypeScript
STACK = 1
```

Stack mode: The title bar overlays on top of the content. Developers need to add padding at the top of the content to avoid occlusion.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-SheetTitleBarHoverMode-STACK = 1--><!--Device-SheetTitleBarHoverMode-STACK = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
