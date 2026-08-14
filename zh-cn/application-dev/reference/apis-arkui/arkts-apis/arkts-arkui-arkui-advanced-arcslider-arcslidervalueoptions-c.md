# ArcSliderValueOptions

配置弧形Slider的数值信息。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-declare class ArcSliderValueOptions--><!--Device-unnamed-declare class ArcSliderValueOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## constructor

```TypeScript
constructor(options?: ArcSliderValueOptionsConstructorOptions)
```

ArcSliderValueOptions的构造函数。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderValueOptions-constructor(options?: ArcSliderValueOptionsConstructorOptions)--><!--Device-ArcSliderValueOptions-constructor(options?: ArcSliderValueOptionsConstructorOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ArcSliderValueOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptionsconstructoroptions-i.md) | 否 | ArcSliderValueOptions的构造信息。不传入时，ArcSliderValueOptions的各项子属性均取其默认值。 |

## max

```TypeScript
@Trace
  max?: number
```

设置最大值。 默认值：100 **说明：** 当出现异常情况min >= max时，min取默认值0，max取默认值100。 progress不在[min, max]范围之内，取min或者max，靠近min取min，靠近max取max。

**类型：** number

**默认值：** 100

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderValueOptions-@Trace  max?: number--><!--Device-ArcSliderValueOptions-@Trace  max?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## min

```TypeScript
@Trace
  min?: number
```

设置最小值。 默认值：0

**类型：** number

**默认值：** 0

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderValueOptions-@Trace  min?: number--><!--Device-ArcSliderValueOptions-@Trace  min?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## progress

```TypeScript
@Trace
  progress?: number
```

设置当前进度值。 默认值：与参数min的取值一致

**类型：** number

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderValueOptions-@Trace  progress?: number--><!--Device-ArcSliderValueOptions-@Trace  progress?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

