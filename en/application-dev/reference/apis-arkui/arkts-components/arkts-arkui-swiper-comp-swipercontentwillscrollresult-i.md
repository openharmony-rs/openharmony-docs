# SwiperContentWillScrollResult

```TypeScript
declare interface SwiperContentWillScrollResult
```

Provides information related to the upcoming scroll action, including the index of the current page, the index of the page that will be displayed in the scroll direction, and the displacement of the scroll action.

**Since:** 15

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: number
```

Displacement of the scroll action, which is signed to indicate different swipe directions. A positive value indicates a swipe from index=1 to index=0, while a negative value indicates a swipe from index=0 to index=1.

This value represents the offset for each frame during a finger swipe and the distance for page turning when the mouse wheel or keyboard navigation is used.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
