# ChipOptions

ChipOptions定义Chip的样式及具体式样参数。

> **说明：**  
>  
> 1. 当`suffixSymbol`有传入参数时，`suffixIcon`和`allowClose`不生效；当`suffixSymbol`没有传入参数而`suffixIcon`有传入参数时，`allowClose`不生效；当  
> `suffixSymbol`和`suffixIcon`都没有传入参数时，`allowClose`决定是否显示删除图标。  
>  
> 2. `backgroundColor`和`activatedBackgroundColor`赋值为`undefined`时，显示默认背景颜色；赋值为非法值时，背景颜色透明。  
>  
> 3. prefixSymbol/suffixSymbol的fontColor默认值为：normalFontColor: `[$r('sys.color.ohos_id_color_primary')]`、  
> activatedFontColor: `[$r('sys.color.ohos_id_color_text_primary_contrary')]`。fontColor默认值为16。  
>  
> 4. prefixIcon的fillColor默认值为：`$r('sys.color.ohos_id_color_secondary')`，suffixIcon的fillColor默认值为：  
> `$r('sys.color.ohos_id_color_primary')`。fillColor对颜色的解析与Image组件保持一致。  
>  
> 5. prefixIcon和suffixIcon的activatedFillColor默认值均为：`$r('sys.color.ohos_id_color_text_primary_contrary')`。  
> activatedFillColor对颜色的解析与Image组件保持一致。

**起始版本：** 11

<!--Device-unnamed-export interface ChipOptions--><!--Device-unnamed-export interface ChipOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SuffixIconOptions, CloseOptions, ChipSymbolGlyphOptions, Chip, AccessibilitySelectedType, LabelMarginOptions, LabelOptions, PrefixIconOptions, IconCommonOptions, ChipOptions, ChipSuffixSymbolGlyphOptions, ChipSize, AccessibilityOptions } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Chip组件的无障碍描述。此描述用于向用户详细解释当前组件，开发人员应为组件的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的结果。特别是当这些结果无法仅从组件的属性和无障碍文本中直接获知时。如果组件同时具备文本属性和无障碍说明属性，当组件被选中时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。

默认值：空字符串。

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-accessibilityDescription?: ResourceStr--><!--Device-ChipOptions-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Chip组件无障碍重要性。用于控制后缀图标是否可被无障碍辅助服务所识别。

支持的值为:

"auto"：当前组件会转化为"yes"。

"yes"：当前组件可被无障碍辅助服务所识别。

"no"：当前组件不可被无障碍辅助服务所识别。

"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。

默认值："auto"。

值为undefined时，按默认值处理。

**类型：** string

**默认值：** "auto"

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-accessibilityLevel?: string--><!--Device-ChipOptions-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilitySelectedType

```TypeScript
accessibilitySelectedType?: AccessibilitySelectedType
```

Chip组件选中态类型。

默认值：当设置了activated属性但未指定accessibilitySelectedType时，默认使用CHECKED类型。当未设置activated属性时，默认使用CLICKED类型。

值为undefined时，按默认值处理。

**类型：** AccessibilitySelectedType

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-accessibilitySelectedType?: AccessibilitySelectedType--><!--Device-ChipOptions-accessibilitySelectedType?: AccessibilitySelectedType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activated

```TypeScript
activated?: boolean
```

Chip是否为激活态。

默认值：false。

true：操作块为激活态；false：操作块为非激活态。

值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-activated?: boolean--><!--Device-ChipOptions-activated?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundColor

```TypeScript
activatedBackgroundColor?: ResourceColor
```

Chip激活时的背景颜色。

默认值：$r('sys.color.ohos_id_color_emphasize')。

值为undefined时，按默认值处理。

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-activatedBackgroundColor?: ResourceColor--><!--Device-ChipOptions-activatedBackgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundSystemMaterial

```TypeScript
activatedBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件激活状态下的系统材质样式。不同材质具有不同的效果，能够影响组件的[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor-1)、[border](../arkts-components/arkts-arkui-commonmethod-c.md#border-1)、[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow-1)等视觉属性。

默认值：undefined

值为undefined时，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-activatedBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipOptions-activatedBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
allowClose?: boolean
```

关闭图标是否显示。

默认值：true

true：删除图标显示；false：删除图标不显示。

值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-allowClose?: boolean--><!--Device-ChipOptions-allowClose?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Chip背景颜色。

默认值：$r('sys.color.ohos_id_color_button_normal')。

