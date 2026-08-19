# SliderChangeMode

滑块的状态值。包括按下、拖动、离开以及点击滑动条使滑块位置时。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum SliderChangeMode--><!--Device-unnamed-export declare enum SliderChangeMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Begin

```TypeScript
Begin
```

手势/鼠标接触或者按下滑块。 **ArkTS-Dyn起始版本：** 7 **ArkTS-Sta起始版本：** 23

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SliderChangeMode-Begin--><!--Device-SliderChangeMode-Begin-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Moving

```TypeScript
Moving
```

正在拖动滑块过程中。 **ArkTS-Dyn起始版本：** 7 **ArkTS-Sta起始版本：** 23

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SliderChangeMode-Moving--><!--Device-SliderChangeMode-Moving-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## End

```TypeScript
End
```

手势/鼠标离开滑块。 **说明：** 异常值恢复成默认值时触发，即value设置小于min或大于max。 **ArkTS-Dyn起始版本：** 7 **ArkTS-Sta起始版本：** 23

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SliderChangeMode-End--><!--Device-SliderChangeMode-End-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Click

```TypeScript
Click
```

点击滑动条使滑块位置移动。 **ArkTS-Dyn起始版本：** 8 **ArkTS-Sta起始版本：** 23

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SliderChangeMode-Click--><!--Device-SliderChangeMode-Click-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

