# SelectParams

AtomicServiceSearch中“选择区”的可选属性。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-export interface SelectParams--><!--Device-unnamed-export interface SelectParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowPosition

```TypeScript
arrowPosition?: ArrowPosition
```

下拉菜单项的文本与箭头之间的对齐方式。默认值：ArrowPosition.END。

**类型：** ArrowPosition

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-arrowPosition?: ArrowPosition--><!--Device-SelectParams-arrowPosition?: ArrowPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## divider

```TypeScript
divider?: Optional<DividerOptions> | null
```

1.设置DividerOptions，则按设置的样式显示分割线。默认值：{strokeWidth: '1px', color: '#33182431'}。 当设置了menuItemContentModifier属性时，本属性不生效。 2.设置为null时，不显示分割线。 3.strokeWidth设置过宽时，会覆盖文字。分割线会从每一个Item底部开始，同时向上向下画分割线。 4.startMargin和endMargin的默认值与不设置divider属性时的分割线样式保持一致。startMargin和endMargin的和与optionWidth的值相等时， 不显示分割线。 startMargin和endMargin的和超过optionWidth的值时，按照默认样式显示分割线。

**类型：** Optional&lt;DividerOptions&gt; \| null

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-divider?: Optional<DividerOptions> | null--><!--Device-SelectParams-divider?: Optional<DividerOptions> | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

下拉按钮本身的文本样式。默认值：{size: \$r('sys.float.ohos_id_text_size_body1')}。

**类型：** Font

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-font?: Font--><!--Device-SelectParams-font?: Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

下拉按钮本身的文本颜色。默认值：{fontColor: \$r('sys.color.ohos_id_color_text_primary')}。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-fontColor?: ResourceColor--><!--Device-SelectParams-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuAlign

```TypeScript
menuAlign?: MenuAlignParams
```

设置下拉按钮与下拉菜单间的对齐方式。默认值：{alignType: MenuAlignType.START, offset: {dx: 0, dy: 0}}。

