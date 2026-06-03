# MenuItem
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Armstrong15-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

用来展示菜单中具体的菜单选项。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 该组件从API版本26.0.0开始支持[WithTheme](./ts-container-with-theme.md)。

## 子组件

无

## 接口

MenuItem(value?: MenuItemOptions | CustomBuilder)

构造菜单选项。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型      | 必填 | 说明      |
| -------- | -------------- | ---- | ------------------------ |
| value  | [MenuItemOptions](#menuitemoptions对象说明)&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | 否   | 包含设置MenuItem的各项信息。 如果不传该参数，则创建空的MenuItem对象。 |

## MenuItemOptions对象说明

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 类型                                        | 只读 | 可选 | 说明                             |
| --------- | ------------------------------------------- | ---- | ---- | -------------------------------------- |
| startIcon | [ResourceStr](ts-types.md#resourcestr)      | 否   | 是   | MenuItem的起始图标。不支持Symbol图标。使用Symbol图标时，须使用symbolStartIcon。 <br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。<br/> **ArkTS-Dyn起始版本：** 9 <br/> **ArkTS-Sta起始版本：** 23      |
| content   | [ResourceStr](ts-types.md#resourcestr)      | 否   | 是   | MenuItem的内容。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。<br/> **ArkTS-Dyn起始版本：** 9 <br/> **ArkTS-Sta起始版本：** 23  |
| endIcon   | [ResourceStr](ts-types.md#resourcestr)      | 否   | 是   | MenuItem的末尾图标。不支持Symbol图标。使用Symbol图标时，须使用symbolEndIcon。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。<br/> **ArkTS-Dyn起始版本：** 9 <br/> **ArkTS-Sta起始版本：** 23 |
| labelInfo | [ResourceStr](ts-types.md#resourcestr)      | 否   | 是   | MenuItem结束的标签信息，如快捷方式Ctrl+C等。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。<br/> **ArkTS-Dyn起始版本：** 9 <br/> **ArkTS-Sta起始版本：** 23  |
| builder   | [CustomBuilder](ts-types.md#custombuilder8) | 否   | 是   | 用于构建二级菜单。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。<br/> **ArkTS-Dyn起始版本：** 9 <br/> **ArkTS-Sta起始版本：** 23                      |
| symbolStartIcon<sup>12+</sup>   | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md) | 否   | 是   | MenuItem起始的Symbol图标。配置该项时，原先startIcon图标不显示。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br/> **ArkTS-Dyn起始版本：** 12 <br/> **ArkTS-Sta起始版本：** 23|
| symbolEndIcon<sup>12+</sup>   | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md)| 否   | 是   | MenuItem末尾的Symbol图标。配置该项时，原先endIcon图标不显示。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br/> **ArkTS-Dyn起始版本：** 12 <br/> **ArkTS-Sta起始版本：** 23|


## 属性

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性：

### selected

ArkTS-Dyn: selected(value: boolean)

ArkTS-Sta: selected(value: boolean | undefined | Bindable\<boolean\>)

设置菜单项是否选中。

从API version 10开始，该参数支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | ArkTS-Dyn: boolean<br/>ArkTS-Sta: boolean \| undefined \| Bindable\<boolean\> | 是   | 菜单项是否选中。取值为undefined时，按默认值处理。<br/>true：菜单项被选中；false：菜单项不被选中。<br />默认值：false |

### selectIcon

ArkTS-Dyn: selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier)

ArkTS-Sta: selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier | undefined)

设置当菜单项被选中时，是否显示被选中的图标。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | ArkTS-Dyn: boolean&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr)<sup>10+</sup>\|&nbsp;[SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md)<sup>12+</sup> <br/>ArkTS-Sta: boolean&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr)\|&nbsp;[SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md) \| undefined | 是   | 菜单项被选中时，是否显示被选中的图标。取值为undefined时，按默认值处理。<br/>true：显示默认的对勾图标；false：不显示图标。<br/>ResourceStr：显示指定的图标。<br/>SymbolGlyphModifier：显示指定的HMSymbol图标。<br/>默认值：false |

