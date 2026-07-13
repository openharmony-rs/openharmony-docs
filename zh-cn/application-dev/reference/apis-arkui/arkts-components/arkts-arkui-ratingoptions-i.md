# RatingOptions

评分组件的信息。

> **说明：**
>
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## indicator

```TypeScript
indicator?: boolean
```

设置评分组件作为指示器使用，值为true时，不可改变评分。

默认值：false，可进行评分

**说明：**

indicator=true时，默认组件高度height=12.0vp，组件width=height * stars。

indicator=false时，默认组件高度height=28.0vp，组件width=height * stars。

**类型：** boolean

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rating

```TypeScript
rating: number
```

设置并接收评分值。

默认值：0

取值范围： [0, stars]

小于0取0，大于[stars](RatingAttribute#stars(value: number))取最大值stars。

该参数支持[$$](../../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

