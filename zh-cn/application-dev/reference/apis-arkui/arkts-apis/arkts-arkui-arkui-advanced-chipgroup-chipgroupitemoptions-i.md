# ChipGroupItemOptions

ChipGroupItemOptions定义每个Chip的非通用属性。

> **说明：**
> 
> 当传入`suffixSymbol`参数时，`allowClose`不生效；当传入`suffixImageIcon`参数而`suffixSymbol`没有传入参数时，`allowClose`不生效；当`suffixSymbol`和
> `suffixImageIcon`都没有传入参数时，`allowClose`决定是否显示关闭图标。`suffixIcon`已废弃，请使用`suffixImageIcon`。
> 
> `suffixSymbol`、`suffixImageIcon`均为后缀图标，同一Chip项中只能配置其中一个。若同时配置多个，仅优先级最高的生效（优先级：`suffixSymbol`
> `suffixImageIcon`）。
> `suffixIcon`已废弃，建议使用`suffixImageIcon`替代。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

ChipGroup中Chip项的无障碍描述。此描述用于向用户详细解释ChipGroup中Chip项，开发人员应为该Chip项的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的结果。特别是当这些结果无法仅从 该Chip项的属性和无障碍文本中直接获知时。如果该Chip项同时具备label文本属性和无障碍说明属性，当其被选中时，系统将首先播报该Chip项的label文本属性，随后播报无障碍说明属性的内容。默认值：空字符串。值为undefined时，按默认值处理。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

ChipGroup中Chip项无障碍重要性。用于控制ChipGroup中Chip项是否可被无障碍辅助服务所识别。支持的值为："auto"：ChipGroup中Chip项会转换为“yes”，适用于大多数场景。"yes"：ChipGroup中Chip项可被无障碍辅助服务所识别，适用于需要明确启用无障碍访问的场景。"no"：ChipGroup中Chip项不可被无障碍辅助服务所识别，适用于纯装饰性图标的场景。"no-hide-descendants"：ChipGroup中Chip项及其所有子组件不可被无障碍辅助服务所识别，适用于需要隐藏整个区域的场景。默认值："auto"值为undefined时，按默认值处理。

**类型：** string

**默认值：** "auto"

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
allowClose?: boolean
```

关闭图标是否显示。false表示关闭图标不显示，true表示关闭图标显示。当需要允许用户删除或移除Chip项时设置此参数为true，适用于编辑模式、可配置标签列表等场景。默认值：false值为undefined时，按默认值处理。  
**说明：**当suffixSymbol有传入参数时，allowClose不生效；当suffixSymbol没有传入参数而suffixIcon或suffixImageIcon有传入参数时，allowClose不生效；当 suffixSymbol、suffixIcon和suffixImageIcon都没有传入参数时，allowClose决定是否显示关闭图标。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeOptions

```TypeScript
closeOptions?: CloseOptions
```

默认关闭图标的无障碍朗读功能和字体大小属性。当需要为关闭图标提供自定义的无障碍朗读内容和字体大小时设置此参数。默认值：参考[CloseOptions](arkts-arkui-arkui-advanced-chip-closeoptions-i.md)中的默认配置。值为undefined时，按默认值处理。

**类型：** [CloseOptions](arkts-arkui-arkui-advanced-chip-closeoptions-i.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label: LabelOptions
```

Chip项显示的文本内容，用于设置Chip上展示的文字信息。

**类型：** [LabelOptions](arkts-arkui-arkui-advanced-chipgroup-labeloptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
prefixIcon?: IconOptions
```

前缀Image图标属性。当需要在Chip前显示图标以增强视觉识别或提供功能提示时设置此参数。默认值：没有前缀Image图标。值为undefined时，按默认值处理。

**类型：** [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixSymbol

```TypeScript
prefixSymbol?: ChipSymbolGlyphOptions
```

前缀SymbolGlyph图标属性。当需要在Chip前显示SymbolGlyph图标以增强视觉识别或提供功能提示时设置此参数。默认值：没有前缀SymbolGlyph图标。值为undefined时，按默认值处理。

**类型：** [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
suffixIcon?: IconOptions
```

后缀Image图标属性。当需要在Chip后显示Image图标以提供额外操作或状态提示时设置此参数。默认值：不显示后缀Image图标。值为undefined时，按默认值处理。  
**说明：**当suffixIcon有传入参数时，allowClose不生效。
**说明：** 从API version 12开始支持，从API version 14开始废弃。建议使用[suffixImageIcon](arkts-arkui-arkui-advanced-chipgroup-suffiximageiconoptions-i.md)替代。

**类型：** [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md)

**起始版本：** 12

**废弃版本：** 14

**替代接口：** [suffixImageIcon](#suffiximageicon)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixImageIcon

```TypeScript
suffixImageIcon?: SuffixImageIconOptions
```

后缀Image图标属性。当需要在Chip后显示图标以提供额外操作或状态提示时设置此参数。  
**说明：**当suffixImageIcon有传入参数时，allowClose不生效；当suffixSymbol和suffixImageIcon同时配置时，仅suffixSymbol生效，suffixImageIcon不生效。默认值：不显示后缀Image图标。值为undefined时，按默认值处理。

**类型：** [SuffixImageIconOptions](arkts-arkui-arkui-advanced-chipgroup-suffiximageiconoptions-i.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbol

```TypeScript
suffixSymbol?: ChipSymbolGlyphOptions
```

后缀SymbolGlyph图标属性。当需要在Chip后显示SymbolGlyph图标以提供额外操作或状态提示时设置此参数。  
**说明：**当suffixSymbol有传入参数时，allowClose不生效。suffixSymbol与suffixImageIcon为互斥属性，同一Chip项中只能配置其中一个，若同时配置仅优先级最高的生效（优先级： suffixSymbol&gt; suffixImageIcon）。默认值：不显示后缀SymbolGlyph图标。值为undefined时，按默认值处理。

**类型：** [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbolOptions

```TypeScript
suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions
```

后缀Symbol图标属性，用于配置后缀Symbol图标的交互功能和无障碍属性。当需要为后缀Symbol图标添加点击事件或无障碍支持时设置此参数。默认值：使用[ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md)的默认值。值为undefined时，按默认值处理。

**类型：** [ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
