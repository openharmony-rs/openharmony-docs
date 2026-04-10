# MenuItemGroup

该组件用来展示菜单MenuItem的分组。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## 子组件

包含[MenuItem](ts-basic-components-menuitem.md)子组件。

## 接口

MenuItemGroup(value?: MenuItemGroupOptions, content_?: CustomBuilder)

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                  | 必填 |说明                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------- |
| value    | [MenuItemGroupOptions](#menuitemgroupoptions对象说明) | 否   | 包含设置MenuItemGroup的标题和尾部显示信息。 |
| content_ | [CustomBuilder](ts-types.md#custombuilder8)           | 否   | 容器内容。 |

## MenuItemGroupOptions对象说明

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称   | 类型                                                         | 必填 | 说明                          |
| ------ | ------------------------------------------------------------ | ---- | ----------------------------- |
| header | [ResourceStr](ts-types.md#resourcestr)&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | 否   | 设置对应group的标题显示信息。 |
| footer | [ResourceStr](ts-types.md#resourcestr)&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | 否   | 设置对应group的尾部显示信息。 |

## 属性

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性：

### attributeModifier<sup>23+</sup>

attributeModifier(modifier: AttributeModifier\<MenuItemGroupAttribute\> | AttributeModifier\<CommonMethod\> | undefined): this

设置MenuItemGroup组件的属性修改器。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                                                                                              | 必填 | 说明                       |
| --------- | ------------------------------------------------------------------------------------------------- | ---- | -------------------------- |
| modifier  | [AttributeModifier](ts-universal-attributes-attribute-modifier.md)\<[MenuItemGroupAttribute](#menuitemgroupattribute)\>&nbsp;\|&nbsp;[AttributeModifier](ts-universal-attributes-attribute-modifier.md)\<[CommonMethod](ts-universal-events-click.md#commonmethod)\>&nbsp;\|&nbsp;undefined | 是   | MenuItemGroup组件的属性修改器。 |

## MenuItemGroupAttribute<sup>23+</sup>

MenuItemGroup组件的属性接口，用于配置MenuItemGroup的各项属性。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

## 示例

详见[Menu组件示例](ts-basic-components-menu.md#示例)。
