# SwiperContentWillScrollResult

```TypeScript
declare interface SwiperContentWillScrollResult
```

Provides information related to the upcoming scroll action, including the index of the current page, the index of the page that will be displayed in the scroll direction, and the displacement of the scroll action.

**Since:** 15

<!--Device-unnamed-declare interface SwiperContentWillScrollResult--><!--Device-unnamed-declare interface SwiperContentWillScrollResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## comingIndex

```TypeScript
comingIndex: number
```

Index of the page that will be displayed in the scroll direction.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-SwiperContentWillScrollResult-comingIndex: number--><!--Device-SwiperContentWillScrollResult-comingIndex: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## currentIndex

```TypeScript
currentIndex: number
```

Index of the current page. During a finger swipe, this value remains constant as long as the finger is on the screen, even if the page has completely moved out of view.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-SwiperContentWillScrollResult-currentIndex: number--><!--Device-SwiperContentWillScrollResult-currentIndex: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: number
```

Offset of this swipe, with a sign. The positive and negative signs indicate different page turn directions. Unit: vp

A positive value indicates turning from index=1 to index=0, and a negative value indicates turning from index=0 to index=1.

In the finger swipe scenario, this value is the offset passed down in each frame of the swipe event. In the scenarios of scrolling the mouse wheel and using keyboard arrow keys for navigation, this value represents the distance of the upcoming page turn.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-SwiperContentWillScrollResult-offset: number--><!--Device-SwiperContentWillScrollResult-offset: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
