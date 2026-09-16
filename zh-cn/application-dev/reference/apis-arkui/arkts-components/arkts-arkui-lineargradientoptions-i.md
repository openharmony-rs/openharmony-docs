# LinearGradientOptions

线性渐变的参数。

> **说明：** 
> 
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle?: number | string
```

线性渐变的角度，number类型时单位为度（°）。角度为0度时渐变方向从下往上，顺时针旋转为正向角度。

取值范围：(-∞,+∞)，设置的值大于0时，按顺时针方向，小于0时，按逆时针方向。

默认值：180

角度为字符串时，合法的取值为数字（默认单位为度，即deg）或数字后带"deg"（度）、"rad"（弧度）、"grad"（梯度）、"turn"（圈）单位，例如："90"、 "90deg"、"1.57rad"。传入非法格式的字符串时，按默认值180处理。

**类型：** number &#124; string

**默认值：** 
- API版本18+：180

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors: Array<[ResourceColor, number]>
```

指定渐变色和其对应的百分比位置的数组，设置不符合ResourceColor格式要求的颜色值时，该颜色项直接跳过不生效。设置metricsColors时此参数失效。ResourceColor表示颜色，number表示该颜色所处的位置，取值范围为[0, 1.0]，设置的值小于0时，按0处理，设置的值大于1.0时，按1.0处理。0表示需要设置渐变色的开始处，1.0表示渐变色的结束处。为了实现多个颜色渐变效果，多个数组中的number类型参数应递增设置。如果后一个数组中的number类型参数小于前一个数组的number类型参数，将按照等于前一个数组number值处理。

默认值：[]，无渐变效果。

**类型：** Array&lt;[ResourceColor, number]&gt;

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: GradientDirection
```

线性渐变的方向，设置angle为非undefined后，direction不生效。设置为GradientDirection.None时，按默认方向渐变。默认值：GradientDirection.Bottom。

**类型：** [GradientDirection](../arkts-apis/arkts-arkui-gradientdirection-e.md)

**默认值：** 
- API版本18+：GradientDirection.Bottom

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeating

```TypeScript
repeating?: boolean
```

设置渐变颜色是否在组件范围内循环重复填充。

默认值：false。

true：渐变效果在组件范围内循环重复。

false：渐变效果仅在指定范围内显示一次。

**类型：** boolean

**默认值：** 
- API版本18+：false

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
