# LinearGradientOptions

线性渐变的参数。
> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

<!--Device-unnamed-declare interface LinearGradientOptions--><!--Device-unnamed-declare interface LinearGradientOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle?: number | string
```

Defines starting angle of linear gradient.

Anonymous Object Rectification.

**类型：** number \| string

**默认值：** 180

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-LinearGradientOptions-angle?: number | string--><!--Device-LinearGradientOptions-angle?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors: Array<[ResourceColor, number]>
```

Defines color description for gradients.

Anonymous Object Rectification.

**类型：** Array&lt;[ResourceColor, number]&gt;

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-LinearGradientOptions-colors: Array<[ResourceColor, number]>--><!--Device-LinearGradientOptions-colors: Array<[ResourceColor, number]>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: GradientDirection
```

Defines the direction of linear gradient.

Anonymous Object Rectification.

**类型：** GradientDirection

**默认值：** GradientDirection.Bottom

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-LinearGradientOptions-direction?: GradientDirection--><!--Device-LinearGradientOptions-direction?: GradientDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeating

```TypeScript
repeating?: boolean
```

Defines gradient colors with repeated coloring.

Anonymous Object Rectification.

**类型：** boolean

**默认值：** false

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-LinearGradientOptions-repeating?: boolean--><!--Device-LinearGradientOptions-repeating?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

