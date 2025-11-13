# MenuItem

用来展示菜单Menu中具体的item菜单项。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## 子组件

无

## 接口

MenuItem(value?: MenuItemOptions | CustomBuilder)

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明                         |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------- |
| value  | [MenuItemOptions](#menuitemoptions对象说明)&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | 否   | 包含设置MenuItem的各项信息。 |

## MenuItemOptions对象说明

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 类型                                        | 必填 | 说明                             |
| --------- | ------------------------------------------- | ---- | -------------------------------------- |
| startIcon | [ResourceStr](ts-types.md#resourcestr)      | 否   | item中显示在左侧的图标信息路径。 <br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。      |
| content   | [ResourceStr](ts-types.md#resourcestr)      | 否   | item的内容信息。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。                        |
| endIcon   | [ResourceStr](ts-types.md#resourcestr)      | 否   | item中显示在右侧的图标信息路径。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。        |
| labelInfo | [ResourceStr](ts-types.md#resourcestr)      | 否   | 定义结束标签信息，如快捷方式Ctrl+C等。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。  |
| builder   | [CustomBuilder](ts-types.md#custombuilder8) | 否   | 用于构建二级菜单。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。                      |
| symbolStartIcon<sup>12+</sup>   | [SymbolGlyphModifier](ts-universal-attributes-attribute-modifier.md) | 否   | item中显示在左侧的HMSymbol图标信息路径。配置该项时，原先startIcon图标不显示。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| symbolEndIcon<sup>12+</sup>   | [SymbolGlyphModifier](ts-universal-attributes-attribute-modifier.md) | 否   | item中显示在右侧的HMSymbol图标信息路径。配置该项时，原先endIcon图标不显示。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|


## 属性

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性：

### selected

ArkTS-Dyn: selected(value: boolean)

ArkTS-Sta: selected(value: boolean | undefined | Bindable\<boolean>)

设置菜单项是否选中。

从API version 10开始，该参数支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。
从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | ArkTS-Dyn: boolean<br/>ArkTS-Sta: boolean \| undefined \| Bindable\<boolean> | 是   | 菜单项是否选中。<br />默认值：false<br/>值为true时，菜单项被选中。值为false时，菜单项不被选中。 |

### selectIcon

ArkTS-Dyn: selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier)

ArkTS-Sta: selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier | undefined)

设置当菜单项被选中时，是否显示被选中的图标。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | ArkTS-Dyn: boolean&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr)<sup>10+</sup>\|&nbsp;[SymbolGlyphModifier](ts-universal-attributes-attribute-modifier.md)<sup>12+</sup> <br/>ArkTS-Sta: boolean&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr)\|&nbsp;[SymbolGlyphModifier](ts-universal-attributes-attribute-modifier.md)> \| undefined | 是   | 菜单项被选中时，是否显示被选中的图标。<br/>默认值：false<br/>true：显示默认的对勾图标。<br/>false：不显示图标。<br/>ResourceStr：显示指定的图标。<br/>SymbolGlyphModifier：显示指定的HMSymbol图标。 |

### contentFont<sup>10+</sup>

ArkTS-Dyn: contentFont(value: Font)

ArkTS-Sta: contentFont(value: Font | undefined)

设置菜单项中内容信息的字体样式。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型                     | 必填 | 说明                         |
| ------ | ------------------------ | ---- | ---------------------------- |
| value  | ArkTS-Dyn: [Font](ts-types.md#font) <br/>ArkTS-Sta: [Font](ts-types.md#font) \| undefined  | 是   | 菜单项中内容信息的字体样式。 |

### contentFontColor<sup>10+</sup>

ArkTS-Dyn: contentFontColor(value: ResourceColor)

ArkTS-Sta: contentFontColor(value: ResourceColor | undefined)

设置菜单项中内容信息的字体颜色。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型                                       | 必填 | 说明                         |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| value  | ArkTS-Dyn: [ResourceColor](ts-types.md#resourcecolor) <br/>ArkTS-Sta: [ResourceColor](ts-types.md#resourcecolor) \| undefined | 是   | 菜单项中内容信息的字体颜色。<br />默认值：'#E5000000' |

### labelFont<sup>10+</sup>

ArkTS-Dyn: labelFont(value: Font)

ArkTS-Sta: labelFont(value: Font | undefined)

设置菜单项中标签信息的字体样式。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型                     | 必填 | 说明                         |
| ------ | ------------------------ | ---- | ---------------------------- |
| value  | ArkTS-Dyn: [Font](ts-types.md#font) <br/>ArkTS-Sta: [Font](ts-types.md#font) \| undefined | 是   | 菜单项中标签信息的字体样式。 |

### labelFontColor<sup>10+</sup>

ArkTS-Dyn: labelFontColor(value: ResourceColor)

ArkTS-Sta: labelFontColor(value: ResourceColor | undefined)

设置菜单项中标签信息的字体颜色。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型                                       | 必填 | 说明                         |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| value  | ArkTS-Dyn: [ResourceColor](ts-types.md#resourcecolor) <br/>ArkTS-Sta: [ResourceColor](ts-types.md#resourcecolor) \| undefined| 是   | 菜单项中标签信息的字体颜色。<br />默认值：'#99000000' |

## 事件

### onChange

onChange(callback: (selected: boolean) => void)

当选中状态发生变化时，触发该回调。只有手动触发且MenuItem状态改变时才会触发onChange回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型    | 必填 | 说明                                                         |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| selected | boolean | 是   | 选中状态发生变化时，触发该回调。<br />返回值为true时，表示已选中，为false时，表示未选中。 |

## 示例

详见[Menu组件示例](ts-basic-components-menu.md#示例)。
