# MaxLinesMode

```TypeScript
declare enum MaxLinesMode
```

Enumerates the display effects of the **TextArea** component when text exceeds the maximum number of lines. The default value is **CLIP** (truncating text at the maximum line count).

**Since:** 20

<!--Device-unnamed-declare enum MaxLinesMode--><!--Device-unnamed-declare enum MaxLinesMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CLIP

```TypeScript
CLIP = 0
```

Text is clipped when it exceeds the maximum number of lines.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MaxLinesMode-CLIP = 0--><!--Device-MaxLinesMode-CLIP = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SCROLL

```TypeScript
SCROLL = 1
```

Text can be scrolled when it exceeds the maximum number of lines.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MaxLinesMode-SCROLL = 1--><!--Device-MaxLinesMode-SCROLL = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
