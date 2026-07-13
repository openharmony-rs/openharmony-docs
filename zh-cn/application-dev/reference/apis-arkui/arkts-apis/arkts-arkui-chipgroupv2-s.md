# ChipGroupV2

ChipGroupV2组件提供操作块群组，用于文件或资源内容的分类等场景。

该组件基于[状态管理（V2）](../../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于
[状态管理（V1）](../../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组
件层级。借助状态管理（V2），开发者可以更灵活地控制组件的数据和状态，实现更高效的用户界面刷新。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

build函数用于构造ChipGroupV2高级组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $items

```TypeScript
$items?: Callback<ChipGroupV2Items>
```

ChipV2项的双向绑定回调方法。

默认值：undefined，不触发回调。

**类型：** Callback<ChipGroupV2Items>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $selectedIndexes

```TypeScript
$selectedIndexes?: Callback<Array<number>>
```

被选中ChipV2索引的双向绑定回调方法。

默认值：undefined，不触发回调。

**类型：** Callback<Array<number>>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## chipGroupPadding

```TypeScript
chipGroupPadding?: ChipGroupV2Padding
```

设置ChipGroupV2的上下内边距，以控制整体高度。类型为[ChipGroupV2Padding](arkts-arkui-chipgroupv2padding-c.md)。

默认值：{ top: 14, bottom: 14 }

单位：vp

值为undefined时，按默认值处理。

**类型：** ChipGroupV2Padding

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## chipGroupSpace

```TypeScript
chipGroupSpace?: ChipGroupV2Space
```

左右内边距及ChipV2之间间距。参考[ChipGroupV2Space](arkts-arkui-chipgroupv2space-c.md)类型。

默认值：{ itemSpace: 8, startSpace: 16, endSpace: 16 }

单位：vp

值为undefined时，按默认值处理。

**类型：** ChipGroupV2Space

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemStyle

```TypeScript
itemStyle?: ChipGroupV2ItemStyle
```

ChipV2的style属性，如颜色，大小等，参考[ChipGroupV2ItemStyle](arkts-arkui-chipgroupv2itemstyle-c.md)类型。

默认值：

{ size: ChipV2Size.NORMAL, backgroundColor: $r('sys.color.ohos_id_color_button_normal'), fontColor: $r('
sys.color.ohos_id_color_text_primary'), selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize') }

值为undefined时，按默认值处理。

图标填充色（[fillColor](../../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipV2.md#chipv2imageiconconfig)和
[activatedFillColor](../../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipV2.md#chipv2imageiconconfig)
）的设置与字体颜色（[fontColor](arkts-arkui-chipgroupv2itemstyleconfig-i.md)）保持一致。如果需要设置不同的颜色，可以在传入items时使用
[prefixSymbolIcon](arkts-arkui-chipgroupv2itemconfig-i.md)和[suffixSymbolIcon](arkts-arkui-chipgroupv2itemconfig-i.md)。

**类型：** ChipGroupV2ItemStyle

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: ChipGroupV2Items
```

每个ChipV2的特定属性，参考[ChipGroupV2ItemConfig](arkts-arkui-chipgroupv2itemconfig-i.md)类型。

值为undefined或空数组时，ChipGroupV2不渲染内部的
[ChipV2](../../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipV2.md)。

**类型：** ChipGroupV2Items

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiple

```TypeScript
multiple?: boolean
```

是否选中多个ChipV2。

true：支持多个ChipV2选中；false：仅支持单个ChipV2选中。

默认值：false

值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<Array<number>>
```

ChipV2状态改变时的回调方法。

默认值：undefined，不触发事件。

**类型：** Callback<Array<number>>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndexes

```TypeScript
selectedIndexes?: Array<number>
```

被选中ChipV2的索引。

默认值：[0]

值为undefined时，按默认值处理。

当multiple等于false时，如果没有传入selectedIndexes，默认是第一个ChipV2被选中，如果传入的selectedIndexes有多个元素时，默认第一个索引的ChipV2被选中。

**类型：** Array<number>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffix

```TypeScript
suffix?: Callback<void>
```

支持开发者自定义builder，如需在组件最右侧显示自定义内容可配置suffix属性，使用属性suffix需引用
[ChipGroupV2IconGroupSuffix](arkts-arkui-chipgroupv2icongroupsuffix-s.md)接口。

默认值：undefined，不在最右侧显示自定义内容。

**类型：** Callback<void>

**起始版本：** 26.0.0

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

