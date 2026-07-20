# ArcSliderOptions

配置弧形Slider的信息。

**起始版本：** 18

**装饰器类型：** @ObservedV2

<!--Device-unnamed-declare class ArcSliderOptions--><!--Device-unnamed-declare class ArcSliderOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcSliderLayoutOptions, ArcSliderValueOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderStyleOptionsConstructorOptions, ArcSlider, ArcSliderLayoutOptionsConstructorOptions, ArcSliderOptions, ArcSliderStyleOptions, ArcSliderPosition, ArcSliderOptionsConstructorOptions } from '@kit.ArkUI';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(options?: ArcSliderOptionsConstructorOptions)
```

ArcSliderOptions的构造函数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptions-constructor(options?: ArcSliderOptionsConstructorOptions)--><!--Device-ArcSliderOptions-constructor(options?: ArcSliderOptionsConstructorOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ArcSliderOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcslideroptionsconstructoroptions-i.md) | 否 | ArcSliderOptions的构造信息。 |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity?: CrownSensitivity
```

设置旋转表冠的灵敏度。

默认值：CrownSensitivity.MEDIUM

**类型：** CrownSensitivity

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptions-digitalCrownSensitivity?: CrownSensitivity--><!--Device-ArcSliderOptions-digitalCrownSensitivity?: CrownSensitivity-End-->

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

<!--Device-ArcSliderOptions-layoutOptions?: ArcSliderLayoutOptions--><!--Device-ArcSliderOptions-layoutOptions?: ArcSliderLayoutOptions-End-->

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

<!--Device-ArcSliderOptions-onChange?: ArcSliderChangeHandler--><!--Device-ArcSliderOptions-onChange?: ArcSliderChangeHandler-End-->

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

<!--Device-ArcSliderOptions-onEnlarge?: ArcSliderEnlargeHandler--><!--Device-ArcSliderOptions-onEnlarge?: ArcSliderEnlargeHandler-End-->

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

<!--Device-ArcSliderOptions-onTouch?: ArcSliderTouchHandler--><!--Device-ArcSliderOptions-onTouch?: ArcSliderTouchHandler-End-->

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

<!--Device-ArcSliderOptions-styleOptions?: ArcSliderStyleOptions--><!--Device-ArcSliderOptions-styleOptions?: ArcSliderStyleOptions-End-->

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

<!--Device-ArcSliderOptions-valueOptions?: ArcSliderValueOptions--><!--Device-ArcSliderOptions-valueOptions?: ArcSliderValueOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

