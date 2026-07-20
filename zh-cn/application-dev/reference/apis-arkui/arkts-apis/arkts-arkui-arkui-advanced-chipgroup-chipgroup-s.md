# ChipGroup

> **说明：**  
>  
> 1. 针对`selectedIndexes`和`multiple`接口，当`multiple`等于`false`时，如果没有传入`selectedIndexes`，默认是第一个Chip被选中，如果传入的  
> `selectedIndexes`有一个以上的元素时，默认第一个索引的Chip被选中。  
>  
> 2. 使用suffix接口时，需引入IconGroupSuffix接口，若不传入，suffix将为空。  
>  
> 3. 图标填充色（`fillColor`和`activedFillColor`）的设置应与字体颜色（`fontColor`）保持一致。如果需要设置不同的颜色，可以在传入  
> `[ChipGroupSpaceOptions](#chipgroupspaceoptions)`时使用`prefixSymbol`。

**起始版本：** 12

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct ChipGroup--><!--Device-unnamed-export declare struct ChipGroup-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipItemLabelOptions, ChipGroupSpaceOptions, SymbolItemOptions, SuffixImageIconOptions, IconGroupSuffix, IconItemOptions, ChipItemStyle, ChipGroupItemOptions, ChipGroup, IconOptions } from '@kit.ArkUI';
```

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor-1)、[border](../arkts-components/arkts-arkui-commonmethod-c.md#border-1)、[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow-1)等视觉属性。

默认值：undefined

值为undefined时，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroup-backgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroup-backgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## chipGroupPadding

```TypeScript
chipGroupPadding?: ChipGroupPaddingOptions
```

设置ChipGroup的上下内边距，以控制整体高度。类型为[ChipGroupPaddingOptions](arkts-arkui-arkui-advanced-chipgroup-chipgrouppaddingoptions-i.md)。

默认值：{ top: 14, bottom: 14 }

单位：vp

值为undefined时，按默认值处理。

**类型：** ChipGroupPaddingOptions

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroup-chipGroupPadding?: ChipGroupPaddingOptions--><!--Device-ChipGroup-chipGroupPadding?: ChipGroupPaddingOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## chipGroupSpace

```TypeScript
chipGroupSpace?: ChipGroupSpaceOptions
```

左右内边距及Chip之间间距。参考[ChipGroupSpaceOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupspaceoptions-i.md)类型。

默认值：{ itemSpace: 8, startSpace: 16, endSpace: 16 }

单位：vp

值为undefined时，按默认值处理。

**类型：** ChipGroupSpaceOptions

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroup-chipGroupSpace?: ChipGroupSpaceOptions--><!--Device-ChipGroup-chipGroupSpace?: ChipGroupSpaceOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemStyle

```TypeScript
itemStyle?: ChipItemStyle
```

`Chip`的`style`属性，如颜色，大小等，参考[ChipItemStyle](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md)类型。

默认值：

{ size: ChipSize.NORMAL, backgroundColor: $r('sys.color.ohos_id_color_button_normal'), fontColor: $r('sys.color.ohos_id_color_text_primary'), selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize') }

值为undefined时，按默认值处理。

**类型：** ChipItemStyle

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroup-itemStyle?: ChipItemStyle--><!--Device-ChipGroup-itemStyle?: ChipItemStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: ChipGroupItemOptions[]
```

每个Chip的特定属性，参考[ChipGroupItemOptions[]]{@link ChipGroupItemOptions}类型。

若为undefined时，ChipGroup默认为空。

**类型：** ChipGroupItemOptions[]

**起始版本：** 12

**装饰器类型：** @Require、@Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroup-items: ChipGroupItemOptions[]--><!--Device-ChipGroup-items: ChipGroupItemOptions[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiple

```TypeScript
multiple?: boolean
```

是否选中多个`Chip`。

`true`：支持多个`Chip`选中；`false`：仅支持单个`Chip`选中。

默认值：`false`

值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroup-multiple?: boolean--><!--Device-ChipGroup-multiple?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<Array<number>>
```

Chip状态改变时的回调方法。

若为undefined，表示解绑事件。

**类型：** Callback&lt;Array&lt;number&gt;&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroup-onChange?: Callback<Array<number>>--><!--Device-ChipGroup-onChange?: Callback<Array<number>>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundSystemMaterial

```TypeScript
selectedBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件被选中时的系统材质样式。不同的材料有不同的效果，会影响组件的背景颜色、边框、阴影和其他视觉属性。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroup-selectedBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroup-selectedBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndexes

```TypeScript
selectedIndexes?: Array<number>
```

被选中Chip的索引。

默认值：[0]

值为undefined时，按默认值处理。

**类型：** Array&lt;number&gt;

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroup-selectedIndexes?: Array<number>--><!--Device-ChipGroup-selectedIndexes?: Array<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffix

```TypeScript
suffix?: Callback<void>
```

支持开发者自定义builder，如需在组件最右侧显示自定义内容可配置suffix属性，使用属性suffix需引用[IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md)接口。

默认不传入时，没有suffix。

值为undefined时，没有suffix。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroup-suffix?: Callback<void>--><!--Device-ChipGroup-suffix?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

