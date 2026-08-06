# ArcSliderLayoutOptions

配置弧形Slider的布局信息。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @ObservedV2

<!--Device-unnamed-declare class ArcSliderLayoutOptions--><!--Device-unnamed-declare class ArcSliderLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## constructor

```TypeScript
constructor(options?: ArcSliderLayoutOptionsConstructorOptions)
```

ArcSliderLayoutOptions的构造函数。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderLayoutOptions-constructor(options?: ArcSliderLayoutOptionsConstructorOptions)--><!--Device-ArcSliderLayoutOptions-constructor(options?: ArcSliderLayoutOptionsConstructorOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | ArcSliderLayoutOptions的构造信息。不传入时，ArcSliderLayoutOptions的各项子属性均取其默认值。 |

## position

```TypeScript
position?: ArcSliderPosition
```

弧形Slider的屏幕显示位置。 默认值：ArcSliderPosition.RIGHT

**类型：** ArcSliderPosition

**默认值：** ArcSliderPosition.RIGHT

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderLayoutOptions-position?: ArcSliderPosition--><!--Device-ArcSliderLayoutOptions-position?: ArcSliderPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## reverse

```TypeScript
reverse?: boolean
```

设置弧形Slider的滑动方向。值为false时表示从上往下滑。 默认值：true，表示从下往上滑动。

**类型：** boolean

**默认值：** true

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSliderLayoutOptions-reverse?: boolean--><!--Device-ArcSliderLayoutOptions-reverse?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

