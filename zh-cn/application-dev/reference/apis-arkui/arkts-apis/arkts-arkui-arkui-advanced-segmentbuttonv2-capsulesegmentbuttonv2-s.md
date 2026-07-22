# CapsuleSegmentButtonV2

**起始版本：** 18

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct CapsuleSegmentButtonV2--><!--Device-unnamed-export declare struct CapsuleSegmentButtonV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OnSelectedIndexesChange, TabSegmentButtonV2, SegmentButtonV2Items, MultiCapsuleSegmentButtonV2, OnSelectedIndexChange, SegmentButtonV2ItemOptions, SegmentButtonV2Item, CapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## build

```TypeScript
build(): void
```

Sets the build function of the segmented button.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-build(): void--><!--Device-CapsuleSegmentButtonV2-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $selectedIndex

```TypeScript
$selectedIndex?: OnSelectedIndexChange
```

配置分段按钮选中项变更时触发的回调函数。

**类型：** OnSelectedIndexChange

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-$selectedIndex?: OnSelectedIndexChange--><!--Device-CapsuleSegmentButtonV2-$selectedIndex?: OnSelectedIndexChange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundBlurStyle

```TypeScript
readonly buttonBackgroundBlurStyle?: BlurStyle
```

配置分段按钮背板模糊材质。

默认值：undefined

该成员只读，不支持更改。

**类型：** BlurStyle

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly buttonBackgroundBlurStyle?: BlurStyle--><!--Device-CapsuleSegmentButtonV2-readonly buttonBackgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundBlurStyleOptions

```TypeScript
readonly buttonBackgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

配置分段按钮背板模糊材质配置参数。

默认值：undefined

该成员只读，不支持更改。

**类型：** BackgroundBlurStyleOptions

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly buttonBackgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-CapsuleSegmentButtonV2-readonly buttonBackgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundColor

```TypeScript
readonly buttonBackgroundColor?: ColorMetrics
```

配置分段按钮背板颜色。

默认值：`$r('sys.color.segment_button_v2_tab_button_background')`

值为undefined时，按默认值处理。

该成员只读，不支持更改。

**类型：** ColorMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly buttonBackgroundColor?: ColorMetrics--><!--Device-CapsuleSegmentButtonV2-readonly buttonBackgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundEffect

```TypeScript
readonly buttonBackgroundEffect?: BackgroundEffectOptions
```

配置分段按钮背板模糊配置参数。

默认值：undefined

该成员只读，不支持更改。

**类型：** BackgroundEffectOptions

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly buttonBackgroundEffect?: BackgroundEffectOptions--><!--Device-CapsuleSegmentButtonV2-readonly buttonBackgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonBorderRadius

```TypeScript
readonly buttonBorderRadius?: LengthMetrics
```

配置分段按钮背板的圆角大小。

取值范围：[0, +∞)

默认值：`$r('sys.float.segment_button_v2_background_corner_radius')`

超出取值范围按默认值处理。

该成员只读，不支持更改。

**类型：** LengthMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly buttonBorderRadius?: LengthMetrics--><!--Device-CapsuleSegmentButtonV2-readonly buttonBorderRadius?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonMinHeight

```TypeScript
readonly buttonMinHeight?: LengthMetrics
```

配置分段按钮最小高度。

取值范围：[0, +∞)

默认值：只有纯文本或者纯图标选项时：`$r('sys.float.segment_button_v2_singleline_background_height')`；有图文混合的选项时：`$r('sys.float.segment_button_v2_doubleline_background_height')`

超出取值范围按默认值处理。

该成员只读，不支持更改。

**类型：** LengthMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly buttonMinHeight?: LengthMetrics--><!--Device-CapsuleSegmentButtonV2-readonly buttonMinHeight?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonPadding

```TypeScript
readonly buttonPadding?: LengthMetrics
```

配置分段按钮内边距。

取值范围：[0, +∞)

默认值：`$r('sys.float.padding_level1')`

超出取值范围按默认值处理。

该成员只读，不支持更改。

**类型：** LengthMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly buttonPadding?: LengthMetrics--><!--Device-CapsuleSegmentButtonV2-readonly buttonPadding?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableStateAnimation

```TypeScript
readonly enableStateAnimation?: boolean
```

设置当通过变量修改selectedIndex值时，是否开启分段按钮的属性动画。true表示开启分段按钮的属性动画；未配置该属性或值为false时表示不开启分段按钮的属性动画，使用原有动画。默认值：false该成员只读，不支持更改。

**类型：** boolean

**起始版本：** 24

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly enableStateAnimation?: boolean--><!--Device-CapsuleSegmentButtonV2-readonly enableStateAnimation?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemBorderRadius

```TypeScript
readonly itemBorderRadius?: LengthMetrics
```

配置分段按钮选项的圆角大小。

取值范围：[0, +∞)

默认值：`$r('sys.float.segment_button_v2_selected_corner_radius')`

超出取值范围按默认值处理。

该成员只读，不支持更改。

**类型：** LengthMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemBorderRadius?: LengthMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemBorderRadius?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemFontColor

```TypeScript
readonly itemFontColor?: ColorMetrics
```

配置分段按钮选中项的字体颜色。

默认值：`$r('sys.color.font_primary')`

值为undefined时，按默认值处理。

**说明：**

items设置textModifier的fontColor属性值时，itemSelectedFontColor不生效。

该成员只读，不支持更改。

**类型：** ColorMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemFontColor?: ColorMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemFontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemFontSize

```TypeScript
readonly itemFontSize?: LengthMetrics
```

配置分段按钮非选中选项的字体大小。

取值范围：[0, +∞)

默认值：`14fp`

**说明：**

不支持设置百分比类型，异常值按默认值处理。

items设置textModifier的fontSize属性值时，itemFontSize不生效。

该成员只读，不支持更改。

**类型：** LengthMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemFontSize?: LengthMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemFontSize?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemFontWeight

```TypeScript
readonly itemFontWeight?: FontWeight
```

配置分段按钮非选中选项的字体字重。

默认值：FontWeight.Medium

超出取值范围按默认值处理。

**说明：**

items设置textModifier的fontWeight属性值时，itemFontWeight不生效。

该成员只读，不支持更改。

**类型：** FontWeight

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemFontWeight?: FontWeight--><!--Device-CapsuleSegmentButtonV2-readonly itemFontWeight?: FontWeight-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemIconFillColor

```TypeScript
readonly itemIconFillColor?: ColorMetrics
```

配置分段按钮非选中的选项图标颜色。

默认值：`$r('sys.color.font_secondary')`

值为undefined时，按默认值处理。

**说明：**

items设置iconModifier的fillColor属性值时，itemIconFillColor不生效。

该成员只读，不支持更改。

**类型：** ColorMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemIconFillColor?: ColorMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemIconFillColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemIconSize

```TypeScript
readonly itemIconSize?: SizeT<LengthMetrics>
```

配置分段按钮选项中Image类型的图标大小。

取值范围：[0, +∞)

默认值：`{ width: LengthMetrics.vp(24), height: LengthMetrics.vp(24) }`

超出取值范围按默认值处理。

**说明：**

items设置iconModifier的width、height属性值时，itemIconSize不生效。

该成员只读，不支持更改。

**类型：** SizeT&lt;LengthMetrics&gt;

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemIconSize?: SizeT<LengthMetrics>--><!--Device-CapsuleSegmentButtonV2-readonly itemIconSize?: SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemMaxFontScale

```TypeScript
readonly itemMaxFontScale?: number | Resource
```

配置分段按钮选项文字大小的最大放大倍数。

取值范围：[1, 2]

默认值：1

**说明：**

设置的值小于 1 时，按值为 1 处理，设置的值大于 2，按值为 2 处理，异常值默认不生效。

该成员只读，不支持更改。

**类型：** number \| Resource

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemMaxFontScale?: number | Resource--><!--Device-CapsuleSegmentButtonV2-readonly itemMaxFontScale?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemMinFontScale

```TypeScript
readonly itemMinFontScale?: number | Resource
```

配置分段按钮选项文字大小的最小字体缩放倍数。

取值范围：[0, 1]

默认值：0

**说明：**

设置的值小于 0 时，按值为 0 处理，设置的值大于 1，按值为 1 处理，异常值默认不生效。

该成员只读，不支持更改。

**类型：** number \| Resource

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemMinFontScale?: number | Resource--><!--Device-CapsuleSegmentButtonV2-readonly itemMinFontScale?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemMinHeight

```TypeScript
readonly itemMinHeight?: LengthMetrics
```

配置分段按钮选项最小高度。

取值范围：[0, +∞)

默认值：

只有纯文本或者纯图标选项时：`$r('sys.float.segment_button_v2_singleline_selected_height')`；有图文混合的选项时：`$r('sys.float.segment_button_v2_doubleline_selected_height')`

超出取值范围按默认值处理。

该成员只读，不支持更改。

**类型：** LengthMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemMinHeight?: LengthMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemMinHeight?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemPadding

```TypeScript
readonly itemPadding?: LocalizedPadding
```

配置分段按钮选项内边距。

默认值：`{ top: LengthMetrics.resource($r('sys.float.padding_level2')), bottom: LengthMetrics.resource($r('sys.float.padding_level2')), start: LengthMetrics.resource($r('sys.float.padding_level4')), end: LengthMetrics.resource($r('sys.float.padding_level4')) }`

值为undefined时，按默认值处理。

该成员只读，不支持更改。

**类型：** LocalizedPadding

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemPadding?: LocalizedPadding--><!--Device-CapsuleSegmentButtonV2-readonly itemPadding?: LocalizedPadding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedBackgroundColor

```TypeScript
readonly itemSelectedBackgroundColor?: ColorMetrics
```

配置分段按钮选中的选项背景颜色。

默认值：`$r('sys.color.segment_button_v2_tab_selected_item_background')`

值为undefined时，按默认值处理。

该成员只读，不支持更改。

**类型：** ColorMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemSelectedBackgroundColor?: ColorMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemSelectedBackgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedFontColor

```TypeScript
readonly itemSelectedFontColor?: ColorMetrics
```

配置分段按钮选中项的字体颜色。

默认值：`$r('sys.color.font_primary')`

值为undefined时，按默认值处理。

**说明：**

items设置textModifier的fontColor属性值时，itemSelectedFontColor不生效。

该成员只读，不支持更改。

**类型：** ColorMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemSelectedFontColor?: ColorMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemSelectedFontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedFontSize

```TypeScript
readonly itemSelectedFontSize?: LengthMetrics
```

配置分段按钮选中项的字体大小。

取值范围：[0, +∞)

默认值：`14fp`

**说明：**

不支持设置百分比类型，异常值按默认值处理。

items设置textModifier的fontSize属性值时，itemSelectedFontSize不生效。

该成员只读，不支持更改。

**类型：** LengthMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemSelectedFontSize?: LengthMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemSelectedFontSize?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedFontWeight

```TypeScript
readonly itemSelectedFontWeight?: FontWeight
```

配置分段按钮选中项的字体字重。

默认值：FontWeight.Medium

超出取值范围按默认值处理。

**说明：**

items设置textModifier的fontWeight属性值时，itemSelectedFontWeight不生效。

该成员只读，不支持更改。

**类型：** FontWeight

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemSelectedFontWeight?: FontWeight--><!--Device-CapsuleSegmentButtonV2-readonly itemSelectedFontWeight?: FontWeight-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedIconFillColor

```TypeScript
readonly itemSelectedIconFillColor?: ColorMetrics
```

配置分段按钮选中的选项图标颜色。

默认值：`$r('sys.color.font_primary')`

值为undefined时，按默认值处理。

**说明：**

items设置iconModifier的fillColor属性值时，itemSelectedIconFillColor不生效。

该成员只读，不支持更改。

**类型：** ColorMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemSelectedIconFillColor?: ColorMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemSelectedIconFillColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedSymbolFontColor

```TypeScript
readonly itemSelectedSymbolFontColor?: ColorMetrics
```

配置分段按钮选中选项的HM Symbol类型图标颜色。

默认值：`$r('sys.color.font_primary')`

值为undefined时，按默认值处理。

**说明：**

items设置symbolModifier的fontColor属性值时，itemSelectedSymbolFontColor不生效。

该成员只读，不支持更改。

**类型：** ColorMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemSelectedSymbolFontColor?: ColorMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemSelectedSymbolFontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemShadow

```TypeScript
readonly itemShadow?: ShadowOptions | ShadowStyle
```

配置分段按钮选项阴影。

默认值：ShadowStyle.OUTER_DEFAULT_XS

超出取值范围按默认值处理。

该成员只读，不支持更改。

**类型：** ShadowOptions \| ShadowStyle

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemShadow?: ShadowOptions | ShadowStyle--><!--Device-CapsuleSegmentButtonV2-readonly itemShadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSpace

```TypeScript
readonly itemSpace?: LengthMetrics
```

配置分段按钮选项之间的间隔。

取值范围：[0, +∞)

默认值：`LengthMetrics.vp(0)`

**说明：**

不支持设置百分比类型，异常值按默认值处理。

该成员只读，不支持更改。

**类型：** LengthMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemSpace?: LengthMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemSpace?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSymbolFontColor

```TypeScript
readonly itemSymbolFontColor?: ColorMetrics
```

配置分段按钮非选中选项HM Symbol类型图标的颜色。

默认值：`$r('sys.color.font_secondary')`

值为undefined时，按默认值处理。

**说明：**

items设置symbolModifier的fontColor属性值时，itemSymbolFontColor不生效。

该成员只读，不支持更改。

**类型：** ColorMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemSymbolFontColor?: ColorMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemSymbolFontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSymbolFontSize

```TypeScript
readonly itemSymbolFontSize?: LengthMetrics
```

配置分段按钮选项中HM Symbol类型图标大小。

取值范围：[0, +∞)

默认值：`20fp`

**说明：**

不支持设置百分比类型，异常值按默认值处理。

items设置symbolModifier的fontSize属性值时，itemSymbolFontSize不生效。

该成员只读，不支持更改。

**类型：** LengthMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly itemSymbolFontSize?: LengthMetrics--><!--Device-CapsuleSegmentButtonV2-readonly itemSymbolFontSize?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
readonly items: SegmentButtonV2Items
```

