# ChipGroup
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @song-song-song-->
<!--Designer: @fenglinbailu-->
<!--Tester: @weixin_45530366-->
<!--Adviser: @Brilliantry_Rui-->

ChipGroup组件提供操作块群组，用于文件或资源内容的分类等场景。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。

## 导入模块

```typescript
import { ChipSize, ChipGroup } from '@kit.ArkUI';
```

## 子组件

无


## 属性

不支持[通用属性](ts-component-general-attributes.md)。

## 事件

不支持[通用事件](ts-component-general-events.md)。

## ChipGroup

ArkTS-Dyn示例：

```ts
ChipGroup({
  items: ChipGroupItemOptions[],
  itemStyle?: ChipItemStyle,
  selectedIndexes?: Array<number>,
  multiple?: boolean,
  chipGroupSpace?: ChipGroupSpaceOptions,
  chipGroupPadding?: ChipGroupPaddingOptions,
  backgroundSystemMaterial?: uiMaterial.Material,
  selectedBackgroundSystemMaterial?: uiMaterial.Material,
  onChange?: Callback<Array<number>>,
  suffix?: Callback<void>
})
```

ArkTS-Sta示例：

```ts
ChipGroup({
  items: ChipGroupItemOptions[],
  itemStyle?: ChipItemStyle,
  selectedIndexes?: Array<int>,
  multiple?: boolean,
  chipGroupSpace?: ChipGroupSpaceOptions,
  chipGroupPadding?: ChipGroupPaddingOptions,
  onChange?: Callback<Array<int>>,
  suffix?: ChipGroupSuffixBuilder
})
```

