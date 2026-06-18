# MenuItemGroup
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Armstrong15-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

该组件用来展示菜单MenuItem的分组。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 该组件从API版本26.0.0开始支持[WithTheme](./ts-container-with-theme.md)。

## 子组件

包含[MenuItem](ts-basic-components-menuitem.md)子组件。

## 接口

MenuItemGroup(value?: MenuItemGroupOptions)

构造MenuItem的分组。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                  | 只读 | 可选 |说明                                        |
| -------- | ----------------------------------------------------- | ---- | ---- | ------------------------------------------- |
| value    | [MenuItemGroupOptions](#menuitemgroupoptions对象说明) | 否   | 是   | 包含设置MenuItemGroup的标题和尾部显示信息。 |

## MenuItemGroupOptions对象说明

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称   | 类型                                                         | 只读 | 可选 | 说明                          |
| ------ | ------------------------------------------------------------ | ---- | ---- | ----------------------------- |
| header | [ResourceStr](ts-types.md#resourcestr)&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | 否   | 是   | 设置对应group的标题显示信息。 <br/> 未设置时，不显示标题信息。 |
| footer | [ResourceStr](ts-types.md#resourcestr)&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | 否   | 是   | 设置对应group的尾部显示信息。 <br/> 未设置时，不显示尾部信息。 |

## 属性

不支持[通用属性](ts-component-general-attributes.md)。

## MenuItemGroupAttribute<sup>23+</sup>

MenuItemGroup组件的属性接口，用于配置MenuItemGroup的各项属性。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### attributeModifier

attributeModifier(modifier: AttributeModifier\<MenuItemGroupAttribute\> | AttributeModifier\<CommonMethod\> | undefined): this

设置MenuItemGroup组件的属性修改器。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                                                                              | 只读 | 可选 | 说明                       |
| --------- | ------------------------------------------------------------------------------------------------- | ---- | ---- | -------------------------- |
| modifier  | [AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifiert)\<[MenuItemGroupAttribute](#menuitemgroupattribute23)\>&nbsp;\|&nbsp;[AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifiert)\<CommonMethod\>&nbsp;\|&nbsp;undefined | 否   | 否   | MenuItemGroup组件的属性修改器。<br/>CommonMethod：[通用属性](./ts-component-general-attributes.md) |

## 示例

详见[Menu组件示例](ts-basic-components-menu.md#示例)。
