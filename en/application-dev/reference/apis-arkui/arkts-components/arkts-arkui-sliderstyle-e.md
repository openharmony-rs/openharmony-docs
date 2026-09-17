# SliderStyle

Enumerates the display styles of the slider thumb relative to the track. For details, see [How Are the Slider Thumb and Track of the Slider Component Aligned?](../../../ui/arkts-select-component-faq.md#how-are-the-slider-thumb-and-track-of-the-slider-component-aligned).

> **NOTE:** 
> 
> - By default, the slider has no padding.
> 
> - For horizontal sliders, the default height is 40 vp, the width matches the parent container's width, and the track maintains center alignment. When **SliderStyle.OutSet** is used, it applies 9 vp (half of the [blockSize](arkts-arkui-slider-comp-attribute.md#blocksize) value) margins on both left and right sides. When
> **SliderStyle.InSet** is used, it enforces 6 vp margins on both left and right sides. Custom padding values will be
> applied in addition to these default margins and will not override them.
> 
> - For vertical sliders, the default width is 40 vp, the height matches the parent container's height, and the track maintains center alignment. When **SliderStyle.OutSet** is used, it applies 10 vp margins on both top and bottom sides. When **SliderStyle.InSet** is used, it enforces 6 vp margins on both top and bottom sides. Custom padding values will be applied in addition to these default margins and will not override them.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OutSet

```TypeScript
OutSet
```

The thumb is on the track.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## InSet

```TypeScript
InSet
```

The thumb is in the track.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE
```

There is no thumb.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
