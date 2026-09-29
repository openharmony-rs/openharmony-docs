# SliderInteraction

```TypeScript
declare enum SliderInteraction
```

Interaction mode between the user and the slider.

| Name | Value|Description |  
| ------ | -- | ----------------------------- |  
| SLIDE_AND_CLICK | 0 | Users can drag the slider or touch the track to move the slider. The slider moves as soon as the mouse or finger is pressed.|
| SLIDE_ONLY | 1 | Users are not allowed to move the slider by touching the slider.|
| SLIDE_AND_CLICK_UP | 2 |Users can drag the slider or touch the track to move the slider. The slider moves when the mouse is released or finger is lifted, if the release/lift position coincides with the screen press position.|

**Since:** 12

<!--Device-unnamed-declare enum SliderInteraction--><!--Device-unnamed-declare enum SliderInteraction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_AND_CLICK

```TypeScript
SLIDE_AND_CLICK = 0
```

Users can drag the slider or touch the track to move the slider. The slider moves as soon as the mouse or finger is pressed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderInteraction-SLIDE_AND_CLICK = 0--><!--Device-SliderInteraction-SLIDE_AND_CLICK = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_ONLY

```TypeScript
SLIDE_ONLY = 1
```

Users are not allowed to move the slider by touching the slider.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderInteraction-SLIDE_ONLY = 1--><!--Device-SliderInteraction-SLIDE_ONLY = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_AND_CLICK_UP

```TypeScript
SLIDE_AND_CLICK_UP = 2
```

Users can drag the slider or touch the track to move the slider. The slider moves when the mouse is released or finger is lifted, if the release/lift position coincides with the screen press position.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderInteraction-SLIDE_AND_CLICK_UP = 2--><!--Device-SliderInteraction-SLIDE_AND_CLICK_UP = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
