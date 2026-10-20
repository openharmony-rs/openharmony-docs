# SegmentButton

```TypeScript
declare struct SegmentButton
```

创建页签类分段按钮或胶囊类分段按钮。

## 子组件

无

## 属性

不支持[通用属性](ts-component-general-attributes.md)。

## 事件

不支持[通用事件](ts-component-general-events.md)。

**起始版本：** 11

**装饰器类型：** @Component

<!--Device-unnamed-declare struct SegmentButton--><!--Device-unnamed-declare struct SegmentButton-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, SegmentButtonInteractionMode, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## enableStateAnimation

```TypeScript
enableStateAnimation: boolean
```

设置当通过变量修改selectedIndexes值时，是否开启分段按钮的属性动画。

true表示开启分段按钮的属性动画；false表示不开启分段按钮的属性动画。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 24

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-SegmentButton-enableStateAnimation: boolean--><!--Device-SegmentButton-enableStateAnimation: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
maxFontScale: number | Resource
```

分段按钮选项文字的最大字体放大倍数，用于限制字体缩放上限。当需要控制字体放大倍数以适应特定UI布局或避免文字过大时传入此参数。

取值范围：[1, 2]

当设置的值小于1时，按值为1处理，设置的值大于2时，按值为2处理。

默认值：1

**类型：** number &#124; [Resource](arkts-arkui-resource-t.md)

**起始版本：** 14

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

<!--Device-SegmentButton-maxFontScale: number | Resource--><!--Device-SegmentButton-maxFontScale: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onItemClicked

```TypeScript
onItemClicked?: Callback<number>
```

当分段按钮选项被点击时，触发的回调函数接收被点击的选项下标作为参数。若不传入此参数，则点击时不触发回调。

**类型：** Callback&lt;number&gt;

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-SegmentButton-onItemClicked?: Callback<number>--><!--Device-SegmentButton-onItemClicked?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: SegmentButtonOptions
```

分段按钮的配置选项，用于设置按钮的类型（页签类或胶囊类）、外观样式（颜色、字体、尺寸等）、按钮内容和选中状态等属性。

**类型：** [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md)

**起始版本：** 11

**装饰器类型：** @ObjectLink

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-SegmentButton-options: SegmentButtonOptions--><!--Device-SegmentButton-options: SegmentButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndexes

```TypeScript
selectedIndexes: number[]
```

分段按钮的选中项编号，第一项的编号为0，之后顺序增加。

**说明：** 

`selectedIndexes`使用[@Link装饰器：父子双向同步](../../../ui/state-management/arkts-link.md)，仅支持有效的按钮编号（第一个按钮编号为0，之后按顺序累加，最大编号为按钮数量减1），传入无效编号时该编号不生效。如没有选中项可传入空数组`[]`。

**类型：** number[]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-SegmentButton-selectedIndexes: number[]--><!--Device-SegmentButton-selectedIndexes: number[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
