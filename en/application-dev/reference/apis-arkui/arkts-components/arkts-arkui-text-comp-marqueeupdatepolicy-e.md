# MarqueeUpdatePolicy

```TypeScript
declare enum MarqueeUpdatePolicy
```

Sets the scrolling policy of the marquee after its attributes are updated.

**Since:** 23

<!--Device-unnamed-declare enum MarqueeUpdatePolicy--><!--Device-unnamed-declare enum MarqueeUpdatePolicy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Restarts the marquee from the start position after the attributes of the marquee component are updated.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-MarqueeUpdatePolicy-DEFAULT = 0--><!--Device-MarqueeUpdatePolicy-DEFAULT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PRESERVE_POSITION

```TypeScript
PRESERVE_POSITION = 1
```

Resumes the marquee from the current position after the attributes of the marquee component are updated.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-MarqueeUpdatePolicy-PRESERVE_POSITION = 1--><!--Device-MarqueeUpdatePolicy-PRESERVE_POSITION = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
