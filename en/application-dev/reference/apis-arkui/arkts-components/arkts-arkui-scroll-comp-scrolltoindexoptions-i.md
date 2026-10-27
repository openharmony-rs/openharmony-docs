# ScrollToIndexOptions

```TypeScript
declare interface ScrollToIndexOptions
```

Provides parameters for scrolling to a specific index.

**Since:** 12

<!--Device-unnamed-declare interface ScrollToIndexOptions--><!--Device-unnamed-declare interface ScrollToIndexOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## extraOffset

```TypeScript
extraOffset?: LengthMetrics
```

Extra offset for scrolling to a specified index.

**Type:** LengthMetrics

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ScrollToIndexOptions-extraOffset?: LengthMetrics--><!--Device-ScrollToIndexOptions-extraOffset?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fastScroll

```TypeScript
fastScroll?: FastScrollMode
```

Fast scroll mode for scrolling to a specified index. When set to a value other than NONE, the scroll animation estimates the target position and skips some intermediate items during the animation. This parameter is valid only when the smooth attribute of the scrollToIndex interface is set to true. Default value: FastScrollMode.NONE.

**Type:** [FastScrollMode](arkts-arkui-scroll-comp-fastscrollmode-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ScrollToIndexOptions-fastScroll?: FastScrollMode--><!--Device-ScrollToIndexOptions-fastScroll?: FastScrollMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
