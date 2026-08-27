# ChipOptions

ChipOptions定义Chip的样式及具体样式参数。

> **说明：**
> 
> 1. 当`suffixSymbol`有传入参数时，`suffixIcon`和`allowClose`不生效；当`suffixSymbol`没有传入参数而`suffixIcon`有传入参数时，`allowClose`不生效；当
> `suffixSymbol`和`suffixIcon`都没有传入参数时，`allowClose`决定是否显示关闭图标。
> 
> 2. `backgroundColor`和`activatedBackgroundColor`赋值为`undefined`时，显示默认背景颜色；赋值为非法值时，背景颜色透明。
> 
> 3. 当prefixSymbol或suffixSymbol设置了图标时，若Chip为非激活状态，图标颜色fontColor为`[\$r('sys.color.ohos_id_color_secondary')]`，若Chip为激活状
> 态，图标颜色fontColor为`[\$r('sys.color.ohos_id_color_text_primary_contrary')]`。此外，当size为ChipSize.SMALL时，图标的默认字体大小fontSize为
> `\$r('sys.float.chip_small_icon_size')`；当size为ChipSize.NORMAL或自定义大小时，图标的默认字体大小fontSize为
> `\$r('sys.float.chip_normal_icon_size')`。
> 
> 4. 当prefixIcon和suffixIcon设置了图标时，fillColor默认值均为：`\$r('sys.color.chip_usually_icon_color')`。fillColor对颜色的解析与Image组件保持一
> 致。
> 
> 5. 当prefixIcon和suffixIcon设置了图标时，activatedFillColor默认值均为：`\$r('sys.color.chip_active_icon_color')`。activatedFillColor
> 对颜色的解析与Image组件保持一致。
> 
> 6. 从API版本26.0.0开始，当配置backgroundSystemMaterial为自动反色材质时，prefixIcon和suffixIcon的填充色以及prefixSymbol和suffixSymbol在非激活状态下的文
> 字颜色会使用支持反色的系统资源，这些颜色会根据背景材质自动匹配反色效果。当设置activatedBackgroundSystemMaterial为自动反色材质时，prefixIcon和suffixIcon的激活态填充色以及
> prefixSymbol和suffixSymbol在激活状态下的文字颜色同样采用支持反色的系统资源，实现与背景材质反色的自动适配。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## onClose

```TypeScript
onClose?: () => void
```

默认关闭图标点击事件。值为undefined时，不触发关闭图标点击事件。  
**说明：**仅当关闭图标显示时生效，即suffixSymbol和suffixIcon都未传入参数且allowClose为true时。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Chip组件的无障碍描述。用于向用户详细解释当前组件，开发人员应提供详尽的文本说明，协助用户理解即将执行的操作及其结果。特别是当这些结果无法仅从组件属性和无障碍文本中直接获知时。如果组件同时具备文本属性和无障碍说明属性，当组件被选 中时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。默认值：空字符串。值为undefined时，按默认值处理。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Chip组件无障碍重要性。用于控制Chip组件是否可被无障碍辅助服务所识别。支持的值为："auto"：当前组件会转化为"yes"。"yes"：当前组件可被无障碍辅助服务所识别。"no"：当前组件不可被无障碍辅助服务所识别。"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。默认值："auto"。值为undefined时，按默认值处理。

**类型：** string

**默认值：** "auto"

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilitySelectedType

```TypeScript
accessibilitySelectedType?: AccessibilitySelectedType
```

Chip组件选中态类型。默认值：当设置了activated属性但未指定accessibilitySelectedType时，默认使用CHECKED类型。当未设置activated属性时，默认使用CLICKED类型。值为undefined时，按默认值处理。

