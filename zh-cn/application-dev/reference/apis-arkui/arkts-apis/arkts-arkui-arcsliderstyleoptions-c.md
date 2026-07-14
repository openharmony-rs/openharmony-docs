# ArcSliderStyleOptions

配置弧形Slider的样式信息。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## constructor

```TypeScript
constructor(options?: ArcSliderStyleOptionsConstructorOptions)
```

ArcSliderStyleOptions的构造函数。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ArcSliderStyleOptionsConstructorOptions | 否 | ArcSliderStyleOptions的构造信息。 |

## activeTrackThickness

```TypeScript
activeTrackThickness?: number
```

放大状态下弧形Slider的描边粗细，单位：vp。

默认值：24

取值范围：[24, 36]，异常值按默认值处理。

**类型：** number

**默认值：** 24

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## selectedColor

```TypeScript
selectedColor?: string
```

设置描边高亮色。

默认值：#FF5EA1FF

**类型：** string

**默认值：** #FF5EA1FF

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## trackBlur

```TypeScript
trackBlur?: number
```

设置描边背景模糊值，单位：vp。

默认值：20

设置小于0的值时，按照默认值处理。

**类型：** number

**默认值：** 20

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## trackColor

```TypeScript
trackColor?: string
```

设置描边背景色。

默认值：#33FFFFFF

**类型：** string

**默认值：** #33FFFFFF

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## trackThickness

```TypeScript
trackThickness?: number
```

正常状态下弧形Slider的描边粗细，单位：vp。

默认值：5

取值范围：[5, 16]，异常值按默认值处理。

**类型：** number

**默认值：** 5

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

