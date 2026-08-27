# MultiCapsuleSegmentButtonV2

分段按钮组件用于创建页签型、单选或多选的胶囊型分段按钮，支持文本、图标、Symbol等多种选项类型及图文混合配置，可自定义字体、颜色、圆角等样式。页签型分段按钮适用于页签切换场景，单选胶囊型分段按钮适用于单选切换场景，多选胶囊型分段按 钮适用于多选筛选场景。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SegmentButtonV2ItemOptions, OnSelectedIndexChange, OnSelectedIndexesChange, SegmentButtonV2Item, SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## $selectedIndexes

```TypeScript
$selectedIndexes: OnSelectedIndexesChange
```

配置分段按钮选中项变更时触发的回调函数。默认值：undefined，未设置时不触发回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

Sets the build function of the segmented button.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemBackgroundBlurStyle

```TypeScript
readonly itemBackgroundBlurStyle?: BlurStyle
```

配置分段按钮选项的模糊材质。默认值：undefined该成员只读，不支持更改。

**类型：** BlurStyle

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemBackgroundBlurStyleOptions

```TypeScript
readonly itemBackgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

配置分段按钮选项的模糊材质配置参数。默认值：undefined该成员只读，不支持更改。

**类型：** [BackgroundBlurStyleOptions](../arkts-components/arkts-arkui-backgroundblurstyleoptions-i.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemBackgroundColor

```TypeScript
readonly itemBackgroundColor?: ColorMetrics
```

配置分段按钮非选中的选项背板颜色。默认值：`\$r('sys.color.segment_button_v2_multi_capsule_button_background')`值为undefined时，按默认值处理。该成员只读，不支持更改。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemBackgroundEffect

```TypeScript
readonly itemBackgroundEffect?: BackgroundEffectOptions
```

配置分段按钮选项的背板效果。默认值：undefined该成员只读，不支持更改。

**类型：** [BackgroundEffectOptions](../arkts-components/arkts-arkui-backgroundeffectoptions-i.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemBorderRadius

```TypeScript
readonly itemBorderRadius?: LengthMetrics
```

配置分段按钮选项的圆角大小。取值范围：[0, +∞)默认值：`\$r('sys.float.segment_button_v2_selected_corner_radius')`超出取值范围按默认值处理。该成员只读，不支持更改。

**类型：** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemFontColor

```TypeScript
readonly itemFontColor?: ColorMetrics
```

配置分段按钮非选中的选项字体颜色。默认值：`\$r('sys.color.font_secondary')`值为undefined时，按默认值处理。  
**说明：**items设置textModifier/fontColor属性值时，itemFontColor不生效。该成员只读，不支持更改。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemFontSize

```TypeScript
readonly itemFontSize?: LengthMetrics
```

配置分段按钮非选中的选项字体大小。取值范围：[0, +∞)默认值：`14fp`  
**说明：**不支持设置百分比类型，异常值按默认值处理。items设置textModifier/fontSize属性值时，itemFontSize不生效。该成员只读，不支持更改。

**类型：** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemFontWeight

```TypeScript
readonly itemFontWeight?: FontWeight
```

配置分段按钮非选中选项的字体字重。默认值：FontWeight.Medium超出取值范围按默认值处理。  
**说明：**items设置textModifier/fontWeight属性值时，itemFontWeight不生效。该成员只读，不支持更改。

**类型：** FontWeight

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemIconFillColor

```TypeScript
readonly itemIconFillColor?: ColorMetrics
```

配置分段按钮非选中的选项图标颜色。默认值：`\$r('sys.color.font_secondary')`值为undefined时，按默认值处理。  
**说明：**items设置iconModifier/fillColor属性值时，itemIconFillColor不生效。backgroundSystemMaterial设置自动反色的系统材质时，该属性使用支持反色的特殊系统资源，颜色自动适配到材质背景色的反色。该成员只读，不支持更改。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemIconSize

```TypeScript
readonly itemIconSize?: SizeT<LengthMetrics>
```

配置分段按钮选项中Image类型的图标大小。取值范围：[0, +∞)默认值：`{ width: LengthMetrics.vp(24), height: LengthMetrics.vp(24) }`超出取值范围按默认值处理。  
**说明：**items设置iconModifier/width、height属性值时，itemIconSize不生效。该成员只读，不支持更改。

**类型：** [SizeT](arkts-arkui-graphics-sizet-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt;

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemMaxFontScale

```TypeScript
readonly itemMaxFontScale?: number | Resource
```

配置分段按钮选项文字大小的最大字体缩放倍数。取值范围：[1, 2]默认值：1  
**说明：**设置的值小于 1 时，按值为 1 处理，设置的值大于 2，按值为 2 处理，异常值默认不生效。该成员只读，不支持更改。

**类型：** number \| Resource

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemMinFontScale

```TypeScript
readonly itemMinFontScale?: number | Resource
```

配置分段按钮选项文字大小的最小字体缩放倍数。取值范围：[0, 1]默认值：0  
**说明：**设置的最小字体缩放值小于 0 时，按值为 0 处理，设置的最小字体缩放值大于 1 时，按值为 1 处理，异常值默认不生效。该成员只读，不支持更改。

**类型：** number \| Resource

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemMinHeight

```TypeScript
readonly itemMinHeight?: LengthMetrics
```

配置分段按钮选项最小高度。取值范围：[0, +∞)默认值：只有纯文本或者纯图标选项时：`\$r('sys.float.segment_button_v2_singleline_selected_height')`；有图文混合的选项时： `\$r('sys.float.segment_button_v2_doubleline_selected_height')`超出取值范围按默认值处理。该成员只读，不支持更改。

**类型：** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemPadding

```TypeScript
readonly itemPadding?: LocalizedPadding
```

配置分段按钮选项内边距。默认值： `{ top: LengthMetrics.resource(\$r('sys.float.padding_level2')), bottom: LengthMetrics.resource(\$r('sys.float.padding_level2')), start: LengthMetrics.resource(\$r('sys.float.padding_level4')), end: LengthMetrics.resource(\$r('sys.float.padding_level4')) }`值为undefined时，按默认值处理。该成员只读，不支持更改。

**类型：** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
readonly items: SegmentButtonV2Items
```

