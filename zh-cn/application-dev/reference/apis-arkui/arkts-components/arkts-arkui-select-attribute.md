# Select属性/事件

除支持通用属性外，还支持以下属性：

**继承/实现关系：** SelectAttribute extends CommonMethod<SelectAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## arrowModifier

```TypeScript
arrowModifier(modifier: Optional<SymbolGlyphModifier>)
```

定制Select按钮下拉箭头图标样式的方法，在应用arrowModifier之后，Select按钮下拉箭头的图标样式将完全由开发者自定义。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;SymbolGlyphModifier&gt; | 是 | 在Select组件上，定制Select按钮下拉箭头图标样式的方法。 当modifier的值为undefined时， 不自定义下拉箭头图标样式。 |

## arrowPosition

```TypeScript
arrowPosition(value: ArrowPosition)
```

设置下拉菜单项的文本与箭头之间的对齐方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ArrowPosition](arkts-arkui-arrowposition-e.md) | 是 | 下拉菜单项的文本与箭头之间的对齐方式。默认值：ArrowPosition.END |

## arrowPosition

```TypeScript
arrowPosition(position: Optional<ArrowPosition>)
```

设置下拉菜单项的文本与箭头之间的对齐方式。与[arrowPosition](#arrowposition)相比，position参数新增了对 undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Optional](arkts-arkui-optional-t.md)&lt;[ArrowPosition](arkts-arkui-arrowposition-e.md)&gt; | 是 | 下拉菜单项的文本与箭头之间的对齐方式。当position的值为undefined时，默认值：ArrowPosition.END |

## avoidance

```TypeScript
avoidance(mode: AvoidanceMode)
```

设置下拉菜单的避让模式。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [AvoidanceMode](arkts-arkui-avoidancemode-e.md) | 是 | 设置下拉菜单的避让模式。默认值：AvoidanceMode.COVER_TARGET |

## controlSize

```TypeScript
controlSize(value: ControlSize)
```

设置Select组件的尺寸。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ControlSize](arkts-arkui-controlsize-e.md) | 是 | Select组件的尺寸。默认值：ControlSize.NORMAL |

## controlSize

```TypeScript
controlSize(size: Optional<ControlSize>)
```

