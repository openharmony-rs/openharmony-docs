# SegmentButton

分段按钮组件包含页签类分段按钮和胶囊类分段按钮。页签类分段按钮适用于页面或内容区域的切换场景；胶囊类分段按钮适用于单选或多选的选择场景，包含胶囊类单选分段按钮和胶囊类多选分段按钮。该组件支持自定义文本颜色、字体大小、字体粗细、背景色、 图片尺寸、内边距、背景模糊材质等外观属性，支持仅文本、仅图标和图标+文本三种按钮样式，并提供无障碍朗读、布局方向镜像、自定义圆角、属性动画等能力，适用于需要快速构建符合设计规范的分段选择界面的场景。

**起始版本：** 11

<!--Device-unnamed-declare struct SegmentButton--><!--Device-unnamed-declare struct SegmentButton-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
import { SegmentButtonV2ItemOptions, OnSelectedIndexChange, OnSelectedIndexesChange, SegmentButtonV2Item, SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## enableStateAnimation

```TypeScript
@Prop
  enableStateAnimation: boolean
```

设置当通过变量修改selectedIndexes值时，是否开启分段按钮的属性动画。 true表示开启分段按钮的属性动画；false表示不开启分段按钮的属性动画。 默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButton-@Prop  enableStateAnimation: boolean--><!--Device-SegmentButton-@Prop  enableStateAnimation: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
@Prop
  maxFontScale: number | Resource
```

分段按钮选项文字的最大字体放大倍数，用于限制字体缩放上限。当需要控制字体放大倍数以适应特定UI布局或避免文字过大时传入此参数。 取值范围：[1, 2] 当设置的值小于1时，按值为1处理，设置的值大于2时，按值为2处理。 默认值：1

**类型：** number \| Resource

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButton-@Prop  maxFontScale: number | Resource--><!--Device-SegmentButton-@Prop  maxFontScale: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onItemClicked

```TypeScript
onItemClicked?: Callback<number>
```

当分段按钮选项被点击时，触发的回调函数接收被点击的选项下标作为参数。若不传入此参数，则点击时不触发回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;number&gt;

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButton-onItemClicked?: Callback<number>--><!--Device-SegmentButton-onItemClicked?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
@ObjectLink
  options: SegmentButtonOptions
```

分段按钮的配置选项，用于设置按钮的类型（页签类或胶囊类）、外观样式（颜色、字体、尺寸等）、按钮内容和选中状态等属性。

**类型：** SegmentButtonOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButton-@ObjectLink  options: SegmentButtonOptions--><!--Device-SegmentButton-@ObjectLink  options: SegmentButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndexes

```TypeScript
@Link
  selectedIndexes: number[]
```

分段按钮的选中项编号，第一项的编号为0，之后顺序增加。 **说明：** `selectedIndexes`使用[@Link装饰器：父子双向同步](../../../ui/state-management/arkts-link.md)，仅支持有效的按钮编号（第一个按钮编号为0，之后按顺序累加，最大编号 为按钮数量减1），传入无效编号时该编号不生效。如没有选中项可传入空数组`[]`。

**类型：** number[]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SegmentButton-@Link  selectedIndexes: number[]--><!--Device-SegmentButton-@Link  selectedIndexes: number[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

