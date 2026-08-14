# ArcSliderOptions

配置弧形Slider的信息。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-declare class ArcSliderOptions--><!--Device-unnamed-declare class ArcSliderOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## constructor

```TypeScript
constructor(options?: ArcSliderOptionsConstructorOptions)
```

ArcSliderOptions的构造函数。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptions-constructor(options?: ArcSliderOptionsConstructorOptions)--><!--Device-ArcSliderOptions-constructor(options?: ArcSliderOptionsConstructorOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ArcSliderOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcslideroptionsconstructoroptions-i.md) | 否 | ArcSliderOptions的构造信息。不传入时，ArcSliderOptions的各项子属性均取其默认值。 |

## digitalCrownSensitivity

```TypeScript
@Trace
  digitalCrownSensitivity?: CrownSensitivity
```

设置旋转表冠的灵敏度。 默认值：CrownSensitivity.MEDIUM

**类型：** CrownSensitivity

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptions-@Trace  digitalCrownSensitivity?: CrownSensitivity--><!--Device-ArcSliderOptions-@Trace  digitalCrownSensitivity?: CrownSensitivity-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## layoutOptions

```TypeScript
@Trace
  layoutOptions?: ArcSliderLayoutOptions
```

配置弧形Slider的样式信息。 默认值：[ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md#ArcSliderStyleOptions)的各项子属性均取其默认值。

**类型：** [ArcSliderLayoutOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptions-c.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptions-@Trace  layoutOptions?: ArcSliderLayoutOptions--><!--Device-ArcSliderOptions-@Trace  layoutOptions?: ArcSliderLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onChange

```TypeScript
@Trace
  onChange?: ArcSliderChangeHandler
```

弧形Slider的进度值发生变化时触发回调。 默认值：不传入的情况，无回调。

**类型：** [ArcSliderChangeHandler](arkts-arkui-arcsliderchangehandler-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptions-@Trace  onChange?: ArcSliderChangeHandler--><!--Device-ArcSliderOptions-@Trace  onChange?: ArcSliderChangeHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onEnlarge

```TypeScript
@Trace
  onEnlarge?: ArcSliderEnlargeHandler
```

弧形Slider放大或缩小时触发回调。 默认值：不传入的情况，无回调。

**类型：** [ArcSliderEnlargeHandler](arkts-arkui-arcsliderenlargehandler-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptions-@Trace  onEnlarge?: ArcSliderEnlargeHandler--><!--Device-ArcSliderOptions-@Trace  onEnlarge?: ArcSliderEnlargeHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onTouch

```TypeScript
@Trace
  onTouch?: ArcSliderTouchHandler
```

弧形Slider被触摸时触发回调。 默认值：不传入的情况，无回调。

**类型：** [ArcSliderTouchHandler](arkts-arkui-arcslidertouchhandler-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptions-@Trace  onTouch?: ArcSliderTouchHandler--><!--Device-ArcSliderOptions-@Trace  onTouch?: ArcSliderTouchHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## styleOptions

```TypeScript
@Trace
  styleOptions?: ArcSliderStyleOptions
```

配置弧形Slider的样式信息。 默认值：[ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md#ArcSliderStyleOptions)的各项子属性均取其默认值。

**类型：** [ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptions-@Trace  styleOptions?: ArcSliderStyleOptions--><!--Device-ArcSliderOptions-@Trace  styleOptions?: ArcSliderStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## valueOptions

```TypeScript
@Trace
  valueOptions?: ArcSliderValueOptions
```

配置弧形Slider的样式信息。 默认值：[ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md#ArcSliderStyleOptions)的各项子属性均取其默认值。

**类型：** [ArcSliderValueOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptions-c.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderOptions-@Trace  valueOptions?: ArcSliderValueOptions--><!--Device-ArcSliderOptions-@Trace  valueOptions?: ArcSliderValueOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

