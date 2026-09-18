# AdaptiveColor

Enumerates the adaptive color modes used for the background blur effect.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Adaptive color mode is not used. The default color is used as the mask color. Using a mode other than **DEFAULT** can be more time-consuming.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AVERAGE

```TypeScript
AVERAGE = 1
```

Adaptive color mode is used. The average color value of the color picking area is used as the mask color.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