值为undefined时，按默认值处理。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-backgroundColor?: ResourceColor--><!--Device-ChipOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor-1)、[border](../arkts-components/arkts-arkui-commonmethod-c.md#border-1)、[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow-1)等视觉属性。

默认值：undefined

值为undefined时，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-backgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipOptions-backgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: Dimension
```

Chip背景圆角半径大小，不支持百分比。

默认值：$r('sys.float.ohos_id_corner_radius_button')。

值为undefined时，按默认值处理。

**类型：** Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-borderRadius?: Dimension--><!--Device-ChipOptions-borderRadius?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeOptions

```TypeScript
closeOptions?: CloseOptions
```

默认关闭图标的无障碍朗读功能属性。

值为undefined时，按默认值处理。

**类型：** CloseOptions

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-closeOptions?: CloseOptions--><!--Device-ChipOptions-closeOptions?: CloseOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

布局方向。

默认值：Direction.Auto。

值为undefined时，按默认值处理。

**类型：** Direction

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-direction?: Direction--><!--Device-ChipOptions-direction?: Direction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

Chip是否可选中。

默认值：true。

true：操作块可选中；false：操作块不可选中。

值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-enabled?: boolean--><!--Device-ChipOptions-enabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Dimension
```

统一设置Chip组件的文本与图标的字体大小，不支持百分比。

该fontSize的优先级低于prefixSymbol、label、suffixSymbol和closeOptions中的fontSize属性。

默认值：

- size为ChipSize.SMALL时，文本默认值：`$r('sys.float.chip_small_font_size')`；图标默认值：`$r('sys.float.chip_small_icon_size')`  
- 其他情况下，文本默认值：`$r('sys.float.chip_normal_font_size')`；图标默认值：`$r('sys.float.chip_normal_icon_size')`

值为undefined时，按默认值处理。

**类型：** Dimension

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-fontSize?: Dimension--><!--Device-ChipOptions-fontSize?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label: LabelOptions
```

文本属性。

**类型：** LabelOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-label: LabelOptions--><!--Device-ChipOptions-label: LabelOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
maxFontScale?: number | Resource
```

Chip组件文本与图标的最大的字体缩放倍数。取值范围：[1, +∞)。

**类型：** number \| Resource

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-maxFontScale?: number | Resource--><!--Device-ChipOptions-maxFontScale?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontScale

```TypeScript
minFontScale?: number | Resource
```

Chip组件文本与图标的最小的字体缩放倍数。取值范围：[0, 1]。

**类型：** number \| Resource

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-minFontScale?: number | Resource--><!--Device-ChipOptions-minFontScale?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClicked

```TypeScript
onClicked?: Callback<void>
```

Chip点击事件。

值为undefined时，Chip不能被点击。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-onClicked?: Callback<void>--><!--Device-ChipOptions-onClicked?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClose

```TypeScript
onClose?: () => void
```

默认关闭图标点击事件。

值为undefined时，关闭图标点击事件。

**类型：** () =&gt; void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-onClose?: () => void--><!--Device-ChipOptions-onClose?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
padding?: LocalizedPadding
```

Chip组件的内边距。

默认值：

- size为ChipSize.SMALL并且activated为true时，默认值：`{ start: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`

- size为ChipSize.SMALL并且activated为false时，默认值：`{ start: LengthMetrics.resource('sys.float.chip_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`

- size不为ChipSize.SMALL并且activated为true时，默认值：`{ start: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`

- size不为ChipSize.SMALL并且activated为false时，默认值：`{ start: LengthMetrics.resource('sys.float.chip_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`

值为undefined时，按默认值处理。

**类型：** LocalizedPadding

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-padding?: LocalizedPadding--><!--Device-ChipOptions-padding?: LocalizedPadding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
prefixIcon?: PrefixIconOptions
```

前缀图标属性。

默认值：不显示前缀图标。

值为undefined时，按默认值处理。

prefixIcon和prefixSymbol同时设置时，显示prefixSymbol的效果，prefixIcon无效。

**类型：** PrefixIconOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-prefixIcon?: PrefixIconOptions--><!--Device-ChipOptions-prefixIcon?: PrefixIconOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixSymbol

```TypeScript
prefixSymbol?: ChipSymbolGlyphOptions
```

前缀图标属性，symbol类型。

默认值：不显示前缀图标。

值为undefined时，按默认值处理。

prefixIcon和prefixSymbol同时设置时，显示prefixSymbol的效果，prefixIcon无效。

**类型：** ChipSymbolGlyphOptions

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-prefixSymbol?: ChipSymbolGlyphOptions--><!--Device-ChipOptions-prefixSymbol?: ChipSymbolGlyphOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ChipSize | SizeOptions
```

Chip尺寸。

默认值：ChipSize.NORMAL

SizeOptions类型参数不支持百分比设置，异常值按默认值处理。

**说明**：[适老化](docroot://ui/arkui-support-for-aging-adaptation.md)在size指定具体宽高时不生效，size设置为{ height: 0, width: 0 }除外。

**类型：** ChipSize \| SizeOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-size?: ChipSize | SizeOptions--><!--Device-ChipOptions-size?: ChipSize | SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
suffixIcon?: SuffixIconOptions
```

后缀图标属性。

默认值：不显示后缀图标。

值为undefined时，按默认值处理。

suffixIcon和suffixSymbol同时设置时，显示suffixSymbol的效果，suffixIcon无效。

**类型：** SuffixIconOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-suffixIcon?: SuffixIconOptions--><!--Device-ChipOptions-suffixIcon?: SuffixIconOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbol

```TypeScript
suffixSymbol?: ChipSymbolGlyphOptions
```

后缀图标属性，symbol类型。

默认值：不显示后缀图标。

值为undefined时，按默认值处理。

suffixIcon和suffixSymbol同时设置时，显示suffixSymbol的效果，suffixIcon无效。

**类型：** ChipSymbolGlyphOptions

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-suffixSymbol?: ChipSymbolGlyphOptions--><!--Device-ChipOptions-suffixSymbol?: ChipSymbolGlyphOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbolOptions

```TypeScript
suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions
```

symbol类型后缀图标属性的无障碍朗读功能属性。

默认值：不显示后缀图标。

值为undefined时，按默认值处理。

**类型：** ChipSuffixSymbolGlyphOptions

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ChipOptions-suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions--><!--Device-ChipOptions-suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

