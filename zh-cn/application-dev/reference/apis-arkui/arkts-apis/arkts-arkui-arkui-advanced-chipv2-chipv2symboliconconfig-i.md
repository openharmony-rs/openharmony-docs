# ChipV2SymbolIconConfig

ChipV2SymbolIconConfig定义Symbol图标的属性配置。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## activated

```TypeScript
activated?: SymbolGlyphModifier
```

激活时图标设定。默认值：不显示前缀图标或后缀图标。值为undefined时，按默认值处理。不支持使用[SymbolEffect](../arkts-components/arkts-arkui-symbolglyph-attribute.md#symboleffect)修改动效类型及 effectStrategy设置动效。

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## normal

```TypeScript
normal?: SymbolGlyphModifier
```

非激活时图标设定。默认值：不显示前缀图标或后缀图标。值为undefined时，按默认值处理。不支持使用[SymbolEffect](../arkts-components/arkts-arkui-symbolglyph-attribute.md#symboleffect)修改动效类型及 effectStrategy设置动效。

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