**类型：** [MenuAlignParams](arkts-arkui-atomicservice-atomicservicesearch-menualignparams-i.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-menuAlign?: MenuAlignParams--><!--Device-SelectParams-menuAlign?: MenuAlignParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuBackgroundBlurStyle

```TypeScript
menuBackgroundBlurStyle?: BlurStyle
```

下拉菜单的背景模糊材质。默认值：BlurStyle.COMPONENT_ULTRA_THICK。

**类型：** BlurStyle

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-menuBackgroundBlurStyle?: BlurStyle--><!--Device-SelectParams-menuBackgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuBackgroundColor

```TypeScript
menuBackgroundColor?: ResourceColor
```

下拉菜单的背景色。默认值：Color.Transparent。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-menuBackgroundColor?: ResourceColor--><!--Device-SelectParams-menuBackgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuItemContentModifier

```TypeScript
menuItemContentModifier?: ContentModifier<MenuItemConfiguration>
```

在Select组件上，定制下拉菜单项内容区的方法。 在应用了该属性后，下拉菜单的内容将完全由开发者自定义，此时为选择区设置的下拉菜单分割线、背景色及字体样式等属性将不再生效。 modifier: 内容修改器，开发者需要自定义class实现ContentModifier接口。默认值为undefined。

**类型：** ContentModifier&lt;MenuItemConfiguration&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-menuItemContentModifier?: ContentModifier<MenuItemConfiguration>--><!--Device-SelectParams-menuItemContentModifier?: ContentModifier<MenuItemConfiguration>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onSelect

```TypeScript
onSelect?: OnSelectCallback
```

下拉菜单选中某一项的回调。默认值为undefined。

**类型：** [OnSelectCallback](arkts-arkui-onselectcallback-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-onSelect?: OnSelectCallback--><!--Device-SelectParams-onSelect?: OnSelectCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## optionBgColor

```TypeScript
optionBgColor?: ResourceColor
```

下拉菜单项的背景色。默认值：Color.Transparent。当设置了menuItemContentModifier属性时，本属性不生效。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-optionBgColor?: ResourceColor--><!--Device-SelectParams-optionBgColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## optionFont

```TypeScript
optionFont?: Font
```

下拉菜单项的文本样式。默认值：{size: \$r('sys.float.ohos_id_text_size_body1'), weight: FontWeight.Regular}。 当设置了menuItemContentModifier属性时，本属性不生效。

**类型：** Font

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-optionFont?: Font--><!--Device-SelectParams-optionFont?: Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## optionFontColor

```TypeScript
optionFontColor?: ResourceColor
```

下拉菜单项的文本颜色。默认值：\$r('sys.color.ohos_id_color_text_primary')。当设置了menuItemContentModifier属性时，本属性不生效。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-optionFontColor?: ResourceColor--><!--Device-SelectParams-optionFontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## optionHeight

```TypeScript
optionHeight?: Dimension
```

设置下拉菜单显示的最大高度，不支持设置百分比。单位：vp。 下拉菜单的默认最大高度是屏幕可用高度的80%，设置的菜单最大高度不能超过默认最大高度，超过时属性不生效，按默认最大高度显示。

**类型：** Dimension

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-optionHeight?: Dimension--><!--Device-SelectParams-optionHeight?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## optionWidth

```TypeScript
optionWidth?: Dimension | OptionWidthMode
```

设置下拉菜单项的宽度，不支持设置百分比。单位：vp。OptionWidthMode为枚举类型，决定下拉菜单是否继承下拉按钮宽度。 当设置为异常值或小于最小宽度56vp时，属性不生效，菜单项宽度设为默认值，即菜单默认宽度为2栅格。

**类型：** Dimension \| OptionWidthMode

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-optionWidth?: Dimension | OptionWidthMode--><!--Device-SelectParams-optionWidth?: Dimension | OptionWidthMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options?: Array<SelectOption>
```

下拉选项内容。默认值为undefined。

**类型：** Array&lt;SelectOption&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-options?: Array<SelectOption>--><!--Device-SelectParams-options?: Array<SelectOption>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectValue

```TypeScript
selectValue?: ResourceStr
```

设置下拉按钮本身的文本内容。默认值为undefined。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-selectValue?: ResourceStr--><!--Device-SelectParams-selectValue?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: number
```

设置下拉菜单初始选项的索引。第一项的索引为0。当不设置selected属性时，默认选择值为-1，菜单项不选中。

**类型：** number

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-selected?: number--><!--Device-SelectParams-selected?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedOptionBgColor

```TypeScript
selectedOptionBgColor?: ResourceColor
```

下拉菜单选中项的背景色。 默认值：\$r('sys.color.ohos_id_color_component_activated')混合\$r('sys.color.ohos_id_alpha_highlight_bg')的透明度。 当设置了menuItemContentModifier属性时，本属性不生效。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-selectedOptionBgColor?: ResourceColor--><!--Device-SelectParams-selectedOptionBgColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedOptionFont

```TypeScript
selectedOptionFont?: Font
```

下拉菜单选中项的文本样式。默认值：{size: \$r('sys.float.ohos_id_text_size_body1'), weight: FontWeight.Regular}。 当设置了menuItemContentModifier属性时，本属性不生效。

**类型：** Font

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-selectedOptionFont?: Font--><!--Device-SelectParams-selectedOptionFont?: Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedOptionFontColor

```TypeScript
selectedOptionFontColor?: ResourceColor
```

下拉菜单选中项的文本颜色。默认值：\$r('sys.color.ohos_id_color_text_primary_activated')。 当设置了menuItemContentModifier属性时，本属性不生效。

**类型：** ResourceColor

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-selectedOptionFontColor?: ResourceColor--><!--Device-SelectParams-selectedOptionFontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: Length
```

下拉菜单项的文本与箭头之间的间距。默认值：8。单位：vp。

**类型：** Length

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectParams-space?: Length--><!--Device-SelectParams-space?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

