# RadialGradientOptions

径向渐变参数。

> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

> **说明：**  
>  
> colors参数的约束：  
>  
> [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)表示填充的颜色，number表示指定颜色所处的位置，取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。想要实现多个颜色渐变  
> 效果时，多个数组中number参数建议递增设置，如后一个数组number参数比前一个数组number小的话，按照等于前一个数组number的值处理。

**起始版本：** 18

<!--Device-unnamed-declare interface RadialGradientOptions--><!--Device-unnamed-declare interface RadialGradientOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## center

```TypeScript
center: [Length, Length]
```

Defines center point for radial gradient.

Anonymous Object Rectification.

**类型：** [Length, Length]

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-RadialGradientOptions-center: [Length, Length]--><!--Device-RadialGradientOptions-center: [Length, Length]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors: Array<[ResourceColor, number]>
```

Defines color description for gradients.

Anonymous Object Rectification.

**类型：** Array<[ResourceColor, number]>

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-RadialGradientOptions-colors: Array<[ResourceColor, number]>--><!--Device-RadialGradientOptions-colors: Array<[ResourceColor, number]>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: Length
```

Defines radius of the radial gradient.

Anonymous Object Rectification.

**类型：** Length

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-RadialGradientOptions-radius: Length--><!--Device-RadialGradientOptions-radius: Length-End-->

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

<!--Device-RadialGradientOptions-repeating?: boolean--><!--Device-RadialGradientOptions-repeating?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

