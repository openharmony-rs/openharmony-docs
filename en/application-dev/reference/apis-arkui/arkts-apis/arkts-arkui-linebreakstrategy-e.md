# LineBreakStrategy

```TypeScript
declare enum LineBreakStrategy
```

Sets the line break rule.

**Since:** 12

<!--Device-unnamed-declare enum LineBreakStrategy--><!--Device-unnamed-declare enum LineBreakStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## GREEDY

```TypeScript
GREEDY = 0
```

Places as many words on a line as possible and moves to the next line only if no more words can fit into the same line.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LineBreakStrategy-GREEDY = 0--><!--Device-LineBreakStrategy-GREEDY = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## HIGH_QUALITY

```TypeScript
HIGH_QUALITY = 1
```

Fills in lines as much as possible on the basis of **BALANCED**, which may result in a large blank area on the last line.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LineBreakStrategy-HIGH_QUALITY = 1--><!--Device-LineBreakStrategy-HIGH_QUALITY = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BALANCED

```TypeScript
BALANCED = 2
```

Without splitting words, the width of each line in a paragraph is the same as much as possible.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LineBreakStrategy-BALANCED = 2--><!--Device-LineBreakStrategy-BALANCED = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
