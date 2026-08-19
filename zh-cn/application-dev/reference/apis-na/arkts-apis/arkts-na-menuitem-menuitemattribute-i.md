# MenuItemAttribute

除支持通用属性外，还支持以下属性：

**继承/实现关系：** MenuItemAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface MenuItemAttribute--><!--Device-unnamed-export declare interface MenuItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(
        modifier: AttributeModifier<MenuItemAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuItemAttribute-attributeModifier(        modifier: AttributeModifier<MenuItemAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-MenuItemAttribute-attributeModifier(        modifier: AttributeModifier<MenuItemAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[MenuItemAttribute](arkts-na-menuitem-menuitemattribute-i.md)&gt; \| [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## contentFont

```TypeScript
contentFont(value: Font | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuItemAttribute-contentFont(value: Font | undefined): this--><!--Device-MenuItemAttribute-contentFont(value: Font | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../../apis-arkui/arkts-apis/arkts-arkui-font-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## contentFontColor

```TypeScript
contentFontColor(value: ResourceColor | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuItemAttribute-contentFontColor(value: ResourceColor | undefined): this--><!--Device-MenuItemAttribute-contentFontColor(value: ResourceColor | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## labelFont

```TypeScript
labelFont(value: Font | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuItemAttribute-labelFont(value: Font | undefined): this--><!--Device-MenuItemAttribute-labelFont(value: Font | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../../apis-arkui/arkts-apis/arkts-arkui-font-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## labelFontColor

```TypeScript
labelFontColor(value: ResourceColor | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuItemAttribute-labelFontColor(value: ResourceColor | undefined): this--><!--Device-MenuItemAttribute-labelFontColor(value: ResourceColor | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onChange

```TypeScript
onChange(callback: ((selected: boolean) => void) | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuItemAttribute-onChange(callback: ((selected: boolean) => void) | undefined): this--><!--Device-MenuItemAttribute-onChange(callback: ((selected: boolean) => void) | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ((selected: boolean) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## selectIcon

```TypeScript
selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuItemAttribute-selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier | undefined): this--><!--Device-MenuItemAttribute-selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| SymbolGlyphModifier \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## selected

```TypeScript
selected(value: boolean | undefined | Bindable<boolean>): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuItemAttribute-selected(value: boolean | undefined | Bindable<boolean>): this--><!--Device-MenuItemAttribute-selected(value: boolean | undefined | Bindable<boolean>): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined \| [Bindable](arkts-na-common-bindable-i.md)&lt;boolean&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

设置MenuItem组件的属性修改器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemAttribute-default--><!--Device-MenuItemAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

