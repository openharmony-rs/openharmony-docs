# ArcSliderValueOptions

配置弧形Slider的数值信息。

**起始版本：** 18

<!--Device-unnamed-declare class ArcSliderValueOptions--><!--Device-unnamed-declare class ArcSliderValueOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcSliderLayoutOptions, ArcSliderValueOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderStyleOptionsConstructorOptions, ArcSlider, ArcSliderLayoutOptionsConstructorOptions, ArcSliderOptions, ArcSliderStyleOptions, ArcSliderPosition, ArcSliderOptionsConstructorOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ArcSliderValueOptionsConstructorOptions)
```

ArcSliderValueOptions的构造函数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderValueOptions-constructor(options?: ArcSliderValueOptionsConstructorOptions)--><!--Device-ArcSliderValueOptions-constructor(options?: ArcSliderValueOptionsConstructorOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ArcSliderValueOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptionsconstructoroptions-i.md) | 否 | ArcSliderValueOptions的构造信息。 |

## max

```TypeScript
max?: number
```

设置最大值。

默认值：100

**说明：**

当出现异常情况min >= max时，min取默认值0，max取默认值100。

progress不在[min, max]范围之内，取min或者max，靠近min取min，靠近max取max。

**类型：** number

**默认值：** 100

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderValueOptions-max?: number--><!--Device-ArcSliderValueOptions-max?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## min

```TypeScript
min?: number
```

设置最小值。

默认值：0

**类型：** number

**默认值：** 0

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderValueOptions-min?: number--><!--Device-ArcSliderValueOptions-min?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## progress

```TypeScript
progress?: number
```

设置当前进度值。

默认值：与参数min的取值一致

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderValueOptions-progress?: number--><!--Device-ArcSliderValueOptions-progress?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

