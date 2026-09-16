# SweepGradientOptions

角度渐变参数。

> **说明：** 
> 
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。
> 
> **说明：** 
> 
> metricsColors参数的约束：
> 
> [ColorMetrics](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md)表示填充的颜色，可以使用
> [colorWithSpace](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md#colorwithspace)方法构造指定色域属性的颜色。number表示指定颜色所处的位置，取值范围为
> [0, 1.0]，设置的值小于0时，按0处理，设置的值大于1.0时，按1.0处理。0表示当前组件渐变区域的开始处，1.0表示渐变区域的结束处。为了实现多个颜色渐变效果，多个数组中的number类型参数应递增设置。如果后一个数组中的
> number类型参数小于前一个数组的number类型参数，将按照等于前一个数组number值处理。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## center

```TypeScript
center: [Length, Length]
```

为角度渐变的中心点，即相对于当前组件左上角的坐标，number类型时单位为vp。

**类型：** [Length, Length]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors: Array<[ResourceColor, number]>
```

指定渐变色和其对应的百分比位置的数组，设置不符合ResourceColor格式要求的颜色值时，该颜色项直接跳过不生效。设置metricsColors时此参数失效。ResourceColor表示颜色。number表示该颜色所处的位置，取值范围为[0, 1.0]，设置的值小于0时，按0处理，设置的值大于1.0时，按1.0处理。0表示需要设置渐变色的开始处，1.0表示渐变色的结束处。为了实现多个颜色渐变效果，多个数组中的number类型参数应递增设置。如果后一个数组中的number类型参数小于前一个数组的number类型参数，将按照等于前一个数组number值处理。

默认值：[]，无渐变效果。

**类型：** Array&lt;[ResourceColor, number]&gt;

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: number | string
```

角度渐变的终点。取值范围：[0, 360]。转换为度的单位之后，设置为小于0度的值时，按值为0度处理，设置为大于360度的值时，按值为360度处理。默认值：0。

角度为字符串时，合法的取值为数字（默认单位为度，即deg）或数字后带"deg"（度）、"rad"（弧度）、"grad"（梯度）、"turn"（圈）单位。例如："90"、 "90deg"、"1.57rad"。传入非法格式的字符串时，按默认值0处理。

**类型：** number &#124; string

**默认值：** 
- API版本18+：0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## metricsColors

```TypeScript
metricsColors?: Array<[ColorMetrics, number]>
```

指定渐变颜色和其对应的百分比位置的数组，设置非法颜色直接跳过。当需要使用广色域（如P3色域）颜色时，应使用metricsColors代替colors。设置metricsColors时colors失效。每个渐变ColorMetrics的色域属性应当统一，设置不同色域属性则认为非法。使用广色域（如DISPLAY_P3）时，需先通过setColorSpace接口将当前窗口设置为广色域。默认不设置，不设置时使用colors参数。

**类型：** Array&lt;[ColorMetrics, number]&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

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

## rotation

```TypeScript
rotation?: number | string
```

角度渐变的旋转角度。未设置rotation时，默认值为0，即不旋转。

角度为字符串时，合法的取值为数字或数字后带"deg"（度）、"rad"（弧度）、"grad"（梯度）、"turn"（圈）单位。例如："90"、 "90deg"、"1.57rad"。传入非法格式的字符串时，按默认值0处理。取值有0到360度的限制，转换为度的单位之后，值在0到360度之间，设置为小于0度的值时，按值为0度处理，设置为大于360度的值时，按值为360度处理。

**类型：** number &#124; string

**默认值：** 
- API版本18+：0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: number | string
```

角度渐变的起点。未设置start时，默认值为0，即起始角度为0度。

角度为字符串时，合法的取值为数字（默认单位为度，即deg）或数字后带"deg"（度）、"rad"（弧度）、"grad"（梯度）、"turn"（圈）单位。例如："90"、 "90deg"、"1.57rad"。传入非法格式的字符串时，按默认值0处理。取值有0到360度的限制，转换为度的单位之后，值在0到360度之间，设置为小于0度的值时，按值为0度处理，设置为大于360度的值时，按值为360度处理。

**类型：** number &#124; string

**默认值：** 
- API版本18+：0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
