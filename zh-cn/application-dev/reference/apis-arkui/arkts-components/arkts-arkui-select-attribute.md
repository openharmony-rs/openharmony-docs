# Select属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** SelectAttribute extends [CommonMethod<SelectAttribute>](CommonMethod<SelectAttribute>)

**起始版本：** 8

<!--Device-unnamed-declare class SelectAttribute extends CommonMethod<SelectAttribute>--><!--Device-unnamed-declare class SelectAttribute extends CommonMethod<SelectAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowModifier

```TypeScript
arrowModifier(modifier: Optional<SymbolGlyphModifier>)
```

定制Select按钮下拉箭头图标样式的方法，在应用arrowModifier之后，Select按钮下拉箭头的图标样式将完全由开发者自定义。
> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-arrowModifier(modifier: Optional<SymbolGlyphModifier>): SelectAttribute--><!--Device-SelectAttribute-arrowModifier(modifier: Optional<SymbolGlyphModifier>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;SymbolGlyphModifier&gt; | 是 | 在Select组件上，定制Select按钮下拉箭头图标样式的方法。 <br/> 当modifier的值为undefined时，不自定义下拉箭头图标样式。 |

## arrowPosition

```TypeScript
arrowPosition(value: ArrowPosition)
```

设置下拉菜单项的文本与箭头之间的对齐方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-arrowPosition(value: ArrowPosition): SelectAttribute--><!--Device-SelectAttribute-arrowPosition(value: ArrowPosition): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ArrowPosition](arkts-arkui-arrowposition-e.md) | 是 | 下拉菜单项的文本与箭头之间的对齐方式。<br/>默认值：ArrowPosition.END |

## arrowPosition

```TypeScript
arrowPosition(position: Optional<ArrowPosition>)
```

设置下拉菜单项的文本与箭头之间的对齐方式。与[arrowPosition](SelectAttribute#arrowPosition(value: ArrowPosition))相比，position参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-arrowPosition(position: Optional<ArrowPosition>): SelectAttribute--><!--Device-SelectAttribute-arrowPosition(position: Optional<ArrowPosition>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Optional](arkts-arkui-optional-t.md)&lt;ArrowPosition&gt; | 是 | 下拉菜单项的文本与箭头之间的对齐方式。<br/>当position的值为undefined时，默认值：ArrowPosition.END |

## avoidance

```TypeScript
avoidance(mode: AvoidanceMode)
```

设置下拉菜单的避让模式。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-avoidance(mode: AvoidanceMode): SelectAttribute--><!--Device-SelectAttribute-avoidance(mode: AvoidanceMode): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AvoidanceMode](arkts-arkui-avoidancemode-e.md) | 是 | 设置下拉菜单的避让模式。<br/>默认值：AvoidanceMode.COVER_TARGET |

## controlSize

```TypeScript
controlSize(value: ControlSize)
```

设置Select组件的尺寸。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-controlSize(value: ControlSize): SelectAttribute--><!--Device-SelectAttribute-controlSize(value: ControlSize): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ControlSize](arkts-arkui-controlsize-e.md) | 是 | Select组件的尺寸。<br/>默认值：ControlSize.NORMAL |

## controlSize

```TypeScript
controlSize(size: Optional<ControlSize>)
```

设置Select组件的尺寸。与[controlSize](SelectAttribute#controlSize(value: ControlSize))<sup>12+</sup>相比，size参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-controlSize(size: Optional<ControlSize>): SelectAttribute--><!--Device-SelectAttribute-controlSize(size: Optional<ControlSize>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [Optional](arkts-arkui-optional-t.md)&lt;ControlSize&gt; | 是 | Select组件的尺寸。<br/>当size的值为undefined时，默认值为ControlSize.NORMAL。 |

## divider

```TypeScript
divider(options: Optional<DividerOptions> | null)
```

设置分割线样式，不设置该属性则按“默认值”展示分割线。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-divider(options: Optional<DividerOptions> | null): SelectAttribute--><!--Device-SelectAttribute-divider(options: Optional<DividerOptions> | null): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;DividerOptions&gt; \| null | 是 | 1.设置DividerOptions，则按设置的样式显示分割线。<br/>默认值：<br/>{<br/>strokeWidth: '1px' , <br/>color: '#33182431'<br/>}<br/>2.设置为null时，不显示分割线。<br/>3.strokeWidth设置过宽时，会覆盖文字。分割线会从每一个Item底部开始，同时向上向下画分割线。<br/>4.startMargin和endMargin的默认值与不设置divider属性时的分割线样式保持一致。startMargin和endMargin的和与optionWidth的值相等时，不显示分割线。 startMargin和endMargin的和超过optionWidth的值时，按照默认样式显示分割线。 |

## dividerStyle

```TypeScript
dividerStyle(style: Optional<DividerStyleOptions>)
```

设置分割线样式，不设置该属性则按“默认值”展示分割线。该属性与divider互斥，按调用顺序生效。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-dividerStyle(style: Optional<DividerStyleOptions>): SelectAttribute--><!--Device-SelectAttribute-dividerStyle(style: Optional<DividerStyleOptions>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;DividerStyleOptions&gt; | 是 | 1.设置DividerOptions，则按设置的样式显示分割线。<br/>默认值：<br/>{<br/>strokeWidth: '1px' , <br/>color: '#33182431'<br/>}<br/>2.设置为null或undefined时，展示默认分割线。<br/>3.当mode为FLOAT_ABOVE_MENU时，strokeWidth设置过宽时，会覆盖文字。分割线会从每一个Item底部开始，同时向上向下画分割线。当mode为EMBEDDED_IN_MENU时，分割线在Menu中展开，独立占用高度。<br/>4.startMargin和endMargin的默认值与不设置divider属性时的分割线样式保持一致。startMargin和endMargin的和与optionWidth的值相等时，不显示分割线。startMargin和endMargin的和超过optionWidth的值时，按照默认样式显示分割线。 |

## font

```TypeScript
font(value: Font)
```

设置下拉按钮本身的文本样式。当size为0时，文本不显示，当size为负值时，文本的size按照默认值显示。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-font(value: Font): SelectAttribute--><!--Device-SelectAttribute-font(value: Font): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 下拉按钮本身的文本样式。<br/>API version 11及以前默认值：<br/>{<br/>size: `$r('sys.float.ohos_id_text_size_button1')`,<br/>weight: FontWeight.Medium<br/>} <br/>API version 12以后，如果设置controlSize的值为：controlSize.SMALL，size默认值是`$r('sys.float.ohos_id_text_size_button2')`，否则为`$r('sys.float.ohos_id_text_size_button1')`。 |

## font

```TypeScript
font(selectFont: Optional<Font>)
```

设置下拉按钮本身的文本样式。当size为0时，文本不显示，当size为负值时，文本的size按照默认值显示。与[font](SelectAttribute#font(value: Font))相比，selectFont参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-font(selectFont: Optional<Font>): SelectAttribute--><!--Device-SelectAttribute-font(selectFont: Optional<Font>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectFont | [Optional](arkts-arkui-optional-t.md)&lt;Font&gt; | 是 | 下拉按钮本身的文本样式。<br/>如果设置controlSize的值为：controlSize.SMALL，size默认值是`$r('sys.float.ohos_id_text_size_button2')`，否则为`$r('sys.float.ohos_id_text_size_button1')`。<br/>当selectFont的值为undefined时，恢复为系统文本样式。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置下拉按钮本身的文本颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-fontColor(value: ResourceColor): SelectAttribute--><!--Device-SelectAttribute-fontColor(value: ResourceColor): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉按钮本身的文本颜色。<br/>默认值：`$r('sys.color.ohos_id_color_text_primary')`混合`$r('sys.color.ohos_id_alpha_content_primary')`的透明度。 |

## fontColor

```TypeScript
fontColor(resColor: Optional<ResourceColor>)
```

设置下拉按钮本身的文本颜色。与[fontColor](SelectAttribute#fontColor(value: ResourceColor))相比，resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-fontColor(resColor: Optional<ResourceColor>): SelectAttribute--><!--Device-SelectAttribute-fontColor(resColor: Optional<ResourceColor>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 下拉按钮本身的文本颜色。<br/>当resColor的值为undefined时，默认值：`$r('sys.color.ohos_id_color_text_primary')`混合`$r('sys.color.ohos_id_alpha_content_primary')`的透明度。<br/>当value的值为undefined时，维持上次取值。 |

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode(mode: Optional<MenuKeyboardAvoidMode>)
```

设置下拉菜单是否避让软键盘。未通过该接口设置时，默认不避让软键盘。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-keyboardAvoidMode(mode: Optional<MenuKeyboardAvoidMode>): SelectAttribute--><!--Device-SelectAttribute-keyboardAvoidMode(mode: Optional<MenuKeyboardAvoidMode>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;MenuKeyboardAvoidMode&gt; | 是 | 设置下拉菜单是否避让软键盘。取值为undefined时，按照MenuKeyboardAvoidMode.NONE处理，不避让软键盘。 |

## menuAlign

```TypeScript
menuAlign(alignType: MenuAlignType, offset?: Offset)
```

设置下拉按钮与下拉菜单间的对齐方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-menuAlign(alignType: MenuAlignType, offset?: Offset): SelectAttribute--><!--Device-SelectAttribute-menuAlign(alignType: MenuAlignType, offset?: Offset): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignType | [MenuAlignType](arkts-arkui-menualigntype-e.md) | 是 | 对齐方式类型。<br/>默认值：MenuAlignType.START |
| offset | [Offset](../arkts-apis/arkts-arkui-componentutils-offset-i.md) | 否 | 按照对齐类型对齐后，下拉菜单相对下拉按钮的偏移量。<br/> 默认值：{dx: 0, dy: 0} |

## menuAlign

```TypeScript
menuAlign(alignType: Optional<MenuAlignType>, offset?: Offset)
```

设置下拉按钮与下拉菜单间的对齐方式。与[menuAlign](SelectAttribute#menuAlign(alignType: MenuAlignType, offset?: Offset))<sup>10+</sup>相比，alignType参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-menuAlign(alignType: Optional<MenuAlignType>, offset?: Offset): SelectAttribute--><!--Device-SelectAttribute-menuAlign(alignType: Optional<MenuAlignType>, offset?: Offset): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignType | [Optional](arkts-arkui-optional-t.md)&lt;MenuAlignType&gt; | 是 | 对齐方式类型。<br/>当alignType的值为undefined时，默认值：MenuAlignType.START |
| offset | [Offset](../arkts-apis/arkts-arkui-componentutils-offset-i.md) | 否 | 按照对齐类型对齐后，下拉菜单相对下拉按钮的偏移量。<br/> 默认值：{dx: 0, dy: 0} |

## menuBackgroundBlurStyle

```TypeScript
menuBackgroundBlurStyle(value: BlurStyle)
```

设置下拉菜单的背景模糊材质。
> **说明：**  
>  
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-menuBackgroundBlurStyle(value: BlurStyle): SelectAttribute--><!--Device-SelectAttribute-menuBackgroundBlurStyle(value: BlurStyle): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BlurStyle](arkts-arkui-blurstyle-e.md) | 是 | 下拉菜单的背景模糊材质。<br/>默认值：BlurStyle.COMPONENT_ULTRA_THICK |

## menuBackgroundBlurStyle

```TypeScript
menuBackgroundBlurStyle(style: Optional<BlurStyle>)
```

设置下拉菜单的背景模糊材质。与[menuBackgroundBlurStyle](SelectAttribute#menuBackgroundBlurStyle(value: BlurStyle))<sup>11+</sup>相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-menuBackgroundBlurStyle(style: Optional<BlurStyle>): SelectAttribute--><!--Device-SelectAttribute-menuBackgroundBlurStyle(style: Optional<BlurStyle>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;BlurStyle&gt; | 是 | 下拉菜单的背景模糊材质。<br/>当style的值为undefined时，默认值：BlurStyle.COMPONENT_ULTRA_THICK |

## menuBackgroundBlurStyleOptions

```TypeScript
menuBackgroundBlurStyleOptions(blurStyle: Optional<BackgroundBlurStyleOptions>)
```

设置Select组件的背景模糊效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-menuBackgroundBlurStyleOptions(blurStyle: Optional<BackgroundBlurStyleOptions>): SelectAttribute--><!--Device-SelectAttribute-menuBackgroundBlurStyleOptions(blurStyle: Optional<BackgroundBlurStyleOptions>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurStyle | [Optional](arkts-arkui-optional-t.md)&lt;BackgroundBlurStyleOptions&gt; | 是 | 设置Select组件的背景模糊效果。 |

## menuBackgroundColor

```TypeScript
menuBackgroundColor(value: ResourceColor)
```

设置下拉菜单的背景色。
> **说明：**  
>  
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-menuBackgroundColor(value: ResourceColor): SelectAttribute--><!--Device-SelectAttribute-menuBackgroundColor(value: ResourceColor): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉菜单的背景色。<br/>默认值：<br/>API version 11之前，默认值为$r('sys.color.ohos_id_color_card_bg')。<br/>API version 11及之后，默认值为Color.Transparent。 |

## menuBackgroundColor

```TypeScript
menuBackgroundColor(resColor: Optional<ResourceColor>)
```

设置下拉菜单的背景色。与[menuBackgroundColor](SelectAttribute#menuBackgroundColor(value: ResourceColor))<sup>11+</sup>相比，resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-menuBackgroundColor(resColor: Optional<ResourceColor>): SelectAttribute--><!--Device-SelectAttribute-menuBackgroundColor(resColor: Optional<ResourceColor>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 下拉菜单的背景色。<br/>当resColor的值为undefined时，默认值为Color.Transparent。 |

## menuBackgroundEffect

```TypeScript
menuBackgroundEffect(effect: Optional<BackgroundEffectOptions>)
```

设置Select组件的背景属性。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-menuBackgroundEffect(effect: Optional<BackgroundEffectOptions>): SelectAttribute--><!--Device-SelectAttribute-menuBackgroundEffect(effect: Optional<BackgroundEffectOptions>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [Optional](arkts-arkui-optional-t.md)&lt;BackgroundEffectOptions&gt; | 是 | 设置Select组件的背景属性，包括：模糊半径、亮度、饱和度和颜色。 |

## menuItemContentModifier

```TypeScript
menuItemContentModifier(modifier: ContentModifier<MenuItemConfiguration>)
```

定制Select下拉菜单项内容区的方法。在应用了menuItemContentModifier后，下拉菜单的内容将完全由开发者自定义，此时为Select组件设置的分割线、选项颜色及下拉菜单的字体颜色等属性将不再生效。
> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-menuItemContentModifier(modifier: ContentModifier<MenuItemConfiguration>): SelectAttribute--><!--Device-SelectAttribute-menuItemContentModifier(modifier: ContentModifier<MenuItemConfiguration>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;MenuItemConfiguration&gt; | 是 | 在Select组件上，定制下拉菜单项内容区的方法。<br/>modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。 |

## menuItemContentModifier

```TypeScript
menuItemContentModifier(modifier: Optional<ContentModifier<MenuItemConfiguration>>)
```

定制Select下拉菜单项内容区的方法。与[menuItemContentModifier](SelectAttribute#menuItemContentModifier(modifier: ContentModifier<MenuItemConfiguration>))<sup>12+</sup>相比，modifier参数新增了对undefined类型的支持。在应用了menuItemContentModifier后，下拉菜单的内容将完全由开发者自定义，此时为Select组件设置的分割线、选项颜色及下拉菜单的字体颜色等属性将不再生效。
> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-menuItemContentModifier(modifier: Optional<ContentModifier<MenuItemConfiguration>>): SelectAttribute--><!--Device-SelectAttribute-menuItemContentModifier(modifier: Optional<ContentModifier<MenuItemConfiguration>>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;ContentModifier&lt;MenuItemConfiguration&gt;&gt; | 是 | 在Select组件上，定制下拉菜单项内容区的方法。<br/>modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。<br/>当modifier的值为undefined时，不使用内容修改器。 |

## menuOutline

```TypeScript
menuOutline(outline: MenuOutlineOptions)
```

设置下拉菜单框的外描边样式。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-menuOutline(outline: MenuOutlineOptions): SelectAttribute--><!--Device-SelectAttribute-menuOutline(outline: MenuOutlineOptions): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outline | [MenuOutlineOptions](arkts-arkui-menuoutlineoptions-i.md) | 是 | 下拉菜单框的外描边样式。 |

## minKeyboardAvoidDistance

```TypeScript
minKeyboardAvoidDistance(distance: Optional<LengthMetrics>)
```

设置Select的菜单避让软键盘的最小距离。未通过该接口设置，最小距离默认为8vp。仅当[keyboardAvoidMode](SelectAttribute#keyboardAvoidMode)设置为避让软键盘时生效。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-minKeyboardAvoidDistance(distance: Optional<LengthMetrics>): SelectAttribute--><!--Device-SelectAttribute-minKeyboardAvoidDistance(distance: Optional<LengthMetrics>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| distance | [Optional](arkts-arkui-optional-t.md)&lt;LengthMetrics&gt; | 是 | 设置下拉菜单避让软键盘的最小距离。设置为负数、undefined时，按照8vp处理。 |

## onSelect

```TypeScript
onSelect(callback: (index: number, value: string) => void)
```

下拉菜单选中某一项时，会触发回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-onSelect(callback: (index: number, value: string) => void): SelectAttribute--><!--Device-SelectAttribute-onSelect(callback: (index: number, value: string) => void): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (index: number, value: string) =&gt; void | 是 |  |

## onSelect

```TypeScript
onSelect(callback: Optional<OnSelectCallback>)
```

下拉菜单选中某一项时，会触发回调。与[onSelect](SelectAttribute#onSelect(callback: (index: number, value: string) => void))相比，callback参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-onSelect(callback: Optional<OnSelectCallback>): SelectAttribute--><!--Device-SelectAttribute-onSelect(callback: Optional<OnSelectCallback>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;OnSelectCallback&gt; | 是 | 下拉菜单选中某一项的回调。<br/>当callback的值为undefined时，不使用回调函数。 |

## optionBgColor

```TypeScript
optionBgColor(value: ResourceColor)
```

设置下拉菜单项的背景色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-optionBgColor(value: ResourceColor): SelectAttribute--><!--Device-SelectAttribute-optionBgColor(value: ResourceColor): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉菜单项的背景色。<br/>默认值：<br/>API version 11之前，默认值为Color.White。<br/>API version 11及之后，默认值为Color.Transparent。 |

## optionBgColor

```TypeScript
optionBgColor(resColor: Optional<ResourceColor>)
```

设置下拉菜单项的背景色。与[optionBgColor](SelectAttribute#optionBgColor(value: ResourceColor))相比，resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-optionBgColor(resColor: Optional<ResourceColor>): SelectAttribute--><!--Device-SelectAttribute-optionBgColor(resColor: Optional<ResourceColor>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 下拉菜单项的背景色。<br/>当resColor的值为undefined时，下拉菜单项的背景色为Color.White。 |

## optionFont

```TypeScript
optionFont(value: Font)
```

设置下拉菜单项的文本样式。当size为0的时候，文本不显示，当size为负值的时候，文本的size按照默认值显示。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-optionFont(value: Font): SelectAttribute--><!--Device-SelectAttribute-optionFont(value: Font): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 下拉菜单项的文本样式。<br/>默认值：<br/>{<br/>size: $r('sys.float.ohos_id_text_size_body1'),<br/>weight: FontWeight.Regular<br/>} |

## optionFont

```TypeScript
optionFont(selectFont: Optional<Font>)
```

设置下拉菜单项的文本样式。当size为0的时候，文本不显示，当size为负值的时候，文本的size按照默认值显示。

与[optionFont](SelectAttribute#optionFont(value: Font))相比，selectFont参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-optionFont(selectFont: Optional<Font>): SelectAttribute--><!--Device-SelectAttribute-optionFont(selectFont: Optional<Font>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectFont | [Optional](arkts-arkui-optional-t.md)&lt;Font&gt; | 是 | 下拉菜单项的文本样式。<br/>当selectFont的值为undefined时，默认值：<br/>{<br/>size: $r('sys.float.ohos_id_text_size_body1'),<br/>weight: FontWeight.Regular<br/>} |

## optionFontColor

```TypeScript
optionFontColor(value: ResourceColor)
```

设置下拉菜单项的文本颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-optionFontColor(value: ResourceColor): SelectAttribute--><!--Device-SelectAttribute-optionFontColor(value: ResourceColor): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉菜单项的文本颜色。<br/>默认值：$r('sys.color.ohos_id_color_text_primary') |

## optionFontColor

```TypeScript
optionFontColor(resColor: Optional<ResourceColor>)
```

设置下拉菜单项的文本颜色。与[optionFontColor](SelectAttribute#optionFontColor(value: ResourceColor))相比，resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-optionFontColor(resColor: Optional<ResourceColor>): SelectAttribute--><!--Device-SelectAttribute-optionFontColor(resColor: Optional<ResourceColor>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 下拉菜单项的文本颜色。<br/>当resColor的值为undefined时，默认值：$r('sys.color.ohos_id_color_text_primary') |

## optionHeight

```TypeScript
optionHeight(value: Dimension)
```

设置下拉菜单显示的最大高度，不支持设置百分比。默认最大高度是屏幕可用高度的80%，设置的菜单最大高度不能超过默认最大高度。

当设置为异常值或零时，属性不生效。

如果下拉菜单所有选项的实际高度没有设定的高度大，下拉菜单的高度按实际高度显示。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-optionHeight(value: Dimension): SelectAttribute--><!--Device-SelectAttribute-optionHeight(value: Dimension): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 下拉菜单显示的最大高度。 |

## optionHeight

```TypeScript
optionHeight(height: Optional<Dimension>)
```

设置下拉菜单显示的最大高度，不支持设置百分比。默认最大高度是屏幕可用高度的80%，设置的菜单最大高度不能超过默认最大高度。与[optionHeight](SelectAttribute#optionHeight(value: Dimension))<sup>11+</sup>相比，height参数新增了对undefined类型的支持。

当设置为异常值或零时，属性不生效。

如果下拉菜单所有选项的实际高度小于设定的高度，下拉菜单的高度按实际高度显示。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-optionHeight(height: Optional<Dimension>): SelectAttribute--><!--Device-SelectAttribute-optionHeight(height: Optional<Dimension>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-optional-t.md)&lt;Dimension&gt; | 是 | 下拉菜单显示的最大高度。<br/>当height的值为undefined时，属性不生效，下拉菜单最大高度设为默认值，即下拉菜单最大高度默认值为屏幕可用高度的80%。 |

## optionTextModifier

```TypeScript
optionTextModifier(modifier: Optional<TextModifier>)
```

定制Select下拉菜单未选中项文本样式的方法，在应用optionTextModifier之后，下拉菜单未选中项的文本样式将完全由开发者自定义。

如果[optionFont](SelectAttribute#optionFont(value: Font))与optionTextModifier的Font属性同时设置，则优先使用[optionFont](SelectAttribute#optionFont(value: Font))设置下拉菜单未选中项的文本样式；[optionFont](SelectAttribute#optionFont(value: Font))中缺省的属性将设置为对应的默认值。
> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-optionTextModifier(modifier: Optional<TextModifier>): SelectAttribute--><!--Device-SelectAttribute-optionTextModifier(modifier: Optional<TextModifier>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;TextModifier&gt; | 是 | 在Select组件上，定制Select下拉菜单未选中项样式的方法。<br/> 当modifier的值为undefined时，不自定义下拉菜单未选中项的文本样式。 |

## optionWidth

```TypeScript
optionWidth(value: Dimension | OptionWidthMode )
```

设置下拉菜单项的宽度，不支持设置百分比。OptionWidthMode类型为枚举类型，OptionWidthMode决定下拉菜单是否继承下拉按钮宽度。

当设置为异常值或小于最小宽度56vp时，属性无效，菜单项宽度设为默认值，即2栅格。

Select组件距屏幕边缘的左右间距为16vp，建议将组件本身及菜单项的宽度设置为小于等于`calc(100% - 32vp)`的值，以避免下拉菜单弹出时发生偏移。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-optionWidth(value: Dimension | OptionWidthMode ): SelectAttribute--><!--Device-SelectAttribute-optionWidth(value: Dimension | OptionWidthMode ): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) \| OptionWidthMode | 是 | 下拉菜单项的宽度。 |

## optionWidth

```TypeScript
optionWidth(width: Optional<Dimension | OptionWidthMode> )
```

设置下拉菜单项的宽度，不支持设置百分比。OptionWidthMode类型为枚举类型，OptionWidthMode决定下拉菜单是否继承下拉按钮宽度。与[optionWidth](SelectAttribute#optionWidth(value: Dimension | OptionWidthMode ))<sup>11+</sup>相比，width参数新增了对undefined类型的支持。

当设置为异常值或小于最小宽度56vp时，属性无效，菜单项宽度设为默认值，即2栅格。

Select组件距屏幕边缘的左右间距为16vp，建议将组件本身及菜单项的宽度设置为小于等于`calc(100% - 32vp)`的值，以避免下拉菜单弹出时发生偏移。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-optionWidth(width: Optional<Dimension | OptionWidthMode> ): SelectAttribute--><!--Device-SelectAttribute-optionWidth(width: Optional<Dimension | OptionWidthMode> ): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-optional-t.md)&lt;Dimension \| OptionWidthMode&gt; | 是 | 下拉菜单项的宽度。<br/>当width的值为undefined时，属性无效，菜单项宽度设为默认值，即2栅格。 |

## selected

```TypeScript
selected(value: number | Resource)
```

设置下拉菜单初始选项的索引，第一项的索引为0。当不设置selected属性或设置为异常值时，默认选中值为-1，菜单项不选中；当设置为undefined、null时，选中第一项。

从API version 10开始，该属性支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

从API version 18开始，该属性支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-selected(value: number | Resource): SelectAttribute--><!--Device-SelectAttribute-selected(value: number | Resource): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| Resource | 是 | 下拉菜单初始选项的索引，索引值从0开始。<br>**起始版本：** 11 |

## selected

```TypeScript
selected(numCount: Optional<number | Resource>)
```

设置下拉菜单初始选项的索引，第一项的索引为0。当不设置selected属性或设置异常值时，默认选择值为-1，菜单项不选中；当设置为undefined、null时，选中第一项。

该属性支持[$$](../../../ui/state-management/arkts-two-way-sync.md)、[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-selected(numCount: Optional<number | Resource>): SelectAttribute--><!--Device-SelectAttribute-selected(numCount: Optional<number | Resource>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| numCount | [Optional](arkts-arkui-optional-t.md)&lt;number \| Resource&gt; | 是 | 下拉菜单初始选项的索引。<br/>当numCount的值为undefined时，选中第一项。 |

## selectedOptionBgColor

```TypeScript
selectedOptionBgColor(value: ResourceColor)
```

设置下拉菜单选中项的背景色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-selectedOptionBgColor(value: ResourceColor): SelectAttribute--><!--Device-SelectAttribute-selectedOptionBgColor(value: ResourceColor): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉菜单选中项的背景色。<br/>默认值：`$r('sys.color.ohos_id_color_component_activated')`混合`$r('sys.color.ohos_id_alpha_highlight_bg')`的透明度。 |

## selectedOptionBgColor

```TypeScript
selectedOptionBgColor(resColor: Optional<ResourceColor>)
```

设置下拉菜单选中项的背景色。与[selectedOptionBgColor](SelectAttribute#selectedOptionBgColor(value: ResourceColor))相比，resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-selectedOptionBgColor(resColor: Optional<ResourceColor>): SelectAttribute--><!--Device-SelectAttribute-selectedOptionBgColor(resColor: Optional<ResourceColor>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 下拉菜单选中项的背景色。<br/>当resColor的值为undefined时，默认值：`$r('sys.color.ohos_id_color_component_activated')`混合`$r('sys.color.ohos_id_alpha_highlight_bg')`的透明度。 |

## selectedOptionFont

```TypeScript
selectedOptionFont(value: Font)
```

设置下拉菜单选中项的文本样式。当size为0的时候，文本不显示，当size为负值的时候，文本的size按照默认值显示。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-selectedOptionFont(value: Font): SelectAttribute--><!--Device-SelectAttribute-selectedOptionFont(value: Font): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 下拉菜单选中项的文本样式。<br/>默认值：<br/>{<br/>size: $r('sys.float.ohos_id_text_size_body1'),<br/>weight: FontWeight.Regular<br/>} |

## selectedOptionFont

```TypeScript
selectedOptionFont(selectFont: Optional<Font>)
```

设置下拉菜单选中项的文本样式。当size为0的时候，文本不显示，当size为负值的时候，文本的size按照默认值显示。与[selectedOptionFont](SelectAttribute#selectedOptionFont(value: Font))相比，selectFont参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-selectedOptionFont(selectFont: Optional<Font>): SelectAttribute--><!--Device-SelectAttribute-selectedOptionFont(selectFont: Optional<Font>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectFont | [Optional](arkts-arkui-optional-t.md)&lt;Font&gt; | 是 | 下拉菜单选中项的文本样式。<br/>当selectFont的值为undefined时，默认值：<br/>{<br/>size: $r('sys.float.ohos_id_text_size_body1'),<br/>weight: FontWeight.Regular<br/>} |

## selectedOptionFontColor

```TypeScript
selectedOptionFontColor(value: ResourceColor)
```

设置下拉菜单选中项的文本颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-selectedOptionFontColor(value: ResourceColor): SelectAttribute--><!--Device-SelectAttribute-selectedOptionFontColor(value: ResourceColor): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉菜单选中项的文本颜色。<br/>默认值：$r('sys.color.ohos_id_color_text_primary_activated') |

## selectedOptionFontColor

```TypeScript
selectedOptionFontColor(resColor: Optional<ResourceColor>)
```

设置下拉菜单选中项的文本颜色。与[selectedOptionFontColor](SelectAttribute#selectedOptionFontColor(value: ResourceColor))相比，resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-selectedOptionFontColor(resColor: Optional<ResourceColor>): SelectAttribute--><!--Device-SelectAttribute-selectedOptionFontColor(resColor: Optional<ResourceColor>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 下拉菜单选中项的文本颜色。<br/>当resColor的值为undefined时，默认值为$r('sys.color.ohos_id_color_text_primary_activated')。 |

## selectedOptionTextModifier

```TypeScript
selectedOptionTextModifier(modifier: Optional<TextModifier>)
```

定制Select下拉菜单选中项文本样式的方法，在应用selectedOptionTextModifier之后，下拉菜单选中项的文本样式将完全由开发者自定义。

如果[selectedOptionFont](SelectAttribute#selectedOptionFont(value: Font))与selectedOptionTextModifier的Font属性同时设置，则优先使用[selectedOptionFont](SelectAttribute#selectedOptionFont(value: Font))设置下拉菜单选中项的文本样式；若未设置[selectedOptionFont](SelectAttribute#selectedOptionFont(value: Font))，则优先使用[optionFont](SelectAttribute#optionFont(value: Font))设置下拉菜单选中项的文本样式。其中[selectedOptionFont](SelectAttribute#selectedOptionFont(value: Font))或者[optionFont](SelectAttribute#optionFont(value: Font))缺省的属性将设置为对应的默认值。
> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-selectedOptionTextModifier(modifier: Optional<TextModifier>): SelectAttribute--><!--Device-SelectAttribute-selectedOptionTextModifier(modifier: Optional<TextModifier>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;TextModifier&gt; | 是 | 设置下拉菜单项选中项的文本样式。<br/>开发者可以根据需要管理和维护文本的样式进行设置。 <br/> 当modifier的值为undefined时，不自定义下拉菜单项选中项的文本样式。 |

## showDefaultSelectedIcon

```TypeScript
showDefaultSelectedIcon(show: boolean)
```

设置是否显示默认选择的图标。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-showDefaultSelectedIcon(show: boolean): SelectAttribute--><!--Device-SelectAttribute-showDefaultSelectedIcon(show: boolean): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| show | boolean | 是 | 是否显示默认选定的图标。<br/>true：显示默认选择的图标；false：不显示默认选择的图标，通过突出显示背景色来表示选中。<br/>默认值：false<br/>当show为true时，若设置了selectedOptionBgColor选中项的背景色时，则同时显示选中项的背景色和默认选定的图标；若未通过selectedOptionBgColor设置选中项的背景色时，不突出显示背景色，只显示默认选定的图标。 |

## showInSubWindow

```TypeScript
showInSubWindow(showInSubWindow: Optional<boolean>)
```

设置下拉菜单是否显示在子窗中。未通过该接口设置时，下拉菜单默认不显示在子窗中。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-showInSubWindow(showInSubWindow: Optional<boolean>): SelectAttribute--><!--Device-SelectAttribute-showInSubWindow(showInSubWindow: Optional<boolean>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| showInSubWindow | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置下拉菜单是否显示在子窗中。<br>true代表下拉菜单显示在子窗中。<br>false代表下拉菜单不显示在子窗中。 |

## space

```TypeScript
space(value: Length)
```

设置下拉菜单项的文本与箭头的间距。不支持设置百分比。将间距设置为null、undefined，或者小于等于8的值时，取默认值。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-space(value: Length): SelectAttribute--><!--Device-SelectAttribute-space(value: Length): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 下拉菜单项的文本与箭头的间距。<br/>默认值：8<br/>**说明：** 设置string类型时，不支持百分比。 |

## space

```TypeScript
space(spaceLength: Optional<Length>)
```

设置下拉菜单项的文本与箭头的间距。不支持设置百分比。设置为null、undefined，或者小于等于8的值，取默认值。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-space(spaceLength: Optional<Length>): SelectAttribute--><!--Device-SelectAttribute-space(spaceLength: Optional<Length>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spaceLength | [Optional](arkts-arkui-optional-t.md)&lt;Length&gt; | 是 | 下拉菜单项的文本与箭头之间的间距。<br/>当spaceLength的值为undefined时，默认值：8 |

## textModifier

```TypeScript
textModifier(modifier: Optional<TextModifier>)
```

定制Select按钮文本样式的方法，在应用了textModifier之后，Select按钮的文本样式将完全由开发者自定义。
> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-textModifier(modifier: Optional<TextModifier>): SelectAttribute--><!--Device-SelectAttribute-textModifier(modifier: Optional<TextModifier>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;TextModifier&gt; | 是 | 在Select组件上，定制按钮文本样式的方法。 <br/> 当modifier的值为undefined时，不自定义文本样式。 |

## value

```TypeScript
value(value: ResourceStr)
```

设置下拉按钮的文本内容。选中菜单项后，按钮文本将自动更新为选中的菜单项文本。

从API version 10开始，该参数支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-value(value: ResourceStr): SelectAttribute--><!--Device-SelectAttribute-value(value: ResourceStr): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 下拉按钮本身的文本内容。<br/>**说明：** 文本长度大于列宽时，文本被截断。<br>**起始版本：** 11 |

## value

```TypeScript
value(resStr: Optional<ResourceStr>)
```

设置下拉按钮的文本内容。选中菜单项后，按钮文本将自动更新为选中的菜单项文本。与[value](SelectAttribute#value(value: ResourceStr))相比，resStr参数新增了对undefined类型的支持。

该参数支持[$$](../../../ui/state-management/arkts-two-way-sync.md)、[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectAttribute-value(resStr: Optional<ResourceStr>): SelectAttribute--><!--Device-SelectAttribute-value(resStr: Optional<ResourceStr>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resStr | [Optional](arkts-arkui-optional-t.md)&lt;ResourceStr&gt; | 是 | 下拉按钮本身的文本内容。<br/>当resStr的值为undefined时维持上次取值。 |

