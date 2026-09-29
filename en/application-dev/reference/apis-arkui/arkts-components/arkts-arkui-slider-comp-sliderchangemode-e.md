# SliderChangeMode

```TypeScript
declare enum SliderChangeMode
```

Enumerates the slider states, including pressed, dragged, released, and moved when the slider is tapped.

**Since:** 7

<!--Device-unnamed-declare enum SliderChangeMode--><!--Device-unnamed-declare enum SliderChangeMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Begin

```TypeScript
Begin
```

The user touches or clicks the thumb.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SliderChangeMode-Begin--><!--Device-SliderChangeMode-Begin-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Moving

```TypeScript
Moving
```

The user is dragging the slider.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SliderChangeMode-Moving--><!--Device-SliderChangeMode-Moving-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## End

```TypeScript
End
```

The user releases the slider by a gesture or mouse.

**Note:** 

This state is triggered when the user releases the slider by a gesture or mouse, including the end of a normal drag. It is also triggered when an invalid value is restored to the default value, that is, when the value is set to a value less than **min** or greater than **max**.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SliderChangeMode-End--><!--Device-SliderChangeMode-End-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Click

```TypeScript
Click
```

The user moves the thumb by clicking the track.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SliderChangeMode-Click--><!--Device-SliderChangeMode-Click-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
