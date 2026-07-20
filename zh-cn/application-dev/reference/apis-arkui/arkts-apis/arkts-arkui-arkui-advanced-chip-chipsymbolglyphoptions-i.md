# ChipSymbolGlyphOptions

ChipSymbolGlyphOptions定义前缀图标和后缀图标的属性。

> **说明：**  
>  
> 不支持使用[SymbolEffect](../arkts-components/arkts-arkui-symboleffect-c.md)修改动效类型及effectStrategy设置动效。

**起始版本：** 12

<!--Device-unnamed-export interface ChipSymbolGlyphOptions--><!--Device-unnamed-export interface ChipSymbolGlyphOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SuffixIconOptions, CloseOptions, ChipSymbolGlyphOptions, Chip, AccessibilitySelectedType, LabelMarginOptions, LabelOptions, PrefixIconOptions, IconCommonOptions, ChipOptions, ChipSuffixSymbolGlyphOptions, ChipSize, AccessibilityOptions } from '@kit.ArkUI';
```

## activated

```TypeScript
activated?: SymbolGlyphModifier
```

激活时图标设定。

默认值：不显示前缀图标或后缀图标

值为undefined时，按默认值处理。

**类型：** SymbolGlyphModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipSymbolGlyphOptions-activated?: SymbolGlyphModifier--><!--Device-ChipSymbolGlyphOptions-activated?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## normal

```TypeScript
normal?: SymbolGlyphModifier
```

非激活时图标设定。

默认值：不显示前缀图标或后缀图标

值为undefined时，按默认值处理。

**类型：** SymbolGlyphModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChipSymbolGlyphOptions-normal?: SymbolGlyphModifier--><!--Device-ChipSymbolGlyphOptions-normal?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