**类型：** [AccessibilitySelectedType](arkts-arkui-arkui-advanced-chip-accessibilityselectedtype-e.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activated

```TypeScript
activated?: boolean
```

Chip是否为激活态。默认值：false。true：Chip为激活态；false：Chip为非激活态。值为undefined时，按默认值处理。  
**使用场景**：常用于标签选择场景表示当前选中项等。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundColor

```TypeScript
activatedBackgroundColor?: ResourceColor
```

Chip激活态的背景颜色。默认值：\$r('sys.color.ohos_id_color_emphasize')。值为undefined时，按默认值处理。赋值为非法值时，背景颜色透明。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundSystemMaterial

```TypeScript
activatedBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件激活状态下的系统材质样式。不同材质具有不同的效果，能够影响组件的backgroundColor、 [border](../arkts-components/arkts-arkui-commonmethod-c.md#border)、shadow等视觉属性。默认值：undefined值为undefined时，不应用材质样式。  
**说明：**当设置activatedBackgroundSystemMaterial时，应将activatedBackgroundColor设为Color.Transparent，否则会与系统材质冲突；当 activatedBackgroundSystemMaterial为undefined时，activatedBackgroundColor属性生效。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
allowClose?: boolean
```

关闭图标是否显示。默认值：true true：关闭图标显示；false：关闭图标不显示。值为undefined时，按默认值处理。  
**说明：**当suffixSymbol有传入参数时，allowClose不生效；当suffixSymbol没有传入参数而suffixIcon有传入参数时，allowClose不生效；当suffixSymbol和 suffixIcon都没有传入参数时，allowClose决定是否显示关闭图标。

**类型：** boolean

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Chip背景颜色。默认值：\$r('sys.color.ohos_id_color_button_normal')。值为undefined时，按默认值处理。赋值为非法值时，背景颜色透明。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的backgroundColor、 [border](../arkts-components/arkts-arkui-commonmethod-c.md#border)、shadow等视觉属性。默认值：undefined值为undefined时，不应用材质样式。  
**说明：**当设置backgroundSystemMaterial时，应将backgroundColor设为Color.Transparent，否则会与系统材质冲突；当backgroundSystemMaterial为 undefined时，backgroundColor属性生效。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: Dimension
```

Chip背景圆角半径大小，不支持百分比，传入百分比时按默认值处理。取值范围：[0, +∞)默认值：\$r('sys.float.ohos_id_corner_radius_button')。单位：vp值为undefined时，按默认值处理。

**类型：** [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeOptions

```TypeScript
closeOptions?: CloseOptions
```

默认关闭图标的功能属性，包括无障碍朗读功能和字体大小等属性。仅在默认关闭图标显示时生效，即allowClose为true且suffixSymbol和suffixIcon均未设置传入参数时。值为undefined时，按默认值处理。

**类型：** [CloseOptions](arkts-arkui-arkui-advanced-chip-closeoptions-i.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

布局方向。默认值：Direction.Auto。值为undefined时，按默认值处理。  
**使用场景**：常用于国际化场景，适配阿拉伯语等从右到左（RTL）阅读习惯的语言环境，实现界面镜像效果。

**类型：** Direction

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

Chip是否可用。默认值：true。true：Chip可用；false：Chip不可用。  
**使用场景**：设置为false禁用Chip，适用于权限受限、数据未加载完成、条件不满足等需要禁止用户操作的场景。值为undefined时，按默认值处理。

**类型：** boolean

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Dimension
```

统一设置Chip组件的文本与图标的字体大小，不支持百分比，传入百分比时按默认值处理。该fontSize的优先级低于prefixSymbol、label、suffixSymbol和closeOptions中的fontSize属性。默认值：  
- size为ChipSize.SMALL时，文本：`\$r('sys.float.chip_small_font_size')`；图标：`\$r('sys.float.chip_small_icon_size')`  
- 其他情况下，文本：`\$r('sys.float.chip_normal_font_size')`；图标：`\$r('sys.float.chip_normal_icon_size')`  
单位：fp值为undefined时，按默认值处理。

**类型：** [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label: LabelOptions
```

设置Chip组件显示的文本内容及样式。

**类型：** [LabelOptions](arkts-arkui-arkui-advanced-chip-labeloptions-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
maxFontScale?: number | Resource
```

Chip组件文本与图标的最大的字体缩放倍数。取值范围：[1, +∞)设置的值小于1时，按值为1处理。异常值默认不生效。默认值：1值为undefined时，按默认值处理。  
**使用场景**：适用于需要限制字体放大上限的无障碍场景，防止字体过大导致布局溢出。

**类型：** number \| Resource

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontScale

```TypeScript
minFontScale?: number | Resource
```

Chip组件文本与图标的最小的字体缩放倍数。取值范围：[0, 1]设置的值小于0时，按值为0处理。设置的值大于1时，按值为1处理。异常值默认不生效。默认值：1值为undefined时，按默认值处理。  
**使用场景**：适用于需要限制字体缩小下限的场景，保证文本可读性。

**类型：** number \| Resource

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClicked

```TypeScript
onClicked?: Callback<void>
```

Chip组件点击事件。值为undefined时，Chip不能被点击。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
padding?: LocalizedPadding
```

Chip组件的内边距。默认值：  
- size为ChipSize.SMALL并且activated为true时，默认值：  
`{ start: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`  
- size为ChipSize.SMALL并且activated为false时，默认值：  
`{ start: LengthMetrics.resource('sys.float.chip_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`  
- size不为ChipSize.SMALL并且activated为true时，默认值：  
`{ start: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`  
- size不为ChipSize.SMALL并且activated为false时，默认值：  
`{ start: LengthMetrics.resource('sys.float.chip_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`值为undefined时，按默认值处理。

**类型：** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
prefixIcon?: PrefixIconOptions
```

设置Chip组件的前缀图标，显示在组件左侧。默认值：不显示前缀图标。值为undefined时，按默认值处理。prefixIcon和prefixSymbol同时设置时，显示prefixSymbol的效果，prefixIcon无效。

**类型：** [PrefixIconOptions](arkts-arkui-arkui-advanced-chip-prefixiconoptions-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixSymbol

```TypeScript
prefixSymbol?: ChipSymbolGlyphOptions
```

前缀图标属性，symbol类型。常用于需要系统标准图标、动态图标效果的场景。默认值：不显示前缀图标。值为undefined时，按默认值处理。prefixIcon和prefixSymbol同时设置时，显示prefixSymbol的效果，prefixIcon无效。

**类型：** [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ChipSize | SizeOptions
```

Chip尺寸。默认值：ChipSize.NORMAL  
**使用场景**：ChipSize.NORMAL适用于常规场景；ChipSize.SMALL适用于紧凑布局场景，如标签列表、筛选栏等；自定义SizeOptions适用于需要特定尺寸的场景。SizeOptions类型参数不支持百分比设置，异常值按默认值处理。  
**说明：**[适老化](../../../ui/arkui-support-for-aging-adaptation.md)在size指定具体宽高时不生效，size设置为{ height: 0, width: 0 }除外。

**类型：** [ChipSize](arkts-arkui-arkui-advanced-chip-chipsize-e.md) \| [SizeOptions](arkts-arkui-sizeoptions-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
suffixIcon?: SuffixIconOptions
```

设置Chip组件的后缀图标，显示在组件右侧。默认值：不显示后缀图标。值为undefined时，按默认值处理。suffixIcon和suffixSymbol同时设置时，显示suffixSymbol的效果，suffixIcon无效。

**类型：** [SuffixIconOptions](arkts-arkui-arkui-advanced-chip-suffixiconoptions-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbol

```TypeScript
suffixSymbol?: ChipSymbolGlyphOptions
```

后缀图标属性，symbol类型。常用于需要系统标准图标、动态图标效果的场景。默认值：不显示后缀图标。值为undefined时，按默认值处理。suffixIcon和suffixSymbol同时设置时，显示suffixSymbol的效果，suffixIcon无效。

**类型：** [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbolOptions

```TypeScript
suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions
```

symbol类型后缀图标的无障碍朗读功能属性及点击事件回调等。默认值：不设置对应属性。值为undefined时，按默认值处理。

**类型：** [ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