配置分段按钮的选项集合信息。值为undefined时，不显示选项信息。该成员只读，不支持更改。

**类型：** [SegmentButtonV2Items](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2items-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedBackgroundColor

```TypeScript
readonly itemSelectedBackgroundColor?: ColorMetrics
```

配置分段按钮选中的选项背景颜色。默认值：`\$r('sys.color.segment_button_v2_tab_selected_item_background')`值为undefined时，按默认值处理。该成员只读，不支持更改。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedFontColor

```TypeScript
readonly itemSelectedFontColor?: ColorMetrics
```

配置分段按钮非选中选项的字体颜色。默认值：`\$r('sys.color.font_secondary')`值为undefined时，按默认值处理。  
**说明：**items设置textModifier/fontColor属性值时，itemFontColor不生效。backgroundSystemMaterial设置自动反色的系统材质时，该属性使用支持反色的特殊系统资源，颜色自动适配到材质背景色的反色。该成员只读，不支持更改。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedFontSize

```TypeScript
readonly itemSelectedFontSize?: LengthMetrics
```

配置分段按钮选中的选项字体大小。取值范围：[0, +∞)默认值：`14fp`  
**说明：**不支持设置百分比类型，异常值按默认值处理。items设置textModifier/fontSize属性值时，itemSelectedFontSize不生效。该成员只读，不支持更改。

**类型：** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedFontWeight

```TypeScript
readonly itemSelectedFontWeight?: FontWeight
```

配置分段按钮选中项的字体字重。默认值：FontWeight.Medium超出取值范围按默认值处理。  
**说明：**items设置textModifier/fontWeight属性值时，itemSelectedFontWeight不生效。该成员只读，不支持更改。

**类型：** FontWeight

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedIconFillColor

```TypeScript
readonly itemSelectedIconFillColor?: ColorMetrics
```

配置分段按钮选中的选项图标颜色。默认值：`\$r('sys.color.font_primary')`值为undefined时，按默认值处理。  
**说明：**items设置iconModifier/fillColor属性值时，itemSelectedIconFillColor不生效。backgroundSystemMaterial设置自动反色的系统材质时，该属性使用支持反色的特殊系统资源，颜色自动适配到材质背景色的反色。该成员只读，不支持更改。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedSymbolFontColor

```TypeScript
readonly itemSelectedSymbolFontColor?: ColorMetrics
```

配置分段按钮选中选项的HM Symbol类型图标颜色。默认值：`\$r('sys.color.font_primary')`值为undefined时，按默认值处理。  
**说明：**items设置symbolModifier/fontColor属性值时，itemSelectedSymbolFontColor不生效。backgroundSystemMaterial设置自动反色的系统材质时，该属性使用支持反色的特殊系统资源，颜色自动适配到材质背景色的反色。该成员只读，不支持更改。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSpace

```TypeScript
readonly itemSpace?: LengthMetrics
```

配置分段按钮选项之间的间隔。取值范围：[0, +∞)默认值：`LengthMetrics.vp(1)`  
**说明：**不支持设置百分比类型，异常值按默认值处理。该成员只读，不支持更改。

**类型：** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSymbolFontColor

```TypeScript
readonly itemSymbolFontColor?: ColorMetrics
```

配置分段按钮非选中选项HM Symbol类型图标的颜色。默认值：`\$r('sys.color.font_secondary')`值为undefined时，按默认值处理。  
**说明：**items设置symbolModifier/fontColor属性值时，itemSymbolFontColor不生效。backgroundSystemMaterial设置自动反色的系统材质时，该属性使用支持反色的特殊系统资源，颜色自动适配到材质背景色的反色。该成员只读，不支持更改。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemSymbolFontSize

```TypeScript
readonly itemSymbolFontSize?: LengthMetrics
```

配置分段按钮选项中HM Symbol类型图标大小。取值范围：[0, +∞)默认值：`20fp`  
**说明：**不支持设置百分比类型，异常值按默认值处理。items设置symbolModifier/fontSize属性值时，itemSymbolFontSize不生效。该成员只读，不支持更改。

**类型：** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## languageDirection

```TypeScript
readonly languageDirection?: Direction
```

配置分段按钮的布局方向。默认值：Direction.Auto超出取值范围按默认值处理。该成员只读，不支持更改。

**类型：** Direction

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onItemClicked

```TypeScript
onItemClicked?: Callback<number>
```

配置分段按钮选项被单击时触发的回调函数。回调参数为number类型，表示被单击选项的下标，第一项编号为0，之后按顺序递增。默认值：undefined，未设置时不触发回调。

**类型：** Callback&lt;number&gt;

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndexes

```TypeScript
readonly selectedIndexes: number[]
```

配置分段按钮被选中的选项下标集合，第一项的编号为0，之后顺序增加。值为undefined时，不选中任何选项。  
**说明：**仅支持有效的按钮编号（第一个按钮编号为0，之后按顺序累加，取值范围：[0, items长度-1]），如没有选中项可传入空数组`[]`。传入无效编号（小于0或大于items长度-1）时，该编号不选中对应选项。该成员只读，不支持更改。

**类型：** number[]

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
