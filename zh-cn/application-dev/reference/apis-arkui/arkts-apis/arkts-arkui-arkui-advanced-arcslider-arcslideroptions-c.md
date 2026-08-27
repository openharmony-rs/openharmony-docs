# ArcSliderOptions

配置弧形Slider的信息。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ArcSliderOptionsConstructorOptions)
```

ArcSliderOptions的构造函数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ArcSliderOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcslideroptionsconstructoroptions-i.md) | 否 | ArcSliderOptions的构造信息。不传入时，ArcSliderOptions的各项子属性均取其默认值。 |

## onChange

```TypeScript
onChange?: ArcSliderChangeHandler
```

弧形Slider的进度值发生变化时触发回调。默认值：不传入的情况，无回调。@Trace

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onEnlarge

```TypeScript
onEnlarge?: ArcSliderEnlargeHandler
```

弧形Slider放大或缩小时触发回调。默认值：不传入的情况，无回调。@Trace

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onTouch

```TypeScript
onTouch?: ArcSliderTouchHandler
```

弧形Slider被触摸时触发回调。默认值：不传入的情况，无回调。@Trace

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity?: CrownSensitivity
```

设置旋转表冠的灵敏度。默认值：CrownSensitivity.MEDIUM@Trace

**类型：** [CrownSensitivity](arkts-arkui-crownsensitivity-e.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## layoutOptions

```TypeScript
layoutOptions?: ArcSliderLayoutOptions
```

配置弧形Slider的样式信息。默认值：[ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)的各项子属性均取其默认值。@Trace

**类型：** [ArcSliderLayoutOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptions-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## styleOptions

```TypeScript
styleOptions?: ArcSliderStyleOptions
```

配置弧形Slider的样式信息。默认值：[ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)的各项子属性均取其默认值。@Trace

**类型：** [ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## valueOptions

```TypeScript
valueOptions?: ArcSliderValueOptions
```

配置弧形Slider的样式信息。默认值：[ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)的各项子属性均取其默认值。@Trace

**类型：** [ArcSliderValueOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptions-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle
