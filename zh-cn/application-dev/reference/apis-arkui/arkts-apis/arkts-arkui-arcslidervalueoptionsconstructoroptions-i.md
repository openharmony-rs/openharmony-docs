# ArcSliderValueOptionsConstructorOptions

ArcSliderValueOptions的构造信息。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

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

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

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

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## progress

```TypeScript
progress?: number
```

设置当前进度值。

默认值：与参数min的取值一致

**类型：** number

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

