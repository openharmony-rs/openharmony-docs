# SegmentButton

分段按钮组件包含页签类分段按钮、胶囊类单选分段按钮和胶囊类多选分段按钮。

> **说明：**
>
> - 分段按钮不支持[通用属性](ts-component-general-attributes.md)。分段按钮使用当前区域可使用的最大宽度作为组件宽度，并且根据按钮个数平均分配每个按钮宽度；分段按钮高度根据按钮内容（文本及图片）自动适应，其最小高度为28vp。
>
> - @Prop装饰的属性为可选参数，仅当与@Require装饰器联合使用时，才必须在构造时传入对应参数。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableStateAnimation

```TypeScript
enableStateAnimation: boolean
```

设置当通过变量修改selectedIndex值时，是否开启分段按钮的属性动画。

true表示开启分段按钮的属性动画；false表示不开启分段按钮的属性动画，使用原有动画。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 24

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
maxFontScale: number | Resource
```

分段按钮选项文字的最大字体放大倍数。

取值范围：[1, 2]

当设置的值小于1时，按值为1处理，设置的值大于2时，按值为2处理。

**类型：** number | Resource

**起始版本：** 14

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onItemClicked

```TypeScript
onItemClicked?: Callback<number>
```

当分段按钮选项被点击时，触发的回调函数接收被点击的选项下标作为参数。若不传入此参数，则点击时不触发回调。

**类型：** Callback<number>

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: SegmentButtonOptions
```

分段按钮选项。

**类型：** SegmentButtonOptions

**起始版本：** 11

**装饰器类型：** @ObjectLink

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndexes

```TypeScript
selectedIndexes: number[]
```

分段按钮的选中项编号，第一项的编号为0，之后顺序增加。

**说明：**

`selectedIndexes`使用[@Link装饰器：父子双向同步](../../../../ui/state-management/arkts-link.md)，仅支持有效的按钮编号（第一个按钮编号为0，之后按顺序累加），如没有
选中项可传入空数组`[]`。

**类型：** number[]

**起始版本：** 11

**装饰器类型：** @Link

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

