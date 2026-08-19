# MenuAttribute

除支持通用属性外，还支持以下属性：

**继承/实现关系：** MenuAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface MenuAttribute--><!--Device-unnamed-export declare interface MenuAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(
        modifier: AttributeModifier<MenuAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuAttribute-attributeModifier(        modifier: AttributeModifier<MenuAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-MenuAttribute-attributeModifier(        modifier: AttributeModifier<MenuAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[MenuAttribute](arkts-na-menu-menuattribute-i.md)&gt; \| [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## font

```TypeScript
font(value: Font | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuAttribute-font(value: Font | undefined): this--><!--Device-MenuAttribute-font(value: Font | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../../apis-arkui/arkts-apis/arkts-arkui-font-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## fontColor

```TypeScript
fontColor(value: ResourceColor | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuAttribute-fontColor(value: ResourceColor | undefined): this--><!--Device-MenuAttribute-fontColor(value: ResourceColor | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## menuItemDivider

```TypeScript
menuItemDivider(options: DividerStyleOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuAttribute-menuItemDivider(options: DividerStyleOptions | undefined): this--><!--Device-MenuAttribute-menuItemDivider(options: DividerStyleOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DividerStyleOptions](../../apis-arkui/arkts-apis/arkts-arkui-dividerstyleoptions-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## menuItemGroupDivider

```TypeScript
menuItemGroupDivider(options: DividerStyleOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuAttribute-menuItemGroupDivider(options: DividerStyleOptions | undefined): this--><!--Device-MenuAttribute-menuItemGroupDivider(options: DividerStyleOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DividerStyleOptions](../../apis-arkui/arkts-apis/arkts-arkui-dividerstyleoptions-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## radius

```TypeScript
radius(value: Dimension | BorderRadiuses | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuAttribute-radius(value: Dimension | BorderRadiuses | undefined): this--><!--Device-MenuAttribute-radius(value: Dimension | BorderRadiuses | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md) \| [BorderRadiuses](../../apis-arkui/arkts-apis/arkts-arkui-borderradiuses-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## subMenuExpandSymbol

```TypeScript
subMenuExpandSymbol(symbol: SymbolGlyphModifier | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuAttribute-subMenuExpandSymbol(symbol: SymbolGlyphModifier | undefined): this--><!--Device-MenuAttribute-subMenuExpandSymbol(symbol: SymbolGlyphModifier | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| symbol | SymbolGlyphModifier \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## subMenuExpandingMode

```TypeScript
subMenuExpandingMode(mode: SubMenuExpandingMode | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MenuAttribute-subMenuExpandingMode(mode: SubMenuExpandingMode | undefined): this--><!--Device-MenuAttribute-subMenuExpandingMode(mode: SubMenuExpandingMode | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [SubMenuExpandingMode](arkts-na-menu-submenuexpandingmode-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

设置Menu组件的属性修改器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuAttribute-default--><!--Device-MenuAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