配置分段按钮的选项集合信息。

值为undefined时，不显示选项信息。

该成员只读，不支持更改。

**类型：** SegmentButtonV2Items

**起始版本：** 18

**装饰器类型：** @Require、@Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly items: SegmentButtonV2Items--><!--Device-CapsuleSegmentButtonV2-readonly items: SegmentButtonV2Items-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## languageDirection

```TypeScript
readonly languageDirection?: Direction
```

配置分段按钮的布局方向。

默认值：Direction.Auto

超出取值范围按默认值处理。

该成员只读，不支持更改。

**类型：** Direction

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly languageDirection?: Direction--><!--Device-CapsuleSegmentButtonV2-readonly languageDirection?: Direction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onItemClicked

```TypeScript
onItemClicked?: Callback<number>
```

配置分段按钮选项被单击时触发的回调函数。

**类型：** Callback&lt;number&gt;

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-onItemClicked?: Callback<number>--><!--Device-CapsuleSegmentButtonV2-onItemClicked?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
readonly selectedIndex: number
```

配置分段按钮被选中的选项下标，第一项的编号为0，之后顺序增加。

值为undefined时，不选中任何选项，其他非正数值，默认选项下标为0。

该成员只读，不支持更改。

**类型：** number

**起始版本：** 18

**装饰器类型：** @Require、@Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CapsuleSegmentButtonV2-readonly selectedIndex: number--><!--Device-CapsuleSegmentButtonV2-readonly selectedIndex: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

