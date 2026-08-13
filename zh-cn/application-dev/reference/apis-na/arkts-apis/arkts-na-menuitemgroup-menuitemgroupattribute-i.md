# MenuItemGroupAttribute

不支持通用属性。

**继承/实现关系：** MenuItemGroupAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface MenuItemGroupAttribute--><!--Device-unnamed-export declare interface MenuItemGroupAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(
        modifier: AttributeModifier<MenuItemGroupAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

设置MenuItemGroup组件的属性修改器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemGroupAttribute-attributeModifier(        modifier: AttributeModifier<MenuItemGroupAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-MenuItemGroupAttribute-attributeModifier(        modifier: AttributeModifier<MenuItemGroupAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[MenuItemGroupAttribute](arkts-na-menuitemgroup-menuitemgroupattribute-i.md)&gt; \| [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 | MenuItemGroup组件的属性修改器。&lt;br/&gt;CommonMethod：通用属性 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

