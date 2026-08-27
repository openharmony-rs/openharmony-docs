# ChipGroup

ChipGroup组件提供操作块群组能力，支持单选或多选模式，可自定义样式、图标和间距，支持选中状态管理和事件回调。适用于文件分类、资源筛选、标签选择、内容分组等多种场景，帮助开发者快速实现选择功能，提供统一的视觉和交互体验。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的backgroundColor、 [border](../arkts-components/arkts-arkui-commonmethod-c.md#border)、shadow视觉属性。设置自 动反色的系统材质时，fontColor如果使用系统预定义的可反色颜色资源（如`\$r('sys.color.font_primary')`），颜色自动适配到材质背景色的反色。默认值：undefined值为undefined时，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## chipGroupPadding

```TypeScript
chipGroupPadding?: ChipGroupPaddingOptions
```

设置ChipGroup的上下内边距，以控制整体高度。类型为[ChipGroupPaddingOptions](arkts-arkui-arkui-advanced-chipgroup-chipgrouppaddingoptions-i.md)。默认值：{ top: 14, bottom: 14 }单位：vp值为undefined时，按默认值处理。

**类型：** [ChipGroupPaddingOptions](arkts-arkui-arkui-advanced-chipgroup-chipgrouppaddingoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## chipGroupSpace

```TypeScript
chipGroupSpace?: ChipGroupSpaceOptions
```

左右内边距及Chip之间间距。参考[ChipGroupSpaceOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupspaceoptions-i.md)类型。默认值：{ itemSpace: 8, startSpace: 16, endSpace: 16 }单位：vp值为undefined时，按默认值处理。

**类型：** [ChipGroupSpaceOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupspaceoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: ChipGroupItemOptions[]
```

每个Chip的特定属性，参考[ChipGroupItemOptions[]][ChipGroupItemOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupitemoptions-i.md)类型。若为undefined时，ChipGroup默认为空。

**类型：** [ChipGroupItemOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupitemoptions-i.md)[]

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemStyle

```TypeScript
itemStyle?: ChipItemStyle
```

`Chip`的`style`属性，如颜色、大小等，参考[ChipItemStyle](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md)类型。默认值：{ size: ChipSize.NORMAL, backgroundColor: \$r('sys.color.ohos_id_color_button_normal'), fontColor: \$r('sys.color.ohos_id_color_text_primary'), selectedFontColor: \$r('sys.color.ohos_id_color_text_primary_contrary'), selectedBackgroundColor: \$r('sys.color.ohos_id_color_emphasize') }值为undefined时，按默认值处理。

**类型：** [ChipItemStyle](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiple

```TypeScript
multiple?: boolean
```

是否选中多个`Chip`。`true`：支持多个`Chip`选中；`false`：仅支持单个`Chip`选中。默认值：`false`值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<Array<number>>
```

Chip状态改变时的回调方法，用于监听Chip选中状态的变更。该回调在selectedIndexes属性更新后触发，开发者可在回调中获取最新的选中状态并执行相应操作，如更新UI、保存选中数据、触发业务逻辑等。当需要响应Chip选中 状态变化时传入此参数，不传入时不监听状态变化。若为undefined，不触发该回调。

**类型：** Callback&lt;Array&lt;number&gt;&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundSystemMaterial

```TypeScript
selectedBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件选中状态的系统材质样式。不同材质具有不同的效果，能够影响组件选中时的backgroundColor、 [border](../arkts-components/arkts-arkui-commonmethod-c.md#border)、shadow视觉属性。设置自 动反色的系统材质时，selectedFontColor如果使用系统预定义的可反色颜色资源（如`\$r('sys.color.font_primary')`），颜色自动适配到材质背景色的反色。当设置 selectedBackgroundSystemMaterial时，应将selectedBackgroundColor设为Color.Transparent，否则会与系统材质冲突。默认值：undefined值为undefined时，不应用选中状态的材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndexes

```TypeScript
selectedIndexes?: Array<number>
```

被选中Chip的索引。取值范围：索引值为非负整数，且不能超过items数组长度减1。传入负数、超出数组范围的索引值或非整数时，该索引值不生效。默认值：[0]若multiple=false，selectedIndexes为空数组时默认选中第1个；selectedIndexes包含多个元素时仅第一个索引生效。值为undefined时，按默认值处理。

**类型：** Array&lt;number&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffix

```TypeScript
suffix?: Callback<void>
```

支持开发者自定义builder，如需在组件最右侧显示自定义内容可配置suffix属性，使用属性suffix需引用[IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md)接口。默认不传入时，没有suffix。值为undefined时，没有suffix。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
