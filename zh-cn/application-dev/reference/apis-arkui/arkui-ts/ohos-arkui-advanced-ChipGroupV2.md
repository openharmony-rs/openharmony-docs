# ChipGroupV2
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @youzhi92-->
<!--Designer: @youzhi92-->
<!--Tester: @TerryTsao-->
<!--Adviser: @Brilliantry_Rui-->

ChipGroupV2组件提供操作块群组，用于文件或资源内容的分类等场景。

该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于[状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组件层级。借助状态管理（V2），开发者可以更灵活地控制组件的数据和状态，实现更高效的用户界面刷新。

> **说明：**
>
> 本模块接口仅可在Stage模型下使用。
>

**起始版本：** 26.0.0

## 导入模块

```ts
import { ChipV2Size, ChipGroupV2 } from '@kit.ArkUI';
```

## 子组件

无

## ChipGroupV2

```ts
ChipGroupV2({
  items: ChipGroupV2Items,
  $items?: Callback<ChipGroupV2Items>,
  itemStyle?: ChipGroupV2ItemStyle,
  selectedIndexes?: Array<number>,
  $selectedIndexes?: Callback<Array<number>>,
  multiple?: boolean,
  chipGroupSpace?: ChipGroupV2Space,
  chipGroupPadding?: ChipGroupV2Padding,
  onChange?: Callback<Array<number>>,
  suffix?: Callback<void>
})
```

### 属性

**起始版本：** 26.0.0

**装饰器类型：** @ComponentV2

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称            | 类型                                            | 必填 | 装饰器类型 | 说明                                                                                     |
| --------------- | ----------------------------------------------- | ---- | ------------------------------------------------------------                             | ------------------------------------------------------------                             |
| items           | [ChipGroupV2Items](#chipgroupv2items) | 是   | @Require<br/>@Param | 每个ChipV2的特定属性，参考[ChipGroupV2ItemConfig](#chipgroupv2itemconfig)类型。<br/>值为undefined或空数组时，ChipGroupV2不渲染内部的[ChipV2](./ohos-arkui-advanced-ChipV2.md)。 |
| $items           | [Callback](ts-types.md#callback12)<[ChipGroupV2Items](#chipgroupv2items)> | 否   | @Event | ChipV2项的双向绑定回调方法。<br/>默认值：undefined，不触发回调。 |
| itemStyle       | [ChipGroupV2ItemStyle](#chipgroupv2itemstyle)                 | 否   | @Param | ChipV2的style属性，如颜色，大小等，参考[ChipGroupV2ItemStyle](#chipgroupv2itemstyle)类型。<br/>默认值：<br>{ size: ChipV2Size.NORMAL, backgroundColor: $r('sys.color.ohos_id_color_button_normal'), fontColor: $r('sys.color.ohos_id_color_text_primary'), selectedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'), selectedBackgroundColor: $r('sys.color.ohos_id_color_emphasize') }<br>值为undefined时，按默认值处理。<br>图标填充色（[fillColor](./ohos-arkui-advanced-ChipV2.md#chipv2imageiconconfig)和[activatedFillColor](./ohos-arkui-advanced-ChipV2.md#chipv2imageiconconfig)）的设置与字体颜色（[fontColor](#chipgroupv2itemstyleconfig)）保持一致。如果需要设置不同的颜色，可以在传入items时使用[prefixSymbolIcon](#chipgroupv2itemconfig)和[suffixSymbolIcon](#chipgroupv2itemconfig)。 |
| selectedIndexes | Array&lt;number&gt;            | 否   | @Param | 被选中ChipV2的索引。<br/>默认值：[0]<br>值为undefined时，按默认值处理。<br>当multiple等于false时，如果没有传入selectedIndexes，默认是第一个ChipV2被选中，如果传入的selectedIndexes有多个元素时，默认第一个索引的ChipV2被选中。  |
| $selectedIndexes | [Callback](ts-types.md#callback12)&lt;Array&lt;number&gt;&gt;                             |否   | @Event | 被选中ChipV2索引的双向绑定回调方法。<br/>默认值：undefined，不触发回调。  |
| multiple        | boolean                                         | 否   | @Param | 是否选中多个ChipV2。<br/>true：支持多个ChipV2选中；false：仅支持单个ChipV2选中。<br/>默认值：false<br>值为undefined时，按默认值处理。 |
| chipGroupSpace  | [ChipGroupV2Space](#chipgroupv2space) | 否   | @Param | 左右内边距及ChipV2之间间距。参考[ChipGroupV2Space](#chipgroupv2space)类型。<br/>默认值：{ itemSpace: 8, startSpace: 16, endSpace: 16 }<br>单位：vp<br/>值为undefined时，按默认值处理。 |
| chipGroupPadding  | [ChipGroupV2Padding](#chipgroupv2padding) | 否   | @Param | 设置ChipGroupV2的上下内边距，以控制整体高度。类型为[ChipGroupV2Padding](#chipgroupv2padding)。<br/>默认值：{ top: 14, bottom: 14 }<br>单位：vp<br/>值为undefined时，按默认值处理。 |
| onChange        | [Callback](ts-types.md#callback12)\<Array\<number>>  | 否   | @Event  | ChipV2状态改变时的回调方法。<br/>默认值：undefined，不触发事件。                                                              |
| suffix          | [Callback](ts-types.md#callback12)\<void\>                                        | 否   | @BuilderParam | 支持开发者自定义builder，如需在组件最右侧显示自定义内容可配置suffix属性，使用属性suffix需引用[ChipGroupV2IconGroupSuffix](#chipgroupv2icongroupsuffix)接口。<br/>默认值：undefined，不在最右侧显示自定义内容。 |

### build

build(): void

build函数用于构造ChipGroupV2高级组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

## ChipGroupV2Item

ChipGroupV2Item定义了芯片组中单个芯片项。

### 属性

**起始版本：** 26.0.0

**装饰器类型：** @ObservedV2

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| prefixIcon | [ChipV2PrefixImageIcon](ohos-arkui-advanced-ChipV2.md#chipv2prefiximageicon) | 否 | 是 | 前缀图标属性。<br>默认值：没有前缀Image图标。<br>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| prefixSymbolIcon | [ChipV2PrefixSymbolIcon](ohos-arkui-advanced-ChipV2.md#chipv2prefixsymbolicon) | 否 | 是 | 前缀Symbol图标属性。<br>默认值：没有前缀Symbol图标。<br>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| label | [ChipV2Label](ohos-arkui-advanced-ChipV2.md#chipv2label) | 否 | 否 | ChipV2文本属性。<br>**装饰器类型：** @Trace |
| suffixIcon | [ChipV2SuffixImageIcon](ohos-arkui-advanced-ChipV2.md#chipv2suffiximageicon) | 否 | 是 | 后缀图标属性。<br>默认值：不显示后缀Image图标。<br>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| suffixSymbolIcon | [ChipV2SuffixSymbolIcon](ohos-arkui-advanced-ChipV2.md#chipv2suffixsymbolicon) | 否 | 是 | 后缀Symbol图标属性。<br>默认值：不显示后缀Symbol图标。<br>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| allowClose | boolean | 否 | 是 | 删除图标是否显示。当传入suffixIcon参数时，allowClose不生效；未传入suffixIcon参数时，allowClose决定是否显示移除图标。<br>true表示删除图标显示，false表示删除图标不显示。<br/>默认值：false<br>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| closeIcon | [ChipV2CloseConfig](ohos-arkui-advanced-ChipV2.md#chipv2closeconfig) | 否 | 是 | 关闭图标的配置，包括无障碍属性配置。<br>默认值：<br>- 尺寸默认值：size为ChipV2Size.SMALL时，默认值为`$r('sys.float.chip_small_font_size')`；其他情况默认值为`$r('sys.float.chip_normal_font_size')`。<br>- 无障碍默认值：无无障碍描述。<br>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 无障碍描述。此描述用于向用户详细解释当前组件，开发人员应为组件的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的结果。特别是当这些结果无法仅从组件的属性和无障碍文本中直接获知时。如果组件同时具备文本属性和无障碍说明属性，当组件被选中时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| accessibilityLevel | string | 否 | 是 | 无障碍重要性。用于控制组件是否可被无障碍辅助服务所识别。<br>支持的值为：<br>"auto"：当前组件会转化为"yes"。<br>"yes"：当前组件可被无障碍辅助服务所识别。<br>"no"：当前组件不可被无障碍辅助服务所识别。<br>"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。<br>默认值："auto"<br>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |

### constructor

constructor(config: ChipGroupV2ItemConfig)

ChipGroupV2Item的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| config | [ChipGroupV2ItemConfig](#chipgroupv2itemconfig) | 是 | 芯片组项配置。 |

## ChipGroupV2ItemConfig

ChipGroupV2ItemConfig定义每个ChipV2的非通用属性配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称         | 类型                           | 只读 | 可选 | 说明                              |
| ----------   | ----------------------------- | ---- | ----------------------------------- | ----------------------------------- |
| prefixIcon   | [ChipV2PrefixImageIconConfig](ohos-arkui-advanced-ChipV2.md#chipv2prefiximageiconconfig)   | 否  | 是  | 前缀Image图标属性。<br>默认值：没有前缀Image图标。<br>值为undefined时，按默认值处理。 |
| prefixSymbolIcon | [ChipV2PrefixSymbolIconConfig](ohos-arkui-advanced-ChipV2.md#chipv2prefixsymboliconconfig) | 否  | 是  | 前缀Symbol图标属性。<br>默认值：没有前缀Symbol图标。<br>值为undefined时，按默认值处理。 |
| label        | [ChipV2LabelConfig](ohos-arkui-advanced-ChipV2.md#chipv2labelconfig) | 否  | 否  | 文本属性。                            |
| suffixIcon   | [ChipV2SuffixImageIconConfig](ohos-arkui-advanced-ChipV2.md#chipv2suffiximageiconconfig) | 否 | 是 | 后缀Image图标属性。<br>默认值：不显示后缀Image图标。<br>值为undefined时，按默认值处理。 |
| suffixSymbolIcon | [ChipV2SuffixSymbolIconConfig](ohos-arkui-advanced-ChipV2.md#chipv2suffixsymboliconconfig) | 否 | 是 | 后缀Symbol图标属性。<br>默认值：不显示后缀Symbol图标。<br>值为undefined时，按默认值处理。 |
| allowClose   | boolean                       | 否  | 是  | 删除图标是否显示。<br>true表示删除图标显示，false表示删除图标不显示。<br/>默认值：false<br>值为undefined时，按默认值处理。 |
| closeIcon | [ChipV2CloseConfig](ohos-arkui-advanced-ChipV2.md#chipv2closeconfig) | 否 | 是 | 关闭图标的配置，包括无障碍属性配置。<br>默认值：<br>- 尺寸默认值：size为ChipV2Size.SMALL时，默认值为`$r('sys.float.chip_small_font_size')`；其他情况默认值为`$r('sys.float.chip_normal_font_size')`。<br>- 无障碍默认值：无无障碍描述。<br>值为undefined时，按默认值处理。 |
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | ChipGroupV2中ChipV2项的无障碍描述。此描述用于向用户详细解释ChipGroupV2中ChipV2项，开发人员应为ChipGroupV2中ChipV2项的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的结果。特别是当这些结果无法仅从ChipGroupV2中ChipV2项的属性和无障碍文本中直接获知时。如果ChipGroupV2中ChipV2项同时具备文本属性和无障碍说明属性，当ChipGroupV2中ChipV2项被选中时，系统将首先播报ChipGroupV2中ChipV2项的文本属性，随后播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。 |
| accessibilityLevel | string | 否 | 是 | ChipGroupV2中ChipV2项无障碍重要性。用于控制ChipGroupV2中ChipV2项是否可被无障碍辅助服务所识别。<br>支持的值为：<br>"auto"：ChipGroupV2中ChipV2项会转换为"yes"。<br>"yes"：ChipGroupV2中ChipV2项可被无障碍辅助服务所识别。<br>"no"：ChipGroupV2中ChipV2项不可被无障碍辅助服务所识别。<br>"no-hide-descendants"：ChipGroupV2中ChipV2项及其所有子组件不可被无障碍辅助服务所识别。<br>默认值："auto"<br>值为undefined时，按默认值处理。 |

## ChipGroupV2Items

ChipGroupV2Items定义了芯片组项的数组类，继承自Array<[ChipGroupV2Item](#chipgroupv2item)>。

**起始版本：** 26.0.0

**装饰器类型：** @ObservedV2

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

### constructor

constructor(items: ChipGroupV2ItemConfig[])

ChipGroupV2Items的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| items | [ChipGroupV2ItemConfig](#chipgroupv2itemconfig)[] | 是 | 芯片组项配置数组。 |

## ChipGroupV2ItemStyle

ChipGroupV2ItemStyle定义了ChipV2的共通属性类。

### 属性

**起始版本：** 26.0.0

**装饰器类型：** @ObservedV2

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| size | [ChipV2Size](ohos-arkui-advanced-ChipV2.md#chipv2size) \| [SizeT](../js-apis-arkui-graphics.md#sizett12)<[LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)> | 否 | 是 | ChipV2尺寸。<br/>默认值：ChipV2Size.NORMAL<br/>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| backgroundColor | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | 否 | 是 | ChipV2背景颜色。<br/>默认值：$r('sys.color.ohos_id_color_button_normal')<br/>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| fontColor | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | 否 | 是 | ChipV2文字颜色。<br/>默认值：$r('sys.color.ohos_id_color_text_primary')<br/>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| selectedFontColor | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | 否 | 是 | ChipV2激活时的文字颜色。<br/>默认值：$r('sys.color.ohos_id_color_text_primary_contrary')<br/>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| selectedBackgroundColor | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | 否 | 是 | ChipV2激活时的背景颜色。<br/>默认值：$r('sys.color.ohos_id_color_emphasize')<br/>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| backgroundSystemMaterial | uiMaterial.[Material](../arkts-apis-uimaterial.md#material) | 否 | 是 | 设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](ts-universal-attributes-border.md#bordercolor)、边框宽度[borderWidth](ts-universal-attributes-border.md#borderwidth)、阴影[shadow](ts-universal-attributes-image-effect.md#shadow)效果、材质层滤镜效果[materialFilter](ts-universal-attributes-filter-effect.md#materialfilter23)。<br>默认值：undefined，不应用材质样式。<br>**装饰器类型：** @Trace |
| selectedBackgroundSystemMaterial | uiMaterial.[Material](../arkts-apis-uimaterial.md#material) | 否 | 是 | 设置组件选中状态下的系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](ts-universal-attributes-border.md#bordercolor)、边框宽度[borderWidth](ts-universal-attributes-border.md#borderwidth)、阴影[shadow](ts-universal-attributes-image-effect.md#shadow)效果、材质层滤镜效果[materialFilter](ts-universal-attributes-filter-effect.md#materialfilter23)。<br>默认值：undefined，不应用材质样式。<br>**装饰器类型：** @Trace |

### constructor

constructor(config: ChipGroupV2ItemStyleConfig)

ChipGroupV2ItemStyle的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| config | [ChipGroupV2ItemStyleConfig](#chipgroupv2itemstyleconfig) | 是 | 芯片组项样式配置。 |

## ChipGroupV2ItemStyleConfig

ChipGroupV2ItemStyleConfig定义了ChipV2的共通属性配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称                    | 类型                                                         | 只读 | 可选 | 说明                                                         |
| ----------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| size                    | [ChipV2Size](ohos-arkui-advanced-ChipV2.md#chipv2size) \| [SizeT](../js-apis-arkui-graphics.md#sizett12)<[LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)> | 否   | 是   | ChipV2尺寸，使用时需要从ChipV2组件引入ChipV2Size类型。<br/>默认值：ChipV2Size.NORMAL<br/>值为undefined时，按默认值处理。 |
| backgroundColor         | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)                   | 否   | 是   | ChipV2背景颜色。<br/>默认值：$r('sys.color.ohos_id_color_button_normal')<br/>值为undefined时，按默认值处理。 |
| fontColor               | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)                   | 否   | 是   | ChipV2文字颜色。<br/>默认值：$r('sys.color.ohos_id_color_text_primary')<br/>值为undefined时，按默认值处理。 |
| selectedFontColor       | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)                   | 否   | 是   | ChipV2激活时的文字颜色。<br/>默认值：$r('sys.color.ohos_id_color_text_primary_contrary')<br/>值为undefined时，按默认值处理。 |
| selectedBackgroundColor | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)                   | 否   | 是   | ChipV2激活时的背景颜色。<br/>默认值：$r('sys.color.ohos_id_color_emphasize')<br/>值为undefined时，按默认值处理。 |
| backgroundSystemMaterial | uiMaterial.[Material](../arkts-apis-uimaterial.md#material) | 否 | 是 | 设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](ts-universal-attributes-border.md#bordercolor)、边框宽度[borderWidth](ts-universal-attributes-border.md#borderwidth)、阴影[shadow](ts-universal-attributes-image-effect.md#shadow)效果、材质层滤镜效果[materialFilter](ts-universal-attributes-filter-effect.md#materialfilter23)。<br>默认值：undefined，不应用材质样式。 |
| selectedBackgroundSystemMaterial | uiMaterial.[Material](../arkts-apis-uimaterial.md#material) | 否 | 是 | 设置组件选中状态下的系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](ts-universal-attributes-border.md#bordercolor)、边框宽度[borderWidth](ts-universal-attributes-border.md#borderwidth)、阴影[shadow](ts-universal-attributes-image-effect.md#shadow)效果、材质层滤镜效果[materialFilter](ts-universal-attributes-filter-effect.md#materialfilter23)。<br>默认值：undefined，不应用材质样式。 |

## ChipGroupV2Space

ChipGroupV2Space定义了ChipGroupV2左右内边距，以及Chip与Chip之间的间距。

### 属性

**起始版本：** 26.0.0

**装饰器类型：** @ObservedV2

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| itemSpace | string \| number | 否 | 是 | ChipV2与ChipV2之间的间距（不支持百分比）。<br/>取值范围：<br/>- number类型：[0, +∞)，如0、8、16、24.5。<br/>- string类型：单位为fp\|vp\|px\|lpx且数值部分大于等于0的字符串，如"8vp"、"16fp"、"12px"、"10lpx"。<br/>- 不支持：负数、百分比单位、无效字符串格式。 <br/>默认值：8<br/>单位：vp<br/>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| startSpace | [Length](ts-types.md#length) | 否 | 是 | 左侧内边距（不支持百分比）。<br/>默认值：16<br/>单位：vp<br/>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| endSpace | [Length](ts-types.md#length) | 否 | 是 | 右侧内边距（不支持百分比）。<br/>默认值：16<br/>单位：vp<br/>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |

### constructor

constructor(config: ChipGroupV2SpaceConfig)

ChipGroupV2Space的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| config | [ChipGroupV2SpaceConfig](#chipgroupv2spaceconfig) | 是 | 芯片组间距配置。 |

## ChipGroupV2SpaceConfig

ChipGroupV2SpaceConfig定义了ChipGroupV2左右内边距，以及Chip与Chip之间的间距配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称       | 类型            | 只读 | 可选 | 说明                                             |
| ---------- | -------------- | ---- | ------------------------------------------------ | ------------------------------------------------ |
| itemSpace | string \| number  | 否  | 是  | ChipV2与ChipV2之间的间距（不支持百分比）。<br/>取值范围：<br/>- number类型：[0, +∞)，如0、8、16、24.5。<br/>- string类型：单位为fp\|vp\|px\|lpx且数值部分大于等于0的字符串，如"8vp"、"16fp"、"12px"、"10lpx"。<br/>- 不支持：负数、百分比单位、无效字符串格式。 <br/>默认值：8<br/>单位：vp<br/>值为undefined时，按默认值处理。 |
| startSpace | [Length](ts-types.md#length)         | 否  | 是  | 左侧内边距（不支持百分比）。<br/>默认值：16<br/>单位：vp<br/>值为undefined时，按默认值处理。           |
| endSpace   | [Length](ts-types.md#length)         | 否  | 是  | 右侧内边距（不支持百分比）。<br/>默认值：16<br/>单位：vp<br/>值为undefined时，按默认值处理。 |

## ChipGroupV2Padding

ChipGroupV2Padding定义了ChipGroupV2的上下内边距，用于控制其整体高度。

### 属性

**起始版本：** 26.0.0

**装饰器类型：** @ObservedV2

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| top | [Length](ts-types.md#length) | 否 | 否 | ChipGroupV2的上方内边距（不支持百分比）。<br/>默认值：14<br/> 单位：vp<br/>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |
| bottom | [Length](ts-types.md#length) | 否 | 否 | ChipGroupV2的下方内边距（不支持百分比）。<br/>默认值：14<br/> 单位：vp<br/>值为undefined时，按默认值处理。<br>**装饰器类型：** @Trace |

### constructor

constructor(config: ChipGroupV2PaddingConfig)

ChipGroupV2Padding的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| config | [ChipGroupV2PaddingConfig](#chipgroupv2paddingconfig) | 是 | 芯片组内边距配置。 |

## ChipGroupV2PaddingConfig

ChipGroupV2PaddingConfig定义了ChipGroupV2的上下内边距配置，用于控制其整体高度。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称   | 类型            | 只读 | 可选 | 说明                                                      |
| ------ | -------------- | ---- | ------------------------------------------------            | ------------------------------------------------            |
| top    | [Length](ts-types.md#length)         | 否  | 否  | ChipGroupV2的上方内边距（不支持百分比）。<br/>默认值：14<br/> 单位：vp<br/>值为undefined时，按默认值处理。 |
| bottom | [Length](ts-types.md#length)         | 否  | 否  | ChipGroupV2的下方内边距（不支持百分比）。<br/>默认值：14<br/> 单位：vp<br/>值为undefined时，按默认值处理。  |

## ChipGroupV2IconGroupSuffix

```typescript
ChipGroupV2IconGroupSuffix({
  items: Array<ChipGroupV2IconItemConfig | SymbolGlyphModifier | ChipGroupV2SymbolItemConfig>,
  iconBackgroundSystemMaterial?: uiMaterial.Material
})
```

### 属性

**起始版本：** 26.0.0

**装饰器类型：** @ComponentV2

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称                        | 类型                    | 必填 | 装饰器类型 | 说明                                                              |
| --------------------------- | ---------------------- | ---- | ----------------------------------------------| ----------------------------------------------|
| items                       | Array<[ChipGroupV2IconItemConfig](#chipgroupv2iconitemconfig) \| [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) \| [ChipGroupV2SymbolItemConfig](#chipgroupv2symbolitemconfig)> | 是   | @Require<br/>@Param | 尾部区域显示的自定义项数组，支持ChipGroupV2IconItemConfig（Image图标）、SymbolGlyphModifier（Symbol图标）或ChipGroupV2SymbolItemConfig（Symbol图标配置）类型。<br>传参SymbolGlyphModifier时，不支持使用symbolEffect修改动效类型和[effectStrategy](./ts-basic-components-symbolGlyph.md#effectstrategy)设置动效。|
| iconBackgroundSystemMaterial | uiMaterial.[Material](../arkts-apis-uimaterial.md#material) | 否 | @Param | 设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](ts-universal-attributes-border.md#bordercolor)、边框宽度[borderWidth](ts-universal-attributes-border.md#borderwidth)、阴影[shadow](ts-universal-attributes-image-effect.md#shadow)效果、材质层滤镜效果[materialFilter](ts-universal-attributes-filter-effect.md#materialfilter23)。<br>默认值：undefined，不应用材质样式。 |

### build

build(): void

build函数用于构造ChipGroupV2IconGroupSuffix组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

## ChipGroupV2IconItemConfig

ChipGroupV2IconItemConfig定义了尾部builder接口配置，针对背板大小及颜色设置限制。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称     | 类型                            | 只读 | 可选 | 说明                                    |
| -------- | --------------                 | ---- | ------------------------------           | ------------------------------           |
| icon     | [ChipV2ImageIconConfig](ohos-arkui-advanced-ChipV2.md#chipv2imageiconconfig)    | 否  | 否  | 自定义尾部图标。<br/>Chip大小是ChipV2Size.SMALL时，图标尺寸为：{ width: 16, height: 16 }。<br/>Chip大小是ChipV2Size.NORMAL时，图标尺寸为：{ width: 24, height: 24 }。</br> 如果想动态修改图标尺寸，那么必须在引入[ChipGroupV2IconGroupSuffix](#chipgroupv2icongroupsuffix)时，使用[SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier)类型。 |
| action   | [Callback](ts-types.md#callback12)\<void>        | 否  | 否  | 自定义尾部图标的响应事件。 |
| accessibilityText | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 尾部图标无障碍文本属性。用于为用户进一步说明尾部图标，开发人员可为尾部图标的该属性设置相对较详细的解释文本，帮助用户理解将要执行的操作。如帮助用户理解将要执行的操作可能导致什么后果，尤其是当这些后果无法从尾部图标本身属性与无障碍文本中了解到时。若尾部图标既拥有文本属性又拥有无障碍说明属性，则尾部图标被选中时，先播报尾部图标的文本属性，再播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。 |
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 尾部图标无障碍描述。此描述用于向用户详细解释尾部图标，开发人员应为尾部图标的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从尾部图标的属性和无障碍文本中直接获知时。如果尾部图标同时具备文本属性和无障碍说明属性，当尾部图标被选中时，系统将首先播报尾部图标的文本属性，随后播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。 |
| accessibilityLevel | string | 否 | 是 | 尾部图标无障碍重要性。用于控制尾部图标是否可被无障碍辅助服务所识别。<br>支持的值为：<br>"auto"：尾部图标转化为"yes"。<br>"yes"：尾部图标可被无障碍辅助服务所识别。<br>"no"：尾部图标不可被无障碍辅助服务所识别。<br>"no-hide-descendants"：尾部图标及其所有子组件不可被无障碍辅助服务所识别。<br>默认值："auto"<br>值为undefined时，按默认值处理。 |

## ChipGroupV2SymbolItemConfig

ChipGroupV2SymbolItemConfig定义了尾部Symbol图标的配置类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | --- | ---- | ---- |
| symbol | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | 否 | 否 | 尾部图标的SymbolGlyphModifier配置对象，用于设置图标的显示样式、渲染模式等。|
| action | [VoidCallback](ts-types.md#voidcallback12) | 否 | 否 | 尾部图标响应事件。|
| accessibilityText | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 尾部图标的无障碍文本属性。用于为用户进一步说明尾部图标，开发人员可为尾部图标的该属性设置相对较详细的解释文本，帮助用户理解将要执行的操作。如帮助用户理解将要执行的操作可能导致什么后果，尤其是当这些后果无法从尾部图标本身属性与无障碍文本中了解到时。若尾部图标既拥有文本属性又拥有无障碍说明属性，则尾部图标被选中时，先播报尾部图标的文本属性，再播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。|
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 尾部图标的无障碍描述。此描述用于向用户详细解释尾部图标，开发人员应为尾部图标的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从尾部图标的属性和无障碍文本中直接获知时。如果尾部图标同时具备文本属性和无障碍说明属性，当尾部图标被选中时，系统将首先播报尾部图标的文本属性，随后播报无障碍说明属性的内容。<br>默认值：空字符串。<br>值为undefined时，按默认值处理。|
| accessibilityLevel | string | 否 | 是 | 尾部图标无障碍重要性。用于控制尾部图标是否可被无障碍辅助服务所识别。<br>支持的值为：<br>"auto"：尾部图标转化为"yes"。<br>"yes"：尾部图标可被无障碍辅助服务所识别。<br>"no"：尾部图标不可被无障碍辅助服务所识别。<br>"no-hide-descendants"：尾部图标及其所有子组件不可被无障碍辅助服务所识别。<br>默认值："auto"。<br>值为undefined时，按默认值处理。 |

## 示例

### 示例1（ChipGroupV2无最右侧自定义组件）

该示例通过不设置[suffix](#属性)属性，实现了[ChipGroupV2](#chipgroupv2-1)没有最右侧自定义组件时的效果。

从API版本26.0.0开始，ChipGroupV2新增suffix属性。

```ts
import { ChipV2Size, ChipGroupV2, ChipGroupV2Items, ChipGroupV2ItemStyle, ChipGroupV2Space, ChipGroupV2Padding, ColorMetrics } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local selected_index: Array<number> = [0, 1, 2, 3, 4, 5, 6];

  build() {
    Column() {
      ChipGroupV2({
        // items内每个对象设置的都是每个ChipV2的特定属性。
        items: new ChipGroupV2Items([
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
        ]),
        // 设置ChipV2的style属性。
        itemStyle: new ChipGroupV2ItemStyle({
          size: ChipV2Size.SMALL,
          backgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_button_normal')),
          fontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary')),
          selectedBackgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_emphasize')),
          selectedFontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary_contrary')),
        }),
        selectedIndexes: this.selected_index,
        multiple: false,
        chipGroupSpace: new ChipGroupV2Space({ itemSpace: 8, endSpace: 0 }),
        chipGroupPadding: new ChipGroupV2Padding({ top: 10, bottom: 10 }),
        onChange: (activatedChipsIndex: Array<number>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
      })
    }
  }
}
```

![](figures/chipgroupv2_1.png)

### 示例2（ChipGroupV2设置最右侧自定义组件）

该示例通过设置[suffix](#属性)属性，实现了[ChipGroupV2](#chipgroupv2-1)最右侧的自定义组件效果。

从API版本26.0.0开始，ChipGroupV2新增suffix属性。

```ts
import { ChipV2Size, ChipGroupV2, ChipGroupV2Items, ChipGroupV2IconGroupSuffix, ChipGroupV2ItemStyle, ChipGroupV2Space, ChipGroupV2Padding, ColorMetrics, LengthMetrics } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local selected_index: Array<number> = [0, 1, 2, 3, 4, 5, 6];
  @Local selected_state: boolean = true;

  @Builder
  ChipGroupSuffix(): void {
    // 开发者通过引用ChipGroupV2IconGroupSuffix，实现组件最右侧的自定义组件效果。
    ChipGroupV2IconGroupSuffix({
      items: [{
        icon: { src: $r('sys.media.ohos_ic_public_search_filled'), size: { width: LengthMetrics.fp(36), height: LengthMetrics.fp(36) } },
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
      ChipGroupV2({
        // items内每个对象设置的都是每个ChipV2的特定属性。
        items: new ChipGroupV2Items([
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
        ]),
        // 设置ChipV2的style属性。
        itemStyle: new ChipGroupV2ItemStyle({
          size: ChipV2Size.NORMAL,
          backgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_button_normal')),
          fontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary')),
          selectedBackgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_emphasize')),
          selectedFontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary_contrary')),
        }),
        selectedIndexes: this.selected_index,
        multiple: true,
        chipGroupSpace: new ChipGroupV2Space({ itemSpace: 8, endSpace: 0 }),
        chipGroupPadding: new ChipGroupV2Padding({ top: 10, bottom: 10 }),
        onChange: (activatedChipsIndex: Array<number>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
        // ChipGroupV2最右侧显示的自定义组件。
        suffix: this.ChipGroupSuffix
      })
    }
  }
}
```

![](figures/chipgroupv2_2.png)

### 示例3（设置Symbol类型图标）

该示例通过[SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier)实现了[ChipGroupV2IconGroupSuffix](#chipgroupv2icongroupsuffix)和[ChipGroupV2](#chipgroupv2-1)设置Symbol类型图标。

从API版本26.0.0开始，新增ChipGroupV2IconGroupSuffix和ChipGroupV2。

```ts
import { ChipV2Size, ChipGroupV2, ChipGroupV2Items, ChipGroupV2IconGroupSuffix, SymbolGlyphModifier, ChipGroupV2ItemStyle, ChipGroupV2Space, ChipGroupV2Padding, ColorMetrics } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local selected_index: Array<number> = [0, 1, 2, 3, 4, 5, 6];
  @Local selected_state: boolean = true;
  @Local prefixModifierNormal: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_star'));
  @Local prefixModifierActivated: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Red]);
  @Local suffixModifierNormal: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_wifi'));
  @Local suffixModifierActivated: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')).fontColor([Color.Red]);

  @Builder
  ChipGroupSuffix(): void {
    // 开发者通过引用ChipGroupV2IconGroupSuffix，实现组件最右侧的自定义组件效果。
    ChipGroupV2IconGroupSuffix({
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
      ChipGroupV2({
        // items内每个对象设置的都是每个ChipV2的特定属性。
        items: new ChipGroupV2Items([
          {
            prefixSymbolIcon: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },
            label: { text: '操作块1' },
            suffixSymbolIcon: { normal: this.suffixModifierNormal, activated: this.suffixModifierActivated },
            allowClose: false,
          },
          {
            prefixSymbolIcon: { normal: this.prefixModifierNormal, activated: this.prefixModifierActivated },
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
        ]),
        // 设置ChipV2的style属性。
        itemStyle: new ChipGroupV2ItemStyle({
          size: ChipV2Size.NORMAL,
          backgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_button_normal')),
          fontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary')),
          selectedBackgroundColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_emphasize')),
          selectedFontColor: ColorMetrics.resourceColor($r('sys.color.ohos_id_color_text_primary_contrary')),
        }),
        selectedIndexes: this.selected_index,
        multiple: true,
        chipGroupSpace: new ChipGroupV2Space({ itemSpace: 8, endSpace: 0 }),
        chipGroupPadding: new ChipGroupV2Padding({ top: 10, bottom: 10 }),
        onChange: (activatedChipsIndex: Array<number>) => {
          console.info('chips on clicked, activated index ' + activatedChipsIndex);
        },
        // ChipGroupV2最右侧显示的自定义组件。
        suffix: this.ChipGroupSuffix
      })
    }
  }
}
```

![](figures/chipgroupv2_3.png)
