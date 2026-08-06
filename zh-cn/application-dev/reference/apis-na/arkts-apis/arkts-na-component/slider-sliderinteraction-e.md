# SliderInteraction

用户与滑动条组件交互方式。 | 名称 | 值 |说明 | | ------ | -- | ----------------------------- | | SLIDE\_AND\_CLICK | 0 | 用户可拖拽滑块或者点击滑轨使滑块移动，鼠标或手指按下即发生移动。| | SLIDE\_ONLY | 1 | 禁止用户通过点击滑轨使滑块移动。| | SLIDE\_AND\_CLICK\_UP | 2 |用户可拖拽滑块或者点击滑轨使滑块移动，当鼠标或手指抬起时，若与屏幕按压位置一致，则触发移动。|

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum SliderInteraction--><!--Device-unnamed-export declare enum SliderInteraction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_AND_CLICK

```TypeScript
SLIDE_AND_CLICK
```

Users can drag the slider or touch the track to move the slider. The slider moves as soon as the mouse or finger is pressed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SliderInteraction-SLIDE_AND_CLICK--><!--Device-SliderInteraction-SLIDE_AND_CLICK-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_ONLY

```TypeScript
SLIDE_ONLY
```

Users are not allowed to move the slider by touching the slider.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SliderInteraction-SLIDE_ONLY--><!--Device-SliderInteraction-SLIDE_ONLY-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_AND_CLICK_UP

```TypeScript
SLIDE_AND_CLICK_UP = 2
```

Users can drag the slider or touch the track to move the slider. The slider moves when the mouse is released or finger is lifted, if the release/lift position coincides with the screen press position.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SliderInteraction-SLIDE_AND_CLICK_UP = 2--><!--Device-SliderInteraction-SLIDE_AND_CLICK_UP = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