### contentFont<sup>10+</sup>

ArkTS-Dyn: contentFont(value: Font)

ArkTS-Sta: contentFont(value: Font | undefined)

设置菜单项中内容信息的字体样式。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                     | 必填 | 说明                         |
| ------ | ------------------------ | ---- | ---------------------------- |
| value  | ArkTS-Dyn: [Font](ts-types.md#font) <br/>ArkTS-Sta: [Font](ts-types.md#font) \| undefined  | 是   | 菜单项中内容信息的字体样式。取值为undefined时，按各属性的默认值处理。 |

### contentFontColor<sup>10+</sup>

ArkTS-Dyn: contentFontColor(value: ResourceColor)

ArkTS-Sta: contentFontColor(value: ResourceColor | undefined)

设置菜单项中内容信息的字体颜色。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                       | 必填 | 说明                         |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| value  | ArkTS-Dyn: [ResourceColor](ts-types.md#resourcecolor) <br/>ArkTS-Sta: [ResourceColor](ts-types.md#resourcecolor) \| undefined | 是   | 菜单项中内容信息的字体颜色。取值为undefined时，按默认值处理。<br />默认值：'#E5000000' |

### labelFont<sup>10+</sup>

ArkTS-Dyn: labelFont(value: Font)

ArkTS-Sta: labelFont(value: Font | undefined)

设置菜单项中标签信息的字体样式。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                     | 必填 | 说明                         |
| ------ | ------------------------ | ---- | ---------------------------- |
| value  | ArkTS-Dyn: [Font](ts-types.md#font) <br/>ArkTS-Sta: [Font](ts-types.md#font) \| undefined | 是   | 菜单项中标签信息的字体样式。取值为undefined时，按各属性的默认值处理。 |

### labelFontColor<sup>10+</sup>

ArkTS-Dyn: labelFontColor(value: ResourceColor)

ArkTS-Sta: labelFontColor(value: ResourceColor | undefined)

设置菜单项中标签信息的字体颜色。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                       | 必填 | 说明                         |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| value  | ArkTS-Dyn: [ResourceColor](ts-types.md#resourcecolor) <br/>ArkTS-Sta: [ResourceColor](ts-types.md#resourcecolor) \| undefined| 是   | 菜单项中标签信息的字体颜色。取值为undefined时，按默认值处理。<br />默认值：'#99000000' |

### attributeModifier<sup>23+</sup>

attributeModifier(modifier: AttributeModifier\<MenuItemAttribute\> | AttributeModifier\<CommonMethod\> | undefined)

设置MenuItem组件的属性修改器。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                                                                              | 必填 | 说明                       |
| --------- | ------------------------------------------------------------------------------------------------- | ---- | -------------------------- |
| modifier  | [AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)\<[MenuItemAttribute](#menuitemattribute)\>&nbsp;\|&nbsp;[AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)\<CommonMethod\>&nbsp;\|&nbsp;undefined | 是   | MenuItem组件的属性修改器。取值为undefined时，则不使用属性修改器。<br/>CommonMethod：[通用属性](./ts-component-general-attributes.md) |

## 事件

### onChange

ArkTS-Dyn: onChange(callback: (selected: boolean) => void)

ArkTS-Sta: onChange(callback: ((selected: boolean) => void) | undefined)

当选中状态发生变化时，触发该回调。只有手动触发且MenuItem状态改变时才会触发onChange回调。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型    | 必填 | 说明                                                         |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: (selected: boolean) => void<br/>ArkTS-Sta: ((selected: boolean) => void) \| undefined | 是   | 选中状态发生变化时，触发该回调。<br />true：未选中切换为选中；false：选中切换为未选中。<br/>ArkTS-Sta：当callback的值为undefined时，不使用回调函数。 |

## MenuItemAttribute

MenuItem组件的属性接口，用于配置MenuItem的各项属性。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 示例

详见[Menu组件示例](ts-basic-components-menu.md#示例)。
