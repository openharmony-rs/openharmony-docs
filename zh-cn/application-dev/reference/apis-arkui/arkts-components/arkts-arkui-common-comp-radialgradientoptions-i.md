# RadialGradientOptions

```TypeScript
declare interface RadialGradientOptions
```

径向渐变参数。

> **说明：** 
> 
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。
> 
> **说明：** 
> 
> colors参数的约束：
> 
> [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)表示填充的颜色，number表示指定颜色所处的位置，取值范围为[0,1.0]，设置的值小于0时，按0处理，设置的值大于1.0时，按1.0处理。0表示当前组件渐
> 变区域的开始处，1.0表示渐变区域的结尾处。为了实现多个颜色渐变效果，多个数组中的number类型参数应递增设置，如果后一个数组中的number类型参数小于前一个数组的number类型参数，将按照等于前一个数组number值处理。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## center

```TypeScript
center: [Length, Length]
```

径向渐变的中心点，即相对于当前组件左上角的坐标，number类型时单位为vp。第一个元素为x坐标，第二个元素为y坐标。

**类型：** [Length, Length]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors: Array<[ResourceColor, number]>
```

指定渐变色和其对应的百分比位置的数组，设置非法颜色直接跳过。ResourceColor表示颜色，number表示该颜色所处的位置，取值范围为[0, 1.0]，设置的值小于0时，按0处理，设置的值大于1.0时，按1.0处理。0表示需要设置渐变色的开始处，1.0表示渐变色的结束处。为了实现多个颜色渐变效果，多个数组中的number类型参数应递增设置。如果后一个数组中的number类型参数小于前一个数组的number类型参数，将按照等于前一个数组number值处理。

默认值：[]，无渐变效果。

**类型：** Array&lt;[ResourceColor, number]&gt;

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: Length
```

径向渐变的半径，number类型时单位为vp。

取值范围：[0,+∞)。设置的值小于0时，按值为0处理。设置的值为undefined时，系统将根据组件尺寸自动计算渐变半径。

**类型：** [Length](../arkts-apis/arkts-arkui-length-t.md)

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
