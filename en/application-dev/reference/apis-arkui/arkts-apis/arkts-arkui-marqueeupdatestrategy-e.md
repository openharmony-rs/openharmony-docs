# MarqueeUpdateStrategy

```TypeScript
declare enum MarqueeUpdateStrategy
```

Sets the scrolling strategy for the marquee after its attributes are updated.

**Since:** 12

<!--Device-unnamed-declare enum MarqueeUpdateStrategy--><!--Device-unnamed-declare enum MarqueeUpdateStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

After the marquee attributes are updated, the marquee scrolls from the start position.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MarqueeUpdateStrategy-DEFAULT = 0--><!--Device-MarqueeUpdateStrategy-DEFAULT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PRESERVE_POSITION

```TypeScript
PRESERVE_POSITION = 1
```

After the marquee attributes are updated, the marquee scrolls from the current position.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MarqueeUpdateStrategy-PRESERVE_POSITION = 1--><!--Device-MarqueeUpdateStrategy-PRESERVE_POSITION = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
