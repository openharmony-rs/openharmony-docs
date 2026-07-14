# ArcSliderLayoutOptions

配置弧形Slider的布局信息。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## constructor

```TypeScript
constructor(options?: ArcSliderLayoutOptionsConstructorOptions)
```

ArcSliderLayoutOptions的构造函数。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ArcSliderLayoutOptionsConstructorOptions | 否 | ArcSliderLayoutOptions的构造信息。 |

## position

```TypeScript
position?: ArcSliderPosition
```

弧形Slider的屏幕显示位置。

默认值：ArcSliderPosition.RIGHT

**类型：** ArcSliderPosition

**默认值：** ArcSliderPosition.RIGHT

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## reverse

```TypeScript
reverse?: boolean
```

设置弧形Slider取值范围是否反向。值为false时表示从上往下滑。

默认值：true，表示从下往上滑动。

**类型：** boolean

**默认值：** true

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

