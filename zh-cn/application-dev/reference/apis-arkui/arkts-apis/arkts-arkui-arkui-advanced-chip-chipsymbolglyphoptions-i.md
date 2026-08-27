# ChipSymbolGlyphOptions

ChipSymbolGlyphOptions定义前缀图标和后缀图标的属性。

> **说明：**
> 
> 不支持使用[SymbolEffect](../arkts-components/arkts-arkui-symbolglyph-attribute.md#symboleffect)修改动效类型及
> effectStrategy设置动效。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## activated

```TypeScript
activated?: SymbolGlyphModifier
```

设置Chip在激活状态下显示的symbol类型图标。默认值：不显示前缀图标或后缀图标值为undefined时，按默认值处理。

**类型：** SymbolGlyphModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## normal

```TypeScript
normal?: SymbolGlyphModifier
```

设置Chip在非激活状态下显示的symbol类型图标。默认值：不显示前缀图标或后缀图标值为undefined时，按默认值处理。

**类型：** SymbolGlyphModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
