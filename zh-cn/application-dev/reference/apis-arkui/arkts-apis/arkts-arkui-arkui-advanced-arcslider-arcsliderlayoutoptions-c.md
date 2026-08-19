# ArcSliderLayoutOptions

配置弧形Slider的布局信息。

**起始版本：** 18

<!--Device-unnamed-declare class ArcSliderLayoutOptions--><!--Device-unnamed-declare class ArcSliderLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ArcSliderLayoutOptionsConstructorOptions)
```

ArcSliderLayoutOptions的构造函数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderLayoutOptions-constructor(options?: ArcSliderLayoutOptionsConstructorOptions)--><!--Device-ArcSliderLayoutOptions-constructor(options?: ArcSliderLayoutOptionsConstructorOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ArcSliderLayoutOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptionsconstructoroptions-i.md) | 否 | ArcSliderLayoutOptions的构造信息。不传入时，ArcSliderLayoutOptions的各项子属性均取其默认值。 |

## position

```TypeScript
@Trace
  position?: ArcSliderPosition
```

弧形Slider的屏幕显示位置。 默认值：ArcSliderPosition.RIGHT

**类型：** [ArcSliderPosition](arkts-arkui-arkui-advanced-arcslider-arcsliderposition-e.md)

**默认值：** ArcSliderPosition.RIGHT

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderLayoutOptions-@Trace  position?: ArcSliderPosition--><!--Device-ArcSliderLayoutOptions-@Trace  position?: ArcSliderPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## reverse

```TypeScript
@Trace
  reverse?: boolean
```

设置弧形Slider的滑动方向。值为false时表示从上往下滑。 默认值：true，表示从下往上滑动。

**类型：** boolean

**默认值：** true

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderLayoutOptions-@Trace  reverse?: boolean--><!--Device-ArcSliderLayoutOptions-@Trace  reverse?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