**装饰器类型：** [@Component](../../../ui/state-management/arkts-create-custom-components.md#component)

### 属性

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称            | 类型                                            | 必填 | 装饰器类型 | 说明                                                                                     |
| --------------- | ----------------------------------------------- | ---- | ------------------------------------------------------------                             | ------------------------------------------------------------                             |
| items           | [ChipGroupItemOptions[]](#chipgroupitemoptions) | 是   | ArkTS-Dyn: [@Require](../../../ui/state-management/arkts-require.md) &nbsp;[@Prop](../../../ui/state-management/arkts-prop.md) <br/> ArkTS-Sta: @Require &nbsp;[@PropRef](../../../ui/state-management-static/arkts-static-propref.md) | 每个[Chip](./ohos-arkui-advanced-Chip.md)的特定属性，参考[ChipGroupItemOptions[]](#chipgroupitemoptions)类型。<br/>若为undefined时，ChipGroup默认为空。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23            |
| itemStyle       | [ChipItemStyle](#chipitemstyle)                 | 否   | ArkTS-Dyn: @Prop<br/> ArkTS-Sta: @PropRef  | `Chip`的`style`属性，如颜色，大小等，参考[ChipItemStyle](#chipitemstyle)类型。<br/>默认值：<br>{  size: ChipSize.NORMAL, backgroundColor: $r('sys.color.ohos_id_color_button_normal'), fontColor: $r('sys.color.ohos_id_color_text_primary'), selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'), selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize') } <br>值为undefined时，按默认值处理。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| selectedIndexes | ArkTS-Dyn: [Array](../../apis-arkts/arkts-apis-arkts-collections-Array.md)&lt;number&gt; <br/> ArkTS-Sta: Array&lt;int&gt; | 否   | ArkTS-Dyn: @Prop<br/> ArkTS-Sta: @PropRef  | 被选中Chip的索引。<br/>默认值：[0] <br>值为undefined时，按默认值处理。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| multiple        | boolean                                         | 否   | ArkTS-Dyn: @Prop<br/> ArkTS-Sta: @PropRef  | 是否选中多个`Chip`。<br/>`true`：支持多个`Chip`选中；`false`：仅支持单个`Chip`选中。<br>默认值：`false` <br>值为undefined时，按默认值处理。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| chipGroupSpace  | [ChipGroupSpaceOptions](#chipgroupspaceoptions) | 否   | ArkTS-Dyn: @Prop<br/> ArkTS-Sta: @PropRef | 左右内边距及Chip之间间距。参考[ChipGroupSpaceOptions](#chipgroupspaceoptions)类型。<br/>默认值：{ itemSpace: 8, startSpace: 16, endSpace: 16 } <br>单位：vp <br>值为undefined时，按默认值处理。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| chipGroupPadding  | [ChipGroupPaddingOptions](#chipgrouppaddingoptions) | 否   | ArkTS-Dyn: @Prop<br/> ArkTS-Sta: @PropRef  | 设置ChipGroup的上下内边距，以控制整体高度。类型为[ChipGroupPaddingOptions](#chipgrouppaddingoptions)。<br/>默认值：{ top: 14, bottom: 14 } <br>单位：vp  <br>值为undefined时，按默认值处理。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| backgroundSystemMaterial | uiMaterial.[Material](../arkts-apis-uimaterial.md#material) | 否 | @Prop | 设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的[backgroundColor](ts-universal-attributes-background.md#backgroundcolor)、[border](ts-universal-attributes-border.md#border)、[shadow](ts-universal-attributes-image-effect.md#shadow)视觉属性。<br>默认值：undefined<br>值为undefined时，不应用材质样式。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 26.0.0<br>**ArkTS-Sta起始版本：** 26.0.0 |
| selectedBackgroundSystemMaterial | uiMaterial.[Material](../arkts-apis-uimaterial.md#material) | 否 | @Prop | 设置组件选中状态的系统材质样式。不同材质具有不同的效果，能够影响组件选中时的[backgroundColor](ts-universal-attributes-background.md#backgroundcolor)、[border](ts-universal-attributes-border.md#border)、[shadow](ts-universal-attributes-image-effect.md#shadow)视觉属性。<br>默认值：undefined<br>值为undefined时，不应用选中状态的材质样式。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 26.0.0开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 26.0.0<br>**ArkTS-Sta起始版本：** 26.0.0 |
| onChange        | ArkTS-Dyn: Callback\<Array\<number>> <br/> ArkTS-Sta: Callback\<Array\<int>> | 否   | -  | Chip状态改变时的回调方法。<br/>若为undefined，表示解绑事件。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| suffix          | Callback\<void\>                                        | 否   | [@BuilderParam](../../../ui/state-management/arkts-builderparam.md) | 支持开发者自定义builder，如需在组件最右侧显示自定义内容可配置suffix属性，使用属性suffix需引用[IconGroupSuffix](#icongroupsuffix)接口。<br/>默认不传入时，没有suffix。<br>值为undefined时，没有suffix。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23  |

> **说明：**
>
> 1. 针对`selectedIndexes`和`multiple`接口，当`multiple`等于`false`时，如果没有传入`selectedIndexes`，默认是第一个Chip被选中，如果传入的`selectedIndexes`有一个以上的元素时，默认第一个索引的Chip被选中。
>
> 2. 使用suffix接口时，需引入IconGroupSuffix接口，若不传入，suffix将为空。
>
> 3. 图标填充色（`fillColor`和`activatedFillColor`）的设置应与字体颜色（`fontColor`）保持一致。如果需要设置不同的颜色，可以在传入[ChipGroupItemOptions](#chipgroupitemoptions)时使用`prefixSymbol`。

### build<sup>23+</sup>

build(): void

build函数用于构造ChipGroup高级组件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**装饰器类型：** [\@Builder](../../../ui/state-management/arkts-builder.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**ArkTS-Sta起始版本：** 23

## ChipGroupItemOptions

ChipGroupItemOptions定义每个Chip的非通用属性。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称         | 类型                           | 只读 | 可选 | 说明                              |
| ----------   | ----------------------------- | ---- | ----------------------------------- | ----------------------------------- |
| prefixIcon   | [IconOptions](#iconoptions)   | 否  | 是  | 前缀Image图标属性。<br>默认值：没有前缀Image图标。<br>值为undefined时，按默认值处理。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12 <br/> **ArkTS-Sta起始版本：** 23 |
| prefixSymbol | [ChipSymbolGlyphOptions](ohos-arkui-advanced-Chip.md#chipsymbolglyphoptions12) | 否  | 是  | 前缀SymbolGlyph图标属性。<br>默认值：没有前缀SymbolGlyph图标。<br>值为undefined时，按默认值处理。<br/> **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12 <br/> **ArkTS-Sta起始版本：** 23 |
| label        | ArkTS-Dyn: [LabelOptions](#labeloptions) <br/> ArkTS-Sta: [ChipItemLabelOptions](#chipitemlabeloptions23) | 否  | 否  | 文本属性。<br> **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 <br/>**ArkTS-Dyn起始版本：** 12 <br/> **ArkTS-Sta起始版本：** 23                           |
| suffixIcon<sup>(deprecated)</sup>   | [IconOptions](#iconoptions) | 否  | 是 | 后缀Image图标属性。<br/>默认值：不显示后缀Image图标。<br>值为undefined时，按默认值处理。<br/> **说明：** 从API version 12开始支持，从API version 14开始废弃，建议使用suffixImageIcon替代。<br/> **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>  **ArkTS模式：** 该接口仅适用于ArkTS-Dyn。 <br/> **ArkTS-Dyn起始版本：** 12 <br/>|
| suffixSymbol | [ChipSymbolGlyphOptions](ohos-arkui-advanced-Chip.md#chipsymbolglyphoptions12) | 否  | 是 | 后缀SymbolGlyph图标属性。<br>默认值：不显示后缀SymbolGlyph图标。<br>值为undefined时，按默认值处理。<br/> **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12 <br/> **ArkTS-Sta起始版本：** 23 |
| allowClose   | boolean                       | 否  | 是  | 删除图标是否显示。<br/>false表示删除图标不显示，true表示删除图标显示。<br/>默认值：false <br>值为undefined时，按默认值处理。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12 <br/> **ArkTS-Sta起始版本：** 23 |
| suffixImageIcon<sup>14+</sup> | [SuffixImageIconOptions](#suffiximageiconoptions14) | 否 | 是 | 后缀Image图标属性。<br>默认值：不显示后缀Image图标。<br>值为undefined时，按默认值处理。<br/> **原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 14 <br/> **ArkTS-Sta起始版本：** 23 |
| suffixSymbolOptions<sup>14+</sup> | [ChipSuffixSymbolGlyphOptions](ohos-arkui-advanced-Chip.md#chipsuffixsymbolglyphoptions14) | 否 | 是 | 后缀Symbol图标属性。<br>默认值：后缀Symbol图标无功能。<br>值为undefined时，按默认值处理。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 14 <br/> **ArkTS-Sta起始版本：** 23 |
| closeOptions<sup>14+</sup> | [CloseOptions](ohos-arkui-advanced-Chip.md#closeoptions14) | 否 | 是 | 默认删除图标的无障碍朗读功能属性。 <br>值为undefined时，按默认值处理。<br/> **原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 14 <br/> **ArkTS-Sta起始版本：** 23 |
| accessibilityDescription<sup>14+</sup> | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | ChipGroup中Chip项的无障碍描述。此描述用于向用户详细解释ChipGroup中Chip项，开发人员应为ChipGroup中Chip项的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的结果。特别是当这些结果无法仅从ChipGroup中Chip项的属性和无障碍文本中直接获知时。如果ChipGroup中Chip项同时具备文本属性和无障碍说明属性，当ChipGroup中Chip项被选中时，系统将首先播报ChipGroup中Chip项的文本属性，随后播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。<br/> **原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 14 <br/> **ArkTS-Sta起始版本：** 23 |
| accessibilityLevel<sup>14+</sup> | string | 否 | 是 | ChipGroup中Chip项无障碍重要性。用于控制ChipGroup中Chip项是否可被无障碍辅助服务所识别。<br>支持的值为:<br>"auto"：ChipGroup中Chip项会转换为“yes”。<br>"yes"：ChipGroup中Chip项可被无障碍辅助服务所识别。<br>"no"：ChipGroup中Chip项不可被无障碍辅助服务所识别。<br>"no-hide-descendants"：ChipGroup中Chip项及其所有子组件不可被无障碍辅助服务所识别。<br>默认值："auto"<br>值为undefined时，按默认值处理。<br/> **原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 14 <br/> **ArkTS-Sta起始版本：** 23 |


> **说明：**
>
>当传入`suffixIcon`参数时，`allowClose`不生效；未传入`suffixIcon`参数时，`allowClose`决定是否显示移除图标。

## ChipItemStyle

ChipItemStyle定义了Chip的共通属性。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称                    | 类型                                                         | 只读 | 可选 | 说明                                                         |
| ----------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| size                    | [ChipSize](ohos-arkui-advanced-Chip.md#chipsize) \| [SizeOptions](ts-types.md#sizeoptions) | 否   | 是   | Chip尺寸，使用时需要从Chip组件引入ChipSize类型。<br/>默认值：ChipSize.NORMAL或{ height: 0, width: 0 }<br/> 为undefined时，使用默认值。 |
| backgroundColor         | [ResourceColor](ts-types.md#resourcecolor)                   | 否   | 是   | Chip背景颜色。<br/>默认值：$r('sys.color.ohos_id_color_button_normal')<br/>为undefined时，backgroundColor走默认值。 |
| fontColor               | [ResourceColor](ts-types.md#resourcecolor)                   | 否   | 是   | Chip文字颜色。<br/>默认值：$r('sys.color.ohos_id_color_text_primary')<br/>为undefined时，fontColor走默认值。 |
| selectedFontColor       | [ResourceColor](ts-types.md#resourcecolor)                   | 否   | 是   | Chip激活时的文字颜色。<br/>默认值：$r('sys.color.ohos_id_color_text_primary_contrary')<br/>为undefined时，selectedFontColor走默认值。 |
| selectedBackgroundColor | [ResourceColor](ts-types.md#resourcecolor)                   | 否   | 是   | Chip激活时的背景颜色。<br/>默认值：$r('sys.color.ohos_id_color_emphasize')<br/>为undefined时，selectedBackgroundColor走默认值。 |

> **说明：**
>
> 1. 操作块的大小有两种类型，一种是ChipSize，提供NORMAL和SMALL两种尺寸供选择；另一种是SizeOptions。
>
> 2. backgroundColor、selectedBackgroundColor传入undefined时，显示默认背景颜色，传入非法值时，背景色透明。

## ChipGroupSpaceOptions

ChipGroupSpaceOptions 定义了ChipGroup左右内边距，以及Chip与Chip之间的间距。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称       | 类型            | 只读 | 可选 | 说明                                             |
| ---------- | -------------- | ---- | ------------------------------------------------ | ------------------------------------------------ |
| itemSpace | ArkTS-Dyn: string \| number <br/> ArkTS-Sta: string \| double  | 否  | 是  | Chip与Chip之间的间距（不支持百分比）。<br/>取值范围：<br/>number类型: ≥ 0 的数值（如：0、8、16、24.5）。<br/>string类型: 单位为fp\|vp\|px\|lpx且数值部分 ≥ 0 的字符串（如："8vp"、"16fp"、"12px"、"10lpx"）。<br/>double类型: ≥ 0 的数值（如：0、8、16、24.5）。 <br/>不支持: 负数、百分比单位、无效字符串格式。 <br/>默认值：8<br/>单位：vp<br/>为undefined时，itemSpace采取默认值。 |
| startSpace | [Length](ts-types.md#length)         | 否  | 是  | 左侧内边距（不支持百分比）。<br/>默认值：16<br/>单位：vp<br/>为undefined时，startSpace取默认值。           |
| endSpace   | [Length](ts-types.md#length)         | 否  | 是  | 右侧内边距（不支持百分比）。<br/>默认值：16<br/>单位：vp<br/>如果为undefined，则使用默认值。 |

## ChipGroupPaddingOptions

ChipGroupPaddingOptions定义了ChipGroup的上下内边距，用于控制其整体高度。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称   | 类型            | 只读 | 可选 | 说明                                                      |
| ------ | -------------- | ---- | ------------------------------------------------            | ------------------------------------------------            |
| top    | [Length](ts-types.md#length)         | 否  | 否  | ChipGroup的上方内边距（不支持百分比）。 单位：vp<br/> 默认值：14<br/>为undefined时，top取默认值。     |
| bottom | [Length](ts-types.md#length)         | 否  | 否  | ChipGroup的下方内边距（不支持百分比）。 单位：vp<br/> 默认值：14<br/>为undefined时，bottom取默认值。     |

## SuffixImageIconOptions<sup>14+</sup>

后缀图标选项的类型。

继承自[IconOptions](#iconoptions)。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | --- | ---- | ---- |
| action | [VoidCallback](ts-types.md#voidcallback12) | 否 | 是 | 后缀图标响应事件。<br>值为undefined时，无后缀图标响应事件。 |
| accessibilityText | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 后缀图标的无障碍文本属性。用于为用户进一步说明后缀图标，开发人员可为后缀图标的该属性设置相对较详细的解释文本，帮助用户理解将要执行的操作。如帮助用户理解将要执行的操作可能导致什么后果，尤其是当这些后果无法从后缀图标本身属性与无障碍文本中了解到时。若后缀图标既拥有文本属性又拥有无障碍说明属性，则后缀图标被选中时，先播报后缀图标的文本属性，再播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。 |
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 后缀图标的无障碍描述。此描述用于向用户详细解释后缀图标，开发人员应为后缀图标的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从后缀图标的属性和无障碍文本中直接获知时。如果后缀图标同时具备文本属性和无障碍说明属性，当后缀图标被选中时，系统将首先播报后缀图标的文本属性，随后播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。 |
| accessibilityLevel | string | 否 | 是 | 后缀图标无障碍重要性。用于控制后缀图标是否可被无障碍辅助服务所识别。<br>支持的值为:<br>"auto"：后缀图标存在action时转化为“yes”，不存在action时，转化为“no”。<br>"yes"：后缀图标可被无障碍辅助服务所识别。<br>"no"：后缀图标不可被无障碍辅助服务所识别。<br>"no-hide-descendants"：后缀图标及其所有子组件不可被无障碍辅助服务所识别。<br>默认值："auto"<br>值为undefined时，按默认值处理。 |

## SymbolItemOptions<sup>14+</sup>

ChipGroup的尾部图标选项类型。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | --- | ---- | ---- |
| symbol | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | 否 | 否 | 尾部图标的SymbolGlyphModifier配置对象，用于设置图标的显示样式、渲染模式等。|
| action | [VoidCallback](ts-types.md#voidcallback12) | 否 | 否 | 尾部图标响应事件。|
| accessibilityText | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 尾部图标的无障碍文本属性。用于为用户进一步说明尾部图标，开发人员可为尾部图标的该属性设置相对较详细的解释文本，帮助用户理解将要执行的操作。如帮助用户理解将要执行的操作可能导致什么后果，尤其是当这些后果无法从尾部图标本身属性与无障碍文本中了解到时。若尾部图标既拥有文本属性又拥有无障碍说明属性，则尾部图标被选中时，先播报尾部图标的文本属性，再播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。 |
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 尾部图标的无障碍描述。此描述用于向用户详细解释尾部图标，开发人员应为尾部图标的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从尾部图标的属性和无障碍文本中直接获知时。如果尾部图标同时具备文本属性和无障碍说明属性，当尾部图标被选中时，系统将首先播报尾部图标的文本属性，随后播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。 |
| accessibilityLevel | string | 否 | 是 | 尾部图标无障碍重要性。用于控制尾部图标是否可被无障碍辅助服务所识别。<br>支持的值为:<br>"auto"：尾部图标转化为“yes”。<br>"yes"：尾部图标可被无障碍辅助服务所识别。<br>"no"：尾部图标不可被无障碍辅助服务所识别。<br>"no-hide-descendants"：尾部图标及其所有子组件不可被无障碍辅助服务所识别。<br>默认值："auto"。<br>值为undefined时，按默认值处理。 |

## IconGroupSuffix

```typescript 
IconGroupSuffix({
  items: Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>,
  iconBackgroundSystemMaterial?: uiMaterial.Material
}) 
```

**装饰器类型：**@Component

### 属性

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称     | 类型                    | 必填 | 装饰器类型 | 说明                                                              |
| -------- | ---------------------- | ---- | ----------------------------------------------| ----------------------------------------------|
| items    | Array<[IconItemOptions](#iconitemoptions) \| [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) \| [ SymbolItemOptions](#symbolitemoptions14)> | 是   |  ArkTS-Dyn: @Require &nbsp;@Prop <br/> ArkTS-Sta: @Require &nbsp;@PropRef | 尾部区域显示的自定义项数组，支持IconItemOptions（Image图标）、SymbolGlyphModifier（Symbol图标）或SymbolItemOptions（Symbol图标配置）类型。<br>**原子化服务API：（仅ArkTS-Dyn）** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| iconBackgroundSystemMaterial | uiMaterial.[Material](../arkts-apis-uimaterial.md#material) | 否 | @Prop | 设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的[backgroundColor](ts-universal-attributes-background.md#backgroundcolor)、[border](ts-universal-attributes-border.md#border)、[shadow](ts-universal-attributes-image-effect.md#shadow)视觉属性。<br>默认值：undefined<br>值为undefined时，不应用材质样式。<br>**原子化服务API：** 从API version 26.0.0开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 26.0.0<br>**ArkTS-Sta起始版本：** 26.0.0 |


> **说明：**
>
> 传参SymbolGlyphModifier时，不支持使用symbolEffect修改动效类型和[effectStrategy](./ts-basic-components-symbolGlyph.md#effectstrategy)设置动效。
>

### build<sup>23+</sup>

build(): void

build函数用于构造ChipGroup高级组件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**装饰器类型：** [\@Builder](../../../ui/state-management/arkts-builder.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**ArkTS-Sta起始版本：** 23

## IconItemOptions

定义了尾部builder接口，针对背板大小及颜色设置限制。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称     | 类型                            | 只读 | 可选 | 说明                                    |
| -------- | --------------                 | ---- | ------------------------------           | ------------------------------           |
| icon     | [IconOptions](#iconoptions)    | 否  | 否  | 自定义Builder icon。<br/>Chip大小是ChipSize.SMALL时，suffix默认值：{width: 16,height: 16}。<br/>Chip大小是ChipSize.NORMAL时，suffix默认值：{width: 24,height: 24}。</br> 如果想动态修改size，那么必须在引入[IconGroupSuffix](#icongroupsuffix)时，使用[SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier)类型。 <br>值为undefined时，按默认值处理。<br> **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 12 <br/> **ArkTS-Sta起始版本：** 23 |
| action   | ArkTS-Dyn: Callback\<void> <br/> ArkTS-Sta: [VoidCallback](ts-types.md#voidcallback12)       | 否  | 否  | 自定义Builder items的回调，尾部图标被点击时触发。<br/>为undefined时，表示解绑事件。<br> **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 <br/>**ArkTS-Dyn起始版本：** 12 <br/> **ArkTS-Sta起始版本：** 23           |
| accessibilityText<sup>14+</sup> | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 尾部图标无障碍文本属性。用于为用户进一步说明尾部图标，开发人员可为尾部图标的该属性设置相对较详细的解释文本，帮助用户理解将要执行的操作。如帮助用户理解将要执行的操作可能导致什么后果，尤其是当这些后果无法从尾部图标本身属性与无障碍文本中了解到时。若尾部图标既拥有文本属性又拥有无障碍说明属性，则尾部图标被选中时，先播报尾部图标的文本属性，再播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 14 <br/> **ArkTS-Sta起始版本：** 23 |
| accessibilityDescription<sup>14+</sup> | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 尾部图标无障碍描述。此描述用于向用户详细解释尾部图标，开发人员应为尾部图标的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从尾部图标的属性和无障碍文本中直接获知时。如果尾部图标同时具备文本属性和无障碍说明属性，当尾部图标被选中时，系统将首先播报尾部图标的文本属性，随后播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 14 <br/> **ArkTS-Sta起始版本：** 23 |
| accessibilityLevel<sup>14+</sup> | string | 否 | 是 | 尾部图标无障碍重要性。用于控制尾部图标是否可被无障碍辅助服务所识别。<br>支持的值为:<br>"auto"：尾部图标转化为“yes”。<br>"yes"：尾部图标可被无障碍辅助服务所识别。<br>"no"：尾部图标不可被无障碍辅助服务所识别。<br>"no-hide-descendants"：尾部图标及其所有子组件不可被无障碍辅助服务所识别。<br>默认值："auto"<br>值为undefined时，按默认值处理。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 14 <br/> **ArkTS-Sta起始版本：** 23 |

## IconOptions

IconOptions定义图标的共通属性。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称 | 类型                                   | 只读 | 可选 | 说明                                                         |
| ---- | -------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| src  | [ResourceStr](ts-types.md#resourcestr) | 否   | 否   | 图标图片或图片地址引用请参考[Image](ts-basic-components-image.md#image-1)。 |
| size | [SizeOptions](ts-types.md#sizeoptions) | 否   | 是   | 图标大小，不支持百分比。<br>默认值：undefined                |

## LabelOptions

LabelOptions定义文本属性。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称 | 类型   | 只读 | 可选 | 说明     |
| ---- | ------ | ---- | -------- | -------- |
| text | string | 否  | 否  | 文本属性  |

## ChipGroupSuffixBuilder<sup>23+</sup>

type ChipGroupSuffixBuilder = () => void

用于构造chipGroup尾部图标的构造器。

**装饰器类型：** [@Builder](../../../ui/state-management/arkts-builder.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

## ChipItemLabelOptions<sup>23+</sup>

[ChipGroup](#chipgroup-1)定义标签选项。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 名称 | 类型                                   | 只读 | 可选 | 说明                                                         |
| ---- | -------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| text  | string | 否   | 否   | 文本内容。 |

## 示例

### 示例1（无最右侧的builder）

该示例实现了在没有最右侧builder时的效果。

ArkTS-Dyn示例：

```typescript
import { ChipSize, ChipGroup } from '@kit.ArkUI';

@Entry
@Preview
@Component
struct Index {
  @State selected_index: Array<number> = [0, 1, 2, 3, 4, 5, 6];

  build() {
    Column() {
      ChipGroup({
        // items内每个对象设置的都是每个Chip的特定属性。
        items: [
          {
            // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
            prefixIcon: { src: $r('app.media.icon') },
            label: { text: '操作块1' },
            suffixIcon: { src: $r('sys.media.ohos_ic_public_cut') },
            allowClose: false
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_copy') },
            label: { text: '操作块2' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: '操作块3' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块4' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: '操作块5' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块6' },
            allowClose: true
          },
        ],
        // 设置Chip的style属性。
        itemStyle: {
          size: ChipSize.SMALL,
          backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
          fontColor: $r('sys.color.ohos_id_color_text_primary'),
          selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
          selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
        },
        selectedIndexes: this.selected_index,
        multiple: false,
        chipGroupSpace: { itemSpace: 8, endSpace: 0 },
        chipGroupPadding: { top: 10, bottom: 10 },
        onChange: (activatedChipsIndex: Array<number>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
      })
    }
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, Text, Column, Component, Button, ClickEvent, Color, $r, ColumnOptions, FlexAlign, Direction, Builder, Row } from '@ohos.arkui.component'
import { State, Watch, PropRef } from '@ohos.arkui.stateManagement'
import hilog from '@ohos.hilog'
import { SymbolGlyphModifier } from '@ohos.arkui.modifier';
import { ChipGroup, IconGroupSuffix, IconItemOptions, ChipGroupItemOptions, ChipItemStyle, SuffixImageIconOptions } from '@ohos.arkui.advanced.ChipGroup';
import { ChipSize , ChipSymbolGlyphOptions} from '@ohos.arkui.advanced.Chip';

@Entry
@Component
struct Index {
  @State selected_index: Array<int> = [0, 1, 2, 3, 4, 5, 6];

  build() {
    Column() {
      ChipGroup({
        // items内每个对象设置的都是每个Chip的特定属性。
        items: [
          {
            // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
            prefixIcon: { src: $r('app.media.icon') },
            label: { text: '操作块1' },
            suffixImageIcon: { src: $r('sys.media.ohos_ic_public_cut') } as SuffixImageIconOptions,
            allowClose: false
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_copy') },
            label: { text: '操作块2' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: '操作块3' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块4' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: '操作块5' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块6' },
            allowClose: true
          },
        ],
        // 设置Chip的style属性。
        itemStyle: {
          size: ChipSize.SMALL,
          backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
          fontColor: $r('sys.color.ohos_id_color_text_primary'),
          selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
          selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
        },
        selectedIndexes: this.selected_index,
        multiple: false,
        chipGroupSpace: { itemSpace: 8, endSpace: 0 },
        chipGroupPadding: { top: 10, bottom: 10 },
        onChange: (activatedChipsIndex: Array<int>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
      })
    }
  }
}
```

![](figures/ChipGroupDemo1.png)

### 示例2（有最右侧的builder）

通过配置suffix实现最右侧的自定义组件效果。

ArkTS-Dyn示例：

```typescript
import { ChipSize, ChipGroup, IconGroupSuffix } from '@kit.ArkUI';

@Entry
@Preview
@Component
struct Index {
  @State selected_index: Array<number> = [0, 1, 2, 3, 4, 5, 6];
  @State selected_state: boolean = true;

  @LocalBuilder
  ChipGroupSuffix(): void {
    // 开发者通过引用IconGroupSuffix，实现组件最右侧的自定义组件效果。
    IconGroupSuffix({
      items: [{
        icon: { src: $r('sys.media.ohos_ic_public_search_filled'), size: { width: 36, height: 36 } },
        action: () => {
          if (this.selected_state == false) {
            this.selected_index = [0, 1, 2, 3, 4, 5, 6];
            this.selected_state = true;
          } else {
            this.selected_index = [];
            this.selected_state = false;
          }
        }
      }
      ]
    })
  }

  build() {
    Column() {
      ChipGroup({
        // items内每个对象设置的都是每个Chip的特定属性。
        items: [
          {
            // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
            prefixIcon: { src: $r('app.media.icon') },
            label: { text: '操作块1' },
            suffixIcon: { src: $r('sys.media.ohos_ic_public_cut') },
            allowClose: false
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_copy') },
            label: { text: '操作块2' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: '操作块3' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块4' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: '操作块5' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块6' },
            allowClose: true
          },
        ],
        // 设置Chip的style属性。
        itemStyle: {
          size: ChipSize.NORMAL,
          backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
          fontColor: $r('sys.color.ohos_id_color_text_primary'),
          selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
          selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
        },
        selectedIndexes: this.selected_index,
        multiple: true,
        chipGroupSpace: { itemSpace: 8, endSpace: 0 },
        chipGroupPadding: { top: 10, bottom: 10 },
        onChange: (activatedChipsIndex: Array<number>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
        // 自定义builder，在组件最右侧显示自定义的内容。
        suffix: this.ChipGroupSuffix
      })
    }
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, Text, Column, Component, Button, ClickEvent, Color, $r, ColumnOptions, FlexAlign, Direction, Builder, Row } from '@ohos.arkui.component'
import { State, Watch, PropRef } from '@ohos.arkui.stateManagement'
import hilog from '@ohos.hilog'
import { SymbolGlyphModifier } from '@ohos.arkui.modifier';
import { ChipGroup, IconGroupSuffix, IconItemOptions, ChipGroupItemOptions, ChipItemStyle, SuffixImageIconOptions } from '@ohos.arkui.advanced.ChipGroup';
import { ChipSize , ChipSymbolGlyphOptions} from '@ohos.arkui.advanced.Chip';

@Entry
@Component
struct Index {
  @State selected_index: Array<int> = [0, 1, 2, 3, 4, 5, 6];
  @State selected_state: boolean = true;

  @Builder
  ChipGroupSuffix(): void {
    // 开发者通过引用IconGroupSuffix，实现组件最右侧的自定义组件效果。
    IconGroupSuffix({
      items: [{
        icon: { src: $r('sys.media.ohos_ic_public_search_filled'), size: { width: 36, height: 36 } },
        action: () => {
          if (this.selected_state == false) {
            this.selected_index = [0, 1, 2, 3, 4, 5, 6];
            this.selected_state = true;
          } else {
            this.selected_index = [];
            this.selected_state = false;
          }
        }
      }
      ]
    })
  }

  build() {
    Column() {
      ChipGroup({
        // items内每个对象设置的都是每个Chip的特定属性。
        items: [
          {
            // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
            prefixIcon: { src: $r('app.media.icon') },
            label: { text: '操作块1' },
            suffixImageIcon: { src: $r('sys.media.ohos_ic_public_cut') } as SuffixImageIconOptions,
            allowClose: false
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_copy') },
            label: { text: '操作块2' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: '操作块3' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块4' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: '操作块5' },
            allowClose: true
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块6' },
            allowClose: true
          },
        ],
        // 设置Chip的style属性。
        itemStyle: {
          size: ChipSize.NORMAL,
          backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
          fontColor: $r('sys.color.ohos_id_color_text_primary'),
          selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
          selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
        },
        selectedIndexes: this.selected_index,
        multiple: true,
        chipGroupSpace: { itemSpace: 8, endSpace: 0 },
        chipGroupPadding: { top: 10, bottom: 10 },
        onChange: (activatedChipsIndex: Array<int>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
        // 自定义builder，在组件最右侧显示自定义的内容。
        suffix: this.ChipGroupSuffix
      })
    }
  }
}
```

![](figures/ChipGroupDemo2.png)

### 示例3（设置Symbol类型图标）
该示例实现了IconGroupSuffix和ChipGroup传入SymbolGlyph资源。

ArkTS-Dyn示例：

```typescript
import { ChipSize, ChipGroup, IconGroupSuffix, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry     
@Preview     
@Component     
struct Index {     
  @State selected_index: Array<number> = [0, 1, 2, 3, 4, 5, 6];     
  @State selected_state: boolean = true;     
  @State prefixModifierNormal: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_star'));     
  @State prefixModifierActivated: SymbolGlyphModifier =     
    new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Red]); 
  @State suffixModifierNormal: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_wifi'));     
  @State suffixModifierActivated: SymbolGlyphModifier =     
    new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')).fontColor([Color.Red]); 


  @LocalBuilder     
  ChipGroupSuffix(): void {     
    // 开发者通过引用IconGroupSuffix，实现组件最右侧的自定义组件效果。 
    IconGroupSuffix({     
      items: [     
        new SymbolGlyphModifier($r('sys.symbol.magnifyingglass'))     
          .onClick(() => {     
            if (this.selected_state == false) {     
              this.selected_index = [0, 1, 2, 3, 4, 5, 6];     
              this.selected_state = true;     
            } else {     
              this.selected_index = [];     
              this.selected_state = false;     
            }     
          })     
      ]     
    })     
  }     


  build() {     
    Column() {     
      ChipGroup({     
        // items内每个对象设置的都是每个Chip的特定属性。 
        items: [     
          {     
            prefixSymbol: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },     
            label: { text: '操作块1' },     
            suffixSymbol: { normal: this.suffixModifierNormal, activated: this.suffixModifierActivated },     
            allowClose: false,     
          },     
          {     
            prefixSymbol: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },     
            label: { text: '操作块2' },     
            allowClose: true,     
          },     
          {     
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },     
            label: { text: '操作块3' },     
            allowClose: true,     
          },     
          {     
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },     
            label: { text: '操作块4' },     
            allowClose: true,     
          },     
          {     
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },     
            label: { text: '操作块5' },     
            allowClose: true,     
          },     
          {     
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },     
            label: { text: '操作块6' },     
            allowClose: true,     
          },     
        ],     
        // 设置Chip的style属性。 
        itemStyle: {     
          size: ChipSize.NORMAL,     
          backgroundColor: $r('sys.color.ohos_id_color_button_normal'),     
          fontColor: $r('sys.color.ohos_id_color_text_primary'),     
          selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),     
          selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),     
        },     
        selectedIndexes: this.selected_index,     
        multiple: true,     
        chipGroupSpace: { itemSpace: 8, endSpace: 0 },     
        chipGroupPadding: { top: 10, bottom: 10 },     
        onChange: (activatedChipsIndex: Array<number>) => {     
          console.info('chips on clicked, activated index ' + activatedChipsIndex);     
        },     
        // 自定义builder，在组件最右侧显示自定义的内容。 
        suffix: this.ChipGroupSuffix     
      })     
    }     
  }     
}
```

ArkTS-Sta示例：

```typescript
import { Entry, Text, Column, Component, Button, ClickEvent, Color, $r, ColumnOptions, FlexAlign, Direction, Builder, Row } from '@ohos.arkui.component'
import { State, Watch, PropRef } from '@ohos.arkui.stateManagement'
import hilog from '@ohos.hilog'
import { SymbolGlyphModifier } from '@ohos.arkui.modifier';
import { ChipGroup, IconGroupSuffix, IconItemOptions, ChipGroupItemOptions, ChipItemStyle, SuffixImageIconOptions } from '@ohos.arkui.advanced.ChipGroup';
import { ChipSize , ChipSymbolGlyphOptions} from '@ohos.arkui.advanced.Chip';

@Entry
@Component
struct Index {
  @State selected_index: Array<int> = [0, 1, 2, 3, 4, 5, 6];
  @State selected_state: boolean = true;
  @State prefixModifierNormal: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_star'));
  @State prefixModifierActivated: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Red]);
  @State suffixModifierNormal: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_wifi'));
  @State suffixModifierActivated: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')).fontColor([Color.Red]);

  @Builder
  ChipGroupSuffix(): void {
    // 开发者通过引用IconGroupSuffix，实现组件最右侧的自定义组件效果。
    IconGroupSuffix({
      items: [
        new SymbolGlyphModifier($r('sys.symbol.magnifyingglass'))
          .onClick(() => {
            if (this.selected_state == false) {
              this.selected_index = [0, 1, 2, 3, 4, 5, 6];
              this.selected_state = true;
            } else {
              this.selected_index = [];
              this.selected_state = false;
            }
          })
      ]
    })
  }

  build() {
    Column() {
      ChipGroup({
        // items内每个对象设置的都是每个Chip的特定属性。 
        items: [
          {
            prefixSymbol: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },
            label: { text: '操作块1' },
            suffixSymbol: { normal: this.suffixModifierNormal, activated: this.suffixModifierActivated },
            allowClose: false,
          },
          {
            prefixSymbol: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },
            label: { text: '操作块2' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_clock') },
            label: { text: '操作块3' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块4' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_mirror') },
            label: { text: '操作块5' },
            allowClose: true,
          },
          {
            prefixIcon: { src: $r('sys.media.ohos_ic_public_cast_stream') },
            label: { text: '操作块6' },
            allowClose: true,
          },
        ],
        // 设置Chip的style属性。 
        itemStyle: {
          size: ChipSize.NORMAL,
          backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
          fontColor: $r('sys.color.ohos_id_color_text_primary'),
          selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
          selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
        },
        selectedIndexes: this.selected_index,
        multiple: true,
        chipGroupSpace: { itemSpace: 8, endSpace: 0 },
        chipGroupPadding: { top: 10, bottom: 10 },
        onChange: (activatedChipsIndex: Array<int>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
        // 自定义builder，在组件最右侧显示自定义的内容。
        suffix: this.ChipGroupSuffix
      })
    }
  }
}
```

![](figures/ChipGroupDemo3.png)

### 示例4（单选时无障碍朗读）

该示例实现ChipGroup在单选模式下，有后缀区域和无后缀区域的屏幕朗读功能，具体播报内容为accessibilityText属性中的内容。

ArkTS-Dyn示例：

```typescript
import { ChipGroup, IconGroupSuffix, SymbolGlyphModifier } from '@kit.ArkUI';

@Builder
function DefaultFunction(): void {
}

@Component
struct SectionGroup {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = DefaultFunction;

  build() {
    Column({ space: 4 }) {
      Text(this.title)
        .fontColor('#FF666666')
        .fontSize(12)
      Column({ space: 8 }) {
        this.content()
      }
    }
    .alignItems(HorizontalAlign.Start)
    .width('100%')
  }
}

@Component
struct SectionItem {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = DefaultFunction;

  build() {
    Column({ space: 12 }) {
      Text(this.title)
      this.content()
    }
    .backgroundColor('#FFFFFFFF')
    .borderRadius(12)
    .padding(12)
    .width('100%')
  }
}

@Entry
@Component
export struct ChipGroupExample2 {
  @LocalBuilder
  Suffix() {
    IconGroupSuffix({
      items: [
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        },
        {
          symbol: new SymbolGlyphModifier($r('sys.symbol.more')),
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        },
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: '更多',
          // accessibilityLevel属性设置为“no”时，accessibilityText属性和accessibilityDescription属性无效
          accessibilityDescription: '新手提醒',
          accessibilityLevel: 'no',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        }
      ]
    })
  }

  build() {
    NavDestination() {
      Scroll() {
        Column({ space: 12 }) {
          SectionGroup({ title: '可用的' }) {
            SectionItem({ title: '单选 无后缀区域' }) {
              ChipGroup({
                items: [
                  {
                    prefixIcon: {
                      src: $r('app.media.startIcon')
                    },
                    label: { text: '选项1' },
                    suffixImageIcon: {
                      src: $r('sys.media.save_button_picture'),
                      accessibilityText: '保存', // 播报“保存，按钮”
                      action: () => {
                        this.getUIContext().getPromptAction().showToast({
                          message: '后缀图标被点击！'
                        });
                      },
                    }
                  },
                  {
                    label: { text: '选项2' },
                    suffixSymbol: {
                      normal: new SymbolGlyphModifier($r('sys.symbol.save')),
                      activated: new SymbolGlyphModifier($r('sys.symbol.save'))
                    },
                    suffixSymbolOptions: {
                      normalAccessibility: {
                        accessibilityText: '保存' // 播报“保存，按钮”
                      },
                      action: () => {
                        this.getUIContext().getPromptAction().showToast({
                          message: '后缀图标被点击！'
                        });
                      }
                    }
                  },
                  {
                    label: { text: '选项3' },
                    suffixIcon: { src: $r('sys.media.save_button_picture'), }
                  },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
                ]
              })
            }

            SectionItem({ title: '单选 有后缀区域' }) {
              ChipGroup({
                items: [
                  { label: { text: '选项1' } },
                  { label: { text: '选项2' } },
                  { label: { text: '选项3' } },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
                ],
                suffix: this.Suffix,
              })
            }
          }
        }
      }
      .padding({
        top: 8,
        bottom: 8,
        left: 16,
        right: 16,
      })
    }
    .title('基础用法')
    .backgroundColor('#F1F3F5')
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, Text, Column, Component, Button, ClickEvent, Color, $r, ColumnOptions, FlexAlign, Direction, Builder, Row, ResourceStr, BuilderParam, HorizontalAlign, NavDestination, Scroll } from '@ohos.arkui.component'
import { State, Watch, PropRef, Require } from '@ohos.arkui.stateManagement'
import hilog from '@ohos.hilog'
import { SymbolGlyphModifier } from '@ohos.arkui.modifier';
import { ChipGroup, IconGroupSuffix, IconItemOptions, ChipGroupItemOptions, ChipItemStyle, SuffixImageIconOptions , SymbolItemOptions} from '@ohos.arkui.advanced.ChipGroup';
import { ChipSize , ChipSymbolGlyphOptions } from '@ohos.arkui.advanced.Chip';

@Builder
function DefaultFunction(): void {
}

@Component
struct SectionGroup {
  @PropRef
  @Require
  title: ResourceStr;
  @BuilderParam
  content: () => void = DefaultFunction;

  build() {
    Column({ space: 4 } as ColumnOptions) {
      Text(this.title)
        .fontColor('#FF666666')
        .fontSize(12)
      Column({ space: 8 } as ColumnOptions) {
        this.content()
      }
    }
    .alignItems(HorizontalAlign.Start)
    .width('100%')
  }
}

@Component
struct SectionItem {
  @PropRef
  @Require
  title: ResourceStr;
  @BuilderParam
  content: () => void = DefaultFunction;

  build() {
    Column({ space: 12 } as ColumnOptions) {
      Text(this.title)
      this.content()
    }
    .backgroundColor('#FFFFFFFF')
    .borderRadius(12)
    .padding(12)
    .width('100%')
  }
}

@Entry
@Component
export struct ChipGroupExample2 {
  @Builder
  Suffix() {
    IconGroupSuffix({
      items: [
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        },
        {
          symbol: new SymbolGlyphModifier($r('sys.symbol.more')),
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        } as SymbolItemOptions,
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: '更多',
          // accessibilityLevel属性设置为“no”时，accessibilityText属性和accessibilityDescription属性无效
          accessibilityDescription: '新手提醒',
          accessibilityLevel: 'no',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        }
      ]
    })
  }

  build() {
    NavDestination() {
      Scroll() {
        Column({ space: 12 } as ColumnOptions) {
          SectionGroup({ title: '可用的' }) {
            SectionItem({ title: '单选 无后缀区域' }) {
              ChipGroup({
                items: [
                  {
                    prefixIcon: {
                      src: $r('app.media.startIcon')
                    },
                    label: { text: '选项1' },
                    suffixImageIcon: {
                      src: $r('sys.media.save_button_picture'),
                      accessibilityText: '保存', // 播报“保存，按钮”
                      action: () => {
                        this.getUIContext().getPromptAction().showToast({
                          message: '后缀图标被点击！'
                        });
                      },
                    } as SuffixImageIconOptions
                  },
                  {
                    label: { text: '选项2' },
                    suffixSymbol: {
                      normal: new SymbolGlyphModifier($r('sys.symbol.save')),
                      activated: new SymbolGlyphModifier($r('sys.symbol.save'))
                    },
                    suffixSymbolOptions: {
                      normalAccessibility: {
                        accessibilityText: '保存' // 播报“保存，按钮”
                      },
                      action: () => {
                        this.getUIContext().getPromptAction().showToast({
                          message: '后缀图标被点击！'
                        });
                      }
                    }
                  },
                  {
                    label: { text: '选项3' },
                    suffixImageIcon: { src: $r('sys.media.save_button_picture') } as SuffixImageIconOptions
                  },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
                ]
              })
            }

            SectionItem({ title: '单选 有后缀区域' }) {
              ChipGroup({
                items: [
                  { label: { text: '选项1' } },
                  { label: { text: '选项2' } },
                  { label: { text: '选项3' } },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
                ],
                suffix: this.Suffix,
              })
            }
          }
        }
      }
      .padding({
        top: 8,
        bottom: 8,
        left: 16,
        right: 16,
      })
    }
    .title('基础用法')
    .backgroundColor('#F1F3F5')
  }
}
```

![](figures/ChipGroupDemo4.png)

### 示例5（多选时无障碍朗读）

该示例实现了ChipGroup在多选模式下，有后缀区域和无后缀区域的屏幕朗读功能，具体播报内容为accessibilityText属性中的内容。

ArkTS-Dyn示例：

```typescript
import { ChipGroup, IconGroupSuffix, SymbolGlyphModifier } from '@kit.ArkUI';

@Builder
function DefaultFunction(): void {
}

@Component
struct SectionGroup {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = DefaultFunction;

  build() {
    Column({ space: 4 }) {
      Text(this.title)
        .fontColor('#FF666666')
        .fontSize(12)
      Column({ space: 8 }) {
        this.content()
      }
    }
    .alignItems(HorizontalAlign.Start)
    .width('100%')
  }
}

@Component
struct SectionItem {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = DefaultFunction;

  build() {
    Column({ space: 12 }) {
      Text(this.title)
      this.content()
    }
    .backgroundColor('#FFFFFFFF')
    .borderRadius(12)
    .padding(12)
    .width('100%')
  }
}

@Entry
@Component
export struct ChipGroupExample2 {
  @LocalBuilder
  Suffix() {
    IconGroupSuffix({
      items: [
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        },
        {
          symbol: new SymbolGlyphModifier($r('sys.symbol.more')),
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        },
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: '更多',
          // accessibilityLevel属性设置为“no”时，accessibilityText属性和accessibilityDescription属性无效
          accessibilityDescription: '新手提醒',
          accessibilityLevel: 'no',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        }
      ]
    })
  }

  build() {
    NavDestination() {
      Scroll() {
        Column({ space: 12 }) {
          SectionGroup({ title: '可用的' }) {
            SectionItem({ title: '多选 无后缀区域' }) {
              ChipGroup({
                items: [
                  { label: { text: '选项1' } },
                  { label: { text: '选项2' } },
                  { label: { text: '选项3' } },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
                ],
                multiple: true
              })
            }

            SectionItem({ title: '多选 有后缀区域' }) {
              ChipGroup({
                items: [
                  { label: { text: '选项1' } },
                  { label: { text: '选项2' } },
                  { label: { text: '选项3' } },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
                ],
                suffix: this.Suffix,
                multiple: true,
              })
            }
          }
        }
      }
      .padding({
        top: 8,
        bottom: 8,
        left: 16,
        right: 16,
      })
    }
    .title('基础用法')
    .backgroundColor('#F1F3F5')
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, Text, Column, Component, Button, ClickEvent, Color, $r, ColumnOptions, FlexAlign, Direction, Builder, Row, ResourceStr, BuilderParam, HorizontalAlign, NavDestination, Scroll } from '@ohos.arkui.component'
import { State, Watch, PropRef, Require } from '@ohos.arkui.stateManagement'
import hilog from '@ohos.hilog'
import { SymbolGlyphModifier } from '@ohos.arkui.modifier';
import { ChipGroup, IconGroupSuffix, IconItemOptions, ChipGroupItemOptions, ChipItemStyle, SuffixImageIconOptions , SymbolItemOptions} from '@ohos.arkui.advanced.ChipGroup';
import { ChipSize , ChipSymbolGlyphOptions } from '@ohos.arkui.advanced.Chip';

@Builder
function DefaultFunction(): void {
}

@Component
struct SectionGroup {
  @PropRef
  @Require
  title: ResourceStr;
  @BuilderParam
  content: () => void = DefaultFunction;

  build() {
    Column({ space: 4 } as ColumnOptions) {
      Text(this.title)
        .fontColor('#FF666666')
        .fontSize(12)
      Column({ space: 8 } as ColumnOptions) {
        this.content()
      }
    }
    .alignItems(HorizontalAlign.Start)
    .width('100%')
  }
}

@Component
struct SectionItem {
  @PropRef
  @Require
  title: ResourceStr;
  @BuilderParam
  content: () => void = DefaultFunction;

  build() {
    Column({ space: 12 } as ColumnOptions) {
      Text(this.title)
      this.content()
    }
    .backgroundColor('#FFFFFFFF')
    .borderRadius(12)
    .padding(12)
    .width('100%')
  }
}

@Entry
@Component
export struct ChipGroupExample2 {
  @Builder
  Suffix() {
    IconGroupSuffix({
      items: [
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        },
        {
          symbol: new SymbolGlyphModifier($r('sys.symbol.more')),
          accessibilityText: '更多', // 播报“更多，按钮，新手提醒”
          accessibilityDescription: '新手提醒',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        } as SymbolItemOptions,
        {
          icon: { src: $r('sys.media.ohos_ic_public_more'), },
          accessibilityText: '更多',
          // accessibilityLevel属性设置为“no”时，accessibilityText属性和accessibilityDescription属性无效
          accessibilityDescription: '新手提醒',
          accessibilityLevel: 'no',
          action: () => {
            this.getUIContext().getPromptAction().showToast({
              message: '更多按钮被点击！'
            });
          }
        }
      ]
    })
  }

  build() {
    NavDestination() {
      Scroll() {
        Column({ space: 12 } as ColumnOptions) {
          SectionGroup({ title: '可用的' }) {
            SectionItem({ title: '多选 无后缀区域' }) {
              ChipGroup({
                items: [
                  { label: { text: '选项1' } },
                  { label: { text: '选项2' } },
                  { label: { text: '选项3' } },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
                ],
                multiple: true
              })
            }

            SectionItem({ title: '多选 有后缀区域' }) {
              ChipGroup({
                items: [
                  { label: { text: '选项1' } },
                  { label: { text: '选项2' } },
                  { label: { text: '选项3' } },
                  { label: { text: '选项4' } },
                  { label: { text: '选项5' } },
                  { label: { text: '选项6' } },
                  { label: { text: '选项7' } },
                  { label: { text: '选项8' } },
                  { label: { text: '选项9' } },
                ],
                suffix: this.Suffix,
                multiple: true,
              })
            }
          }
        }
      }
      .padding({
        top: 8,
        bottom: 8,
        left: 16,
        right: 16,
      })
    }
    .title('基础用法')
    .backgroundColor('#F1F3F5')
  }
}
```

![](figures/ChipGroupDemo5.png)

### 示例6（设置系统材质样式）

该示例通过配置backgroundSystemMaterial和iconBackgroundSystemMaterial实现系统材质样式。

从API版本26.0.0开始，[ChipGroup](#chipgroup-1)新增backgroundSystemMaterial属性，[IconGroupSuffix](#icongroupsuffix)新增iconBackgroundSystemMaterial属性。

ArkTS-Dyn示例：

```typescript
import { ChipGroup, IconGroupSuffix, uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct ChipGroupMaterialExample {
  @State selectedIndexes: Array<number> = [0];

  @LocalBuilder
  suffix() {
    IconGroupSuffix({
      items: [{
        icon: {
          src: $r('sys.media.AI_phone'),
        },
        action: () => {
          this.getUIContext().getPromptAction().showToast({
            message: '后缀图标被点击'
          })
        }
      }],
      // 设置后缀图标的系统材质样式
      iconBackgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
        style: uiMaterial.ImmersiveStyle.ULTRA_THIN
      })
    })
  }

  build() {
    Column() {
      ChipGroup({
        items: [
          { label: { text: '选项1' } },
          { label: { text: '选项2' } },
          { label: { text: '选项3' } },
          { label: { text: '选项4' } },
          { label: { text: '选项5' } },
          { label: { text: '选项6' } },
        ],
        selectedIndexes: this.selectedIndexes,
        itemStyle: {
          // 设置透明的背景颜色，否则会和系统材质冲突
          backgroundColor: Color.Transparent,
        },
        // 设置ChipGroup的系统材质样式
        backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN
        }),
        onChange: (activatedChipsIndex: Array<number>) => {
          this.selectedIndexes = activatedChipsIndex;
        },
        suffix: () => {
          this.suffix()
        }
      })
    }
    .linearGradient({
      angle: 135, // 渐变角度，135度是从左上到右下
      colors: [
        ['#FF9A9E', 0.0], // 起始颜色及位置 (0.0 表示起点)
        ['#FECFEF', 0.5], // 中间颜色及位置
        ['#A18CD1', 1.0]  // 结束颜色及位置 (1.0 表示终点)
      ]
    })
    .padding(12)
    .width('100%')
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```typescript
'use static'

import {
  $r,
  Builder,
  ChipGroup,
  ChipGroupItemOptions,
  ChipItemLabelOptions,
  ChipItemStyle,
  Color,
  Column,
  ColumnOptions,
  Component,
  Entry,
  IconGroupSuffix,
  IconItemOptions,
  IconOptions,
  State,
  uiMaterial
} from '@kit.ArkUI';

@Entry
@Component
struct ChipGroupMaterialExample {
  @State selectedIndexes: Array<int> = [0];

  @Builder
  suffix() {
    IconGroupSuffix({
      items: [{
        icon: { src: $r('sys.media.ohos_ic_public_more') } as IconOptions,
        action: () => {
          this.getUIContext().getPromptAction().showToast({
            message: '后缀图标被点击'
          })
        }
      } as IconItemOptions],
      // 设置后缀图标的系统材质样式
      iconBackgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
        style: uiMaterial.ImmersiveStyle.ULTRA_THIN
      })
    })
  }

  build() {
    Column({ space: 10 } as ColumnOptions) {
      ChipGroup({
        items: [
          { label: { text: '选项1' } as ChipItemLabelOptions } as ChipGroupItemOptions,
          { label: { text: '选项2' } as ChipItemLabelOptions } as ChipGroupItemOptions,
          { label: { text: '选项3' } as ChipItemLabelOptions } as ChipGroupItemOptions,
          { label: { text: '选项4' } as ChipItemLabelOptions } as ChipGroupItemOptions,
          { label: { text: '选项5' } as ChipItemLabelOptions } as ChipGroupItemOptions,
          { label: { text: '选项6' } as ChipItemLabelOptions } as ChipGroupItemOptions,
        ],
        selectedIndexes: this.selectedIndexes,
        itemStyle: {
          // 设置透明的背景颜色，否则会和系统材质冲突
          backgroundColor: Color.Transparent,
        } as ChipItemStyle,
        // 设置ChipGroup的系统材质样式
        backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN
        }),
        onChange: (activatedChipsIndex: Array<int>) => {
          this.selectedIndexes = activatedChipsIndex;
        },
        suffix: () => {
          this.suffix()
        }
      })
    }
    .linearGradient({
      angle: 135, // 渐变角度，135度是从左上到右下
      colors: [
        ['#FF9A9E', 0.0], // 起始颜色及位置 (0.0 表示起点)
        ['#FECFEF', 0.5], // 中间颜色及位置
        ['#A18CD1', 1.0]  // 结束颜色及位置 (1.0 表示终点)
      ]
    })
    .padding(12)
    .width('100%')
    .height('100%')
  }
}
```

![](figures/zh-cn_chip-group_material.png)
