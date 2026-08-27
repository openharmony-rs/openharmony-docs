# Chip

## 导入模块

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## Chip

```TypeScript
export declare function Chip(options: ChipOptions): void
```

创建Chip组件。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ChipOptions](arkts-arkui-arkui-advanced-chip-chipoptions-i.md) | 是 | 定义Chip组件的参数，包括尺寸、启用状态、激活态、前缀/后缀图标、文本内容、背景颜色、圆角、无障碍属性等，用于自定义Chip组件的样式和行为。 |