设置Select组件的尺寸。与[controlSize](#controlsize)&lt;sup&gt;12+&lt;/sup&gt;相比，size参数新增了对 undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [Optional](arkts-arkui-optional-t.md)&lt;[ControlSize](arkts-arkui-controlsize-e.md)&gt; | 是 | Select组件的尺寸。当size的值为undefined时，默认值为ControlSize.NORMAL。 |

## divider

```TypeScript
divider(options: Optional<DividerOptions> | null)
```

设置分割线样式，不设置该属性则按“默认值”展示分割线。该属性与dividerStyle冲突，如果同时设置，按调用顺序生效，后者覆盖前者。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;[DividerOptions](arkts-arkui-divideroptions-i.md)&gt; \| null | 是 | 1.设置DividerOptions，则按设置的样式显示分割线。 默认值：{strokeWidth: '1px' , color: '#33182431'} 2.设置为null时，不显示分割线。 3.strokeWidth设置过宽时，会覆盖文字。分割线会从每一个 Item底部开始，同时向上向下画分割线。 4.startMargin和endMargin的默认值与不设置divider属性时的分割线样式保持一致。startMargin和endMargin的和与 optionWidth的值相等时，不显示分割线。 startMargin和endMargin的和超过optionWidth的值时，按照默认样式显示分割线。 |

## dividerStyle

```TypeScript
dividerStyle(style: Optional<DividerStyleOptions>)
```

设置分割线样式，不设置该属性则按“默认值”展示分割线。该属性与divider冲突，如果同时设置，按调用顺序生效，后者覆盖前者。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[DividerStyleOptions](../arkts-apis/arkts-arkui-dividerstyleoptions-i.md)&gt; | 是 | 1.设置DividerStyleOptions，则按设置的样式显示分割线。 默认值：{strokeWidth: '1px' , color: '#33182431'} 2.设置为null或undefined时，展示默认分割线。 3.当mode为FLOAT_ABOVE_MENU时， strokeWidth设置过宽时，会覆盖文字。分割线会从每一个Item底部开始，同时向上向下画分割线。当mode为EMBEDDED_IN_MENU时，分割线在Menu中展开，独立占用高度。 4.startMargin和endMargin的默认值与不设置divider属性时的分割线样式保持一致。startMargin和endMargin的和与optionWidth的值相等时，不显示分割线。startMargin和 endMargin的和超过optionWidth的值时，按照默认样式显示分割线。 |

## font

```TypeScript
font(value: Font)
```

设置下拉按钮本身的文本样式。当size为0时，文本不显示，当size为负值时，文本的size按照默认值显示。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Font | 是 | 下拉按钮本身的文本样式。API version 11及以前默认值：{size:  `\\$r('sys.float.ohos_id_text_size_button1')`,weight: FontWeight.Medium} API version 12以后，如果设置 controlSize的值为：controlSize.SMALL，size默认值是`\\$r('sys.float.ohos_id_text_size_button2')`，否则为 `\\$r('sys.float.ohos_id_text_size_button1')`。 |

## font

```TypeScript
font(selectFont: Optional<Font>)
```

设置下拉按钮本身的文本样式。当size为0时，文本不显示，当size为负值时，文本的size按照默认值显示。与[font](#font)相比，selectFont 参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectFont | [Optional](arkts-arkui-optional-t.md)&lt;Font&gt; | 是 | 下拉按钮本身的文本样式。如果设置controlSize的值为：controlSize.SMALL，size默认值是 `\\$r('sys.float.ohos_id_text_size_button2')`，否则为`\\$r('sys.float.ohos_id_text_size_button1')`。当selectFont的值为 undefined时，恢复为系统文本样式。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置下拉按钮本身的文本颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉按钮本身的文本颜色。默认值：`\\$r('sys.color.ohos_id_color_text_primary')`混合 `\\$r('sys.color.ohos_id_alpha_content_primary')`的透明度。 |

## fontColor

```TypeScript
fontColor(resColor: Optional<ResourceColor>)
```

设置下拉按钮本身的文本颜色。与[fontColor](#fontcolor)相比，resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 下拉按钮本身的文本颜色。当resColor的值为undefined时，默认值： `\\$r('sys.color.ohos_id_color_text_primary')`混合`\\$r('sys.color.ohos_id_alpha_content_primary')`的透明度。当value的值 为undefined时，维持上次取值。 |

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode(mode: Optional<MenuKeyboardAvoidMode>)
```

设置下拉菜单是否避让软键盘。未通过该接口设置时，默认不避让软键盘。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;[MenuKeyboardAvoidMode](arkts-arkui-menukeyboardavoidmode-e.md)&gt; | 是 | 设置下拉菜单是否避让软键盘。取值为undefined时，按照MenuKeyboardAvoidMode.NONE处理，不避让软键盘。各枚举值的具体效果参见MenuKeyboardAvoidMode枚举说明。 |

## menuAlign

```TypeScript
menuAlign(alignType: MenuAlignType, offset?: Offset)
```

设置下拉按钮与下拉菜单间的对齐方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignType | [MenuAlignType](arkts-arkui-menualigntype-e.md) | 是 | 对齐方式类型。默认值：MenuAlignType.START |
| offset | Offset | 否 | 按照对齐类型对齐后，下拉菜单相对下拉按钮的偏移量。dx控制水平方向偏移，dy控制垂直方向偏移。默认值：{dx: 0, dy: 0} |

## menuAlign

```TypeScript
menuAlign(alignType: Optional<MenuAlignType>, offset?: Offset)
```

设置下拉按钮与下拉菜单间的对齐方式。与[menuAlign](#menualign)&lt;sup&gt;10+&lt;/sup&gt;相比，alignType参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignType | [Optional](arkts-arkui-optional-t.md)&lt;[MenuAlignType](arkts-arkui-menualigntype-e.md)&gt; | 是 | 对齐方式类型。当alignType的值为undefined时，默认值：MenuAlignType.START |
| offset | Offset | 否 | 按照对齐类型对齐后，下拉菜单相对下拉按钮的偏移量。默认值：{dx: 0, dy: 0} |

## menuBackgroundBlurStyle

```TypeScript
menuBackgroundBlurStyle(value: BlurStyle)
```

设置下拉菜单的背景模糊材质。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BlurStyle | 是 | 下拉菜单的背景模糊材质。默认值：BlurStyle.COMPONENT_ULTRA_THICK |

## menuBackgroundBlurStyle

```TypeScript
menuBackgroundBlurStyle(style: Optional<BlurStyle>)
```

设置下拉菜单的背景模糊材质。与[menuBackgroundBlurStyle](#menubackgroundblurstyle)&lt;sup&gt;11+&lt;/ sup&gt;相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;BlurStyle&gt; | 是 | 下拉菜单的背景模糊材质。当style的值为undefined时，默认值：BlurStyle.COMPONENT_ULTRA_THICK |

## menuBackgroundBlurStyleOptions

```TypeScript
menuBackgroundBlurStyleOptions(blurStyle: Optional<BackgroundBlurStyleOptions>)
```

设置Select组件的背景模糊效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurStyle | [Optional](arkts-arkui-optional-t.md)&lt;[BackgroundBlurStyleOptions](arkts-arkui-backgroundblurstyleoptions-i.md)&gt; | 是 | 设置Select组件的背景模糊效果。 |

## menuBackgroundColor

```TypeScript
menuBackgroundColor(value: ResourceColor)
```

设置下拉菜单的背景色。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉菜单的背景色。默认值：API version 11之前，默认值为\\$r('sys.color.ohos_id_color_card_bg')。 API version 11及之后，默认值为Color.Transparent。 |

## menuBackgroundColor

```TypeScript
menuBackgroundColor(resColor: Optional<ResourceColor>)
```

设置下拉菜单的背景色。与[menuBackgroundColor](#menubackgroundcolor)&lt;sup&gt;11+&lt;/sup&gt;相比， resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 下拉菜单的背景色。当resColor的值为undefined时，默认值为Color.Transparent。 |

## menuBackgroundEffect

```TypeScript
menuBackgroundEffect(effect: Optional<BackgroundEffectOptions>)
```

设置Select组件的背景属性。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [Optional](arkts-arkui-optional-t.md)&lt;[BackgroundEffectOptions](arkts-arkui-backgroundeffectoptions-i.md)&gt; | 是 | 设置Select组件的背景属性，包括：模糊半径、亮度、饱和度和颜色。 |

## menuItemContentModifier

```TypeScript
menuItemContentModifier(modifier: ContentModifier<MenuItemConfiguration>)
```

定制Select下拉菜单项内容区的方法。在应用了menuItemContentModifier后，下拉菜单的内容将完全由开发者自定义，此时为Select组件设置的分割线、选项颜色及下拉菜单的字体颜色等属性将不再生效。适用于下拉菜单项需要展示图文混排、多行文本、复杂图标或内置控件等复杂布局的场景。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;[MenuItemConfiguration](arkts-arkui-menuitemconfiguration-i.md)&gt; | 是 | 在Select组件上，定制下拉菜单项内容区的方法。modifier：内容修改器，开发者需要自定义 class实现ContentModifier接口。 |

## menuItemContentModifier

```TypeScript
menuItemContentModifier(modifier: Optional<ContentModifier<MenuItemConfiguration>>)
```

定制Select下拉菜单项内容区的方法。与 [menuItemContentModifier](#menuitemcontentmodifier) &lt;sup&gt;12+&lt;/sup&gt;相比，modifier参数新增了对undefined类型的支持。在应用了menuItemContentModifier后，下拉菜单的内容将完全由开发者自定义，此时为Select组件设置的分割线、选项颜色 及下拉菜单的字体颜色等属性将不再生效。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;[ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;[MenuItemConfiguration](arkts-arkui-menuitemconfiguration-i.md)&gt;&gt; | 是 | 在Select组件上，定制下拉菜单项内容区的方法。modifier：内容修改 器，开发者需要自定义class实现ContentModifier接口。当modifier的值为undefined或null时，不使用内容修改器。 |

## menuOutline

```TypeScript
menuOutline(outline: MenuOutlineOptions)
```

设置下拉菜单框的外描边样式。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outline | [MenuOutlineOptions](arkts-arkui-menuoutlineoptions-i.md) | 是 | 下拉菜单框的外描边样式。 |

## minKeyboardAvoidDistance

```TypeScript
minKeyboardAvoidDistance(distance: Optional<LengthMetrics>)
```

设置Select的菜单避让软键盘的最小距离。未通过该接口设置，最小距离默认为8vp。仅当[keyboardAvoidMode](#keyboardavoidmode)设置为避让软键盘时生 效。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (index: number, value: string) = & gt; void | 是 |  |

## onSelect

```TypeScript
onSelect(callback: Optional<OnSelectCallback>)
```

下拉菜单选中某一项时，会触发回调。与onSelect相比， callback参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;[OnSelectCallback](arkts-arkui-onselectcallback-t.md)&gt; | 是 | 下拉菜单选中某一项的回调。当callback的值为undefined时，不使用回调函数。 |

## optionBgColor

```TypeScript
optionBgColor(value: ResourceColor)
```

设置下拉菜单项的背景色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉菜单项的背景色。默认值：API version 11之前，默认值为Color.White。API version 11及之后，默认 值为Color.Transparent。 |

## optionBgColor

```TypeScript
optionBgColor(resColor: Optional<ResourceColor>)
```

设置下拉菜单项的背景色。与[optionBgColor](#optionbgcolor)相比，resColor参数新增了对undefined类型 的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 下拉菜单项的背景色。当resColor的值为undefined时，下拉菜单项的背景色为Color.White。 |

## optionFont

```TypeScript
optionFont(value: Font)
```

设置下拉菜单项的文本样式。当size为0的时候，文本不显示，当size为负值的时候，文本的size按照默认值显示。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Font | 是 | 下拉菜单项的文本样式。默认值：{size: \\$r('sys.float.ohos_id_text_size_body1'),weight:  FontWeight.Regular} |

## optionFont

```TypeScript
optionFont(selectFont: Optional<Font>)
```

设置下拉菜单项的文本样式。当size为0的时候，文本不显示，当size为负值的时候，文本的size按照默认值显示。与[optionFont](#optionfont)相比，selectFont参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectFont | [Optional](arkts-arkui-optional-t.md)&lt;Font&gt; | 是 | 下拉菜单项的文本样式。当selectFont的值为undefined时，默认值：{size: \\$r('sys.float.ohos_id_text_size_body1'),weight: FontWeight.Regular} |

## optionFontColor

```TypeScript
optionFontColor(value: ResourceColor)
```

设置下拉菜单项的文本颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉菜单项的文本颜色。默认值：\\$r('sys.color.ohos_id_color_text_primary') |

## optionFontColor

```TypeScript
optionFontColor(resColor: Optional<ResourceColor>)
```

设置下拉菜单项的文本颜色。与[optionFontColor](#optionfontcolor)相比，resColor参数新增了对 undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 下拉菜单项的文本颜色。当resColor的值为undefined时，默认值：\\$r('sys.color.ohos_id_color_text_primary') |

## optionHeight

```TypeScript
optionHeight(value: Dimension)
```

设置下拉菜单显示的最大高度，不支持设置百分比。默认最大高度是屏幕可用高度的80%，设置的菜单最大高度不能超过默认最大高度。当设置为无效值或零时，属性不生效。如果下拉菜单所有选项的实际高度小于设定的高度，下拉菜单的高度按实际高度显示。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 下拉菜单显示的最大高度。 |

## optionHeight

```TypeScript
optionHeight(height: Optional<Dimension>)
```

设置下拉菜单显示的最大高度，不支持设置百分比。默认最大高度是屏幕可用高度的80%，设置的菜单最大高度不能超过默认最大高度。与 [optionHeight](#optionheight)&lt;sup&gt;11+&lt;/sup&gt;相比，height参数新增了对undefined类型的支持。当设置为无效值或零时，属性不生效。如果下拉菜单所有选项的实际高度小于设定的高度，下拉菜单的高度按实际高度显示。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-optional-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt; | 是 | 下拉菜单显示的最大高度。当height的值为undefined时，属性不生效，下拉菜单最大高度设为默认值，即下拉菜单最大高度默认值为屏幕可用 高度的80%。 |

## optionTextModifier

```TypeScript
optionTextModifier(modifier: Optional<TextModifier>)
```

定制Select下拉菜单未选中项文本样式的方法，在应用optionTextModifier之后，下拉菜单未选中项的文本样式将完全由开发者自定义。如果[optionFont](#optionfont)与optionTextModifier的Font属性同时设置，则优先使用 [optionFont](#optionfont)设置下拉菜单未选中项的文本样式； [optionFont](#optionfont)中缺省的属性将设置为对应的默认值。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;[TextModifier](../arkts-apis/arkts-arkui-textmodifier-c.md)&gt; | 是 | 在Select组件上，定制Select下拉菜单未选中项文本样式的方法。 当modifier的值为undefined时，不自定义下拉菜单 未选中项的文本样式。 |

## optionWidth

```TypeScript
optionWidth(value: Dimension | OptionWidthMode )
```

设置下拉菜单项的宽度，不支持设置百分比。OptionWidthMode类型为枚举类型，OptionWidthMode决定下拉菜单是否继承下拉按钮宽度。当设置为无效值或小于最小宽度56vp时，属性无效，菜单项宽度设为默认值，即2栅格。Select组件距屏幕边缘的左右间距为16vp，建议将组件本身及菜单项的宽度设置为小于等于`calc(100% - 32vp)`的值，以避免下拉菜单弹出时发生偏移。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) \| [OptionWidthMode](../arkts-apis/arkts-arkui-optionwidthmode-e.md) | 是 | 下拉菜单项的宽度。 |

## optionWidth

```TypeScript
optionWidth(width: Optional<Dimension | OptionWidthMode> )
```

设置下拉菜单项的宽度，不支持设置百分比。OptionWidthMode类型为枚举类型，OptionWidthMode决定下拉菜单是否继承下拉按钮宽度。与 [optionWidth](#optionwidth)&lt;sup&gt;11+&lt;/sup&gt;相比，width参数新增了对 undefined类型的支持。当设置为无效值或小于最小宽度56vp时，属性无效，菜单项宽度设为默认值，即2栅格。Select组件距屏幕边缘的左右间距为16vp，建议将组件本身及菜单项的宽度设置为小于等于`calc(100% - 32vp)`的值，以避免下拉菜单弹出时发生偏移。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-optional-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md) \| [OptionWidthMode](../arkts-apis/arkts-arkui-optionwidthmode-e.md)&gt; | 是 | 下拉菜单项的宽度。当width的值为undefined时，属性无效，菜单项宽度设为默认值，即2栅格。 |

## selected

```TypeScript
selected(value: number | Resource)
```

设置下拉菜单初始选项的索引，第一项的索引为0。当不设置selected属性、或设置为负数、非整数、超出索引范围等异常值时，默认选中值为-1，菜单项不选中；当设置为undefined、null时，选中第一项。从API version 10开始，该属性支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。从API version 18开始，该属性支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| Resource | 是 | 下拉菜单初始选项的索引，索引值从0开始。<br>**起始版本：** 11 |

## selected

```TypeScript
selected(numCount: Optional<number | Resource>)
```

设置下拉菜单初始选项的索引，第一项的索引为0。当不设置selected属性、或设置为负数、非整数、超出索引范围等异常值时，默认选中值为-1，菜单项不选中；当设置为undefined、null时，选中第一项。该属性支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)、 [!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| numCount | [Optional](arkts-arkui-optional-t.md)&lt;number \| Resource & gt; | 是 | 下拉菜单初始选项的索引，索引值从0开始。当numCount的值为undefined或null时，选中第一项。 |

## selectedOptionBgColor

```TypeScript
selectedOptionBgColor(value: ResourceColor)
```

设置下拉菜单选中项的背景色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉菜单选中项的背景色。默认值：`\\$r('sys.color.ohos_id_color_component_activated')`混合 `\\$r('sys.color.ohos_id_alpha_highlight_bg')`的透明度。 |

## selectedOptionBgColor

```TypeScript
selectedOptionBgColor(resColor: Optional<ResourceColor>)
```

设置下拉菜单选中项的背景色。与[selectedOptionBgColor](#selectedoptionbgcolor)相比， resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 下拉菜单选中项的背景色。当resColor的值为undefined时，默认值： `\\$r('sys.color.ohos_id_color_component_activated')`混合`\\$r('sys.color.ohos_id_alpha_highlight_bg')`的透明度。 |

## selectedOptionFont

```TypeScript
selectedOptionFont(value: Font)
```

设置下拉菜单选中项的文本样式。当size为0的时候，文本不显示，当size为负值的时候，文本的size按照默认值显示。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Font | 是 | 下拉菜单选中项的文本样式。默认值：{size: \\$r('sys.float.ohos_id_text_size_body1'),weight:  FontWeight.Regular} |

## selectedOptionFont

```TypeScript
selectedOptionFont(selectFont: Optional<Font>)
```

设置下拉菜单选中项的文本样式。当size为0的时候，文本不显示，当size为负值的时候，文本的size按照默认值显示。与 [selectedOptionFont](#selectedoptionfont)相比，selectFont参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectFont | [Optional](arkts-arkui-optional-t.md)&lt;Font&gt; | 是 | 下拉菜单选中项的文本样式。当selectFont的值为undefined时，默认值：{size: \\$r('sys.float.ohos_id_text_size_body1'),weight: FontWeight.Regular} |

## selectedOptionFontColor

```TypeScript
selectedOptionFontColor(value: ResourceColor)
```

设置下拉菜单选中项的文本颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 下拉菜单选中项的文本颜色。默认值：\\$r('sys.color.ohos_id_color_text_primary_activated') |

## selectedOptionFontColor

```TypeScript
selectedOptionFontColor(resColor: Optional<ResourceColor>)
```

设置下拉菜单选中项的文本颜色。与[selectedOptionFontColor](#selectedoptionfontcolor)相比， resColor参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 下拉菜单选中项的文本颜色。当resColor的值为undefined时，默认值为\\$r('sys.color.ohos_id_color_text_primary_activated')。 |

## selectedOptionTextModifier

```TypeScript
selectedOptionTextModifier(modifier: Optional<TextModifier>)
```

定制Select下拉菜单选中项文本样式的方法，在应用selectedOptionTextModifier之后，下拉菜单选中项的文本样式将完全由开发者自定义。如果[selectedOptionFont](#selectedoptionfont)与selectedOptionTextModifier的Font属性同时设 置，则优先使用[selectedOptionFont](#selectedoptionfont)设置下拉菜单选中项的文本样式；若未设置 [selectedOptionFont](#selectedoptionfont)，则优先使用 [optionFont](#optionfont)设置下拉菜单选中项的文本样式。其中 [selectedOptionFont](#selectedoptionfont)或者 [optionFont](#optionfont)缺省的属性将设置为对应的默认值。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;[TextModifier](../arkts-apis/arkts-arkui-textmodifier-c.md)&gt; | 是 | 设置下拉菜单项选中项的文本样式。开发者可以根据需要管理和维护文本的样式进行设置。 当modifier的值为 undefined时，不自定义下拉菜单项选中项的文本样式。 |

## showDefaultSelectedIcon

```TypeScript
showDefaultSelectedIcon(show: boolean)
```

设置是否显示默认选择的图标。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| show | boolean | 是 | 是否显示默认选定的图标。true：显示默认选择的图标；false：不显示默认选择的图标，通过突出显示背景色来表示选中。默认值：false当show为 true时，若设置了selectedOptionBgColor选中项的背景色时，则同时显示选中项的背景色和默认选定的图标；若未通过selectedOptionBgColor设置选中项的背景色时，不突出显示背景色，只显示默认 选定的图标。 |

## showInSubWindow

```TypeScript
showInSubWindow(showInSubWindow: Optional<boolean>)
```

设置下拉菜单是否显示在子窗中。未通过该接口设置时，下拉菜单默认不显示在子窗中。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| showInSubWindow | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置下拉菜单是否显示在子窗中。true代表下拉菜单显示在子窗中。false代表下拉菜单不显示在子窗中。 |

## space

```TypeScript
space(value: Length)
```

设置下拉菜单项的文本与箭头的间距。不支持设置百分比。将间距设置为null、undefined，或者小于等于8的值时，取默认值。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 下拉菜单项的文本与箭头的间距。默认值：8   **说明：** 设置string类型时，不支持百分比。 |

## space

```TypeScript
space(spaceLength: Optional<Length>)
```

设置下拉菜单项的文本与箭头的间距。不支持设置百分比。设置为null、undefined，或者小于等于8的值，取默认值。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spaceLength | [Optional](arkts-arkui-optional-t.md)&lt;[Length](../arkts-apis/arkts-arkui-length-t.md)&gt; | 是 | 下拉菜单项的文本与箭头之间的间距。当spaceLength的值为undefined时，默认值：8 |

## textModifier

```TypeScript
textModifier(modifier: Optional<TextModifier>)
```

定制Select按钮文本样式的方法，在应用了textModifier之后，Select按钮的文本样式将完全由开发者自定义。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;[TextModifier](../arkts-apis/arkts-arkui-textmodifier-c.md)&gt; | 是 | 在Select组件上，定制按钮文本样式的方法。 当modifier的值为undefined时，不自定义文本样式。 |

## value

```TypeScript
value(value: ResourceStr)
```

设置下拉按钮的文本内容。选中菜单项后，按钮文本将自动更新为选中的菜单项文本。从API version 10开始，该参数支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 下拉按钮本身的文本内容。   **说明：** 文本长度大于列宽时，文本被截断。<br>**起始版本：** 11 |

## value

```TypeScript
value(resStr: Optional<ResourceStr>)
```

设置下拉按钮的文本内容。选中菜单项后，按钮文本将自动更新为选中的菜单项文本。与[value](#value)相比，resStr参数新增了对 undefined类型的支持。该参数支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)、 [!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resStr | [Optional](arkts-arkui-optional-t.md)&lt;[ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)&gt; | 是 | 下拉按钮本身的文本内容。当resStr的值为undefined时维持上次取值。 |
