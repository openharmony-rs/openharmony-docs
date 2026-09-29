# PageFlipMode

```TypeScript
declare enum PageFlipMode
```

Enumerates the modes for flipping pages using the mouse wheel.

**Since:** 15

<!--Device-unnamed-declare enum PageFlipMode--><!--Device-unnamed-declare enum PageFlipMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONTINUOUS

```TypeScript
CONTINUOUS = 0
```

Continuous page flipping mode where multiple pages are turned continuously when the user scrolls the mouse wheel without interruption.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-PageFlipMode-CONTINUOUS = 0--><!--Device-PageFlipMode-CONTINUOUS = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SINGLE

```TypeScript
SINGLE = 1
```

Single-page flipping mode where the mouse wheel event is ignored until the current page flipping animation is complete.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-PageFlipMode-SINGLE = 1--><!--Device-PageFlipMode-SINGLE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
