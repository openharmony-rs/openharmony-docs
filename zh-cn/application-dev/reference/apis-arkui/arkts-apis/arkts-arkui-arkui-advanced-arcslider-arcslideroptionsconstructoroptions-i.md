# ArcSliderOptionsConstructorOptions

ArcSliderOptions的构造信息。

**起始版本：** 18

<!--Device-unnamed-interface ArcSliderOptionsConstructorOptions--><!--Device-unnamed-interface ArcSliderOptionsConstructorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcSliderLayoutOptions, ArcSliderValueOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderStyleOptionsConstructorOptions, ArcSlider, ArcSliderLayoutOptionsConstructorOptions, ArcSliderOptions, ArcSliderStyleOptions, ArcSliderPosition, ArcSliderOptionsConstructorOptions } from '@kit.ArkUI';
```

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity?: CrownSensitivity
```

设置旋转表冠的灵敏度。

默认值：CrownSensitivity.MEDIUM

**类型：** CrownSensitivity

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptionsConstructorOptions-digitalCrownSensitivity?: CrownSensitivity--><!--Device-ArcSliderOptionsConstructorOptions-digitalCrownSensitivity?: CrownSensitivity-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## layoutOptions

```TypeScript
layoutOptions?: ArcSliderLayoutOptions
```

配置弧形Slider的样式信息。

默认值：[ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)的各项子属性均取其默认值。

**类型：** ArcSliderLayoutOptions

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptionsConstructorOptions-layoutOptions?: ArcSliderLayoutOptions--><!--Device-ArcSliderOptionsConstructorOptions-layoutOptions?: ArcSliderLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onChange

```TypeScript
onChange?: ArcSliderChangeHandler
```

弧形Slider的进度值发生变化时，告知应用。

默认值：不传入的情况，无回调。

**类型：** ArcSliderChangeHandler

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptionsConstructorOptions-onChange?: ArcSliderChangeHandler--><!--Device-ArcSliderOptionsConstructorOptions-onChange?: ArcSliderChangeHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onEnlarge

```TypeScript
onEnlarge?: ArcSliderEnlargeHandler
```

弧形Slider放大或缩小时，告知应用。

默认值：不传入的情况，无回调。

**类型：** ArcSliderEnlargeHandler

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptionsConstructorOptions-onEnlarge?: ArcSliderEnlargeHandler--><!--Device-ArcSliderOptionsConstructorOptions-onEnlarge?: ArcSliderEnlargeHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onTouch

```TypeScript
onTouch?: ArcSliderTouchHandler
```

弧形Slider被触摸时，告知应用。

默认值：不传入的情况，无回调。

**类型：** ArcSliderTouchHandler

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptionsConstructorOptions-onTouch?: ArcSliderTouchHandler--><!--Device-ArcSliderOptionsConstructorOptions-onTouch?: ArcSliderTouchHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## styleOptions

```TypeScript
styleOptions?: ArcSliderStyleOptions
```

配置弧形Slider的样式信息。

默认值：[ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)的各项子属性均取其默认值。

**类型：** ArcSliderStyleOptions

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptionsConstructorOptions-styleOptions?: ArcSliderStyleOptions--><!--Device-ArcSliderOptionsConstructorOptions-styleOptions?: ArcSliderStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## valueOptions

```TypeScript
valueOptions?: ArcSliderValueOptions
```

配置弧形Slider的样式信息。

默认值：[ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)的各项子属性均取其默认值。

**类型：** ArcSliderValueOptions

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptionsConstructorOptions-valueOptions?: ArcSliderValueOptions--><!--Device-ArcSliderOptionsConstructorOptions-valueOptions?: ArcSliderValueOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

