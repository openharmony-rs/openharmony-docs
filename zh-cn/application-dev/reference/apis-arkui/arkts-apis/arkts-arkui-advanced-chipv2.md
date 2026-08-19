# @ohos.arkui.advanced.ChipV2

## 导入模块

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ChipV2Accessibility](arkts-arkui-arkui-advanced-chipv2-chipv2accessibility-c.md) | ChipV2Accessibility定义无障碍属性类。 |
| [ChipV2CloseIcon](arkts-arkui-arkui-advanced-chipv2-chipv2closeicon-c.md) | ChipV2CloseIcon用于定义ChipV2组件关闭图标的功能属性类，包括无障碍功能属性。 继承自[ChipV2Accessibility](arkts-arkui-arkui-advanced-chipv2-chipv2accessibility-c.md)。 |
| [ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md) | ChipV2Icon定义图标的基类。 |
| [ChipV2ImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2imageicon-c.md) | ChipV2ImageIcon定义图标图片的基类。 继承自[ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md)。 |
| [ChipV2Label](arkts-arkui-arkui-advanced-chipv2-chipv2label-c.md) | ChipV2Label定义文本属性类。 |
| [ChipV2Options](arkts-arkui-arkui-advanced-chipv2-chipv2options-c.md) | ChipV2Options定义ChipV2的样式及具体样式参数。 |
| [ChipV2PrefixImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2prefiximageicon-c.md) | ChipV2PrefixImageIcon定义前缀图标类。 继承自[ChipV2ImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2imageicon-c.md)。 |
| [ChipV2PrefixSymbolIcon](arkts-arkui-arkui-advanced-chipv2-chipv2prefixsymbolicon-c.md) | ChipV2PrefixSymbolIcon定义前缀Symbol图标类。 继承自[ChipV2SymbolIcon](arkts-arkui-arkui-advanced-chipv2-chipv2symbolicon-c.md)。 |
| [ChipV2SuffixImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2suffiximageicon-c.md) | ChipV2SuffixImageIcon定义后缀图标类。 继承自[ChipV2ImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2imageicon-c.md)。 |
| [ChipV2SuffixSymbolIcon](arkts-arkui-arkui-advanced-chipv2-chipv2suffixsymbolicon-c.md) | ChipV2SuffixSymbolIcon定义后缀Symbol图标类。 继承自[ChipV2SymbolIcon](arkts-arkui-arkui-advanced-chipv2-chipv2symbolicon-c.md)。 |
| [ChipV2SymbolIcon](arkts-arkui-arkui-advanced-chipv2-chipv2symbolicon-c.md) | ChipV2SymbolIcon定义Symbol图标类。 继承自[ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md)。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ChipV2](arkts-arkui-arkui-advanced-chipv2-chipv2-s.md) | ChipV2是提供丰富样式和交互能力的操作块组件，支持前缀图标、后缀图标、激活状态、关闭按钮等特性，支持Symbol和Image两种图标类型，并提供完善的无障碍访问能力。该组件适用于搜索历史记录、邮件发送列表、标签选择、过滤器、联系人 展示等场景。 该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于 [状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以更灵活地控制组件的数据和状态，实现更高效的用户界面刷新。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md) | ChipV2AccessibilityConfig定义无障碍属性配置。 |
| [ChipV2CloseConfig](arkts-arkui-arkui-advanced-chipv2-chipv2closeconfig-i.md) | ChipV2CloseConfig用于定义ChipV2组件关闭图标的功能属性配置，包括无障碍功能属性。 继承自[ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md)。 |
| [ChipV2ImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md) | ChipV2ImageIconConfig定义图标的通用属性配置。 |
| [ChipV2LabelConfig](arkts-arkui-arkui-advanced-chipv2-chipv2labelconfig-i.md) | ChipV2LabelConfig定义文本属性配置。 |
| [ChipV2LabelMarginConfig](arkts-arkui-arkui-advanced-chipv2-chipv2labelmarginconfig-i.md) | ChipV2LabelMarginConfig定义文本与左右侧图标之间间距配置。 |
| [ChipV2LocalizedLabelMarginConfig](arkts-arkui-arkui-advanced-chipv2-chipv2localizedlabelmarginconfig-i.md) | ChipV2LocalizedLabelMarginConfig用于定义本地化文本与左右侧图标之间间距配置。 |
| [ChipV2PrefixImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2prefiximageiconconfig-i.md) | ChipV2PrefixImageIconConfig定义前缀图标的属性配置。 继承自[ChipV2ImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md)。 |
| [ChipV2PrefixSymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2prefixsymboliconconfig-i.md) | ChipV2PrefixSymbolIconConfig定义前缀Symbol图标的属性配置。 继承自[ChipV2SymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2symboliconconfig-i.md)。 |
| [ChipV2SuffixImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2suffiximageiconconfig-i.md) | ChipV2SuffixImageIconConfig定义后缀图标的属性配置。 继承自[ChipV2ImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md)和[ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md)。 |
| [ChipV2SuffixSymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2suffixsymboliconconfig-i.md) | ChipV2SuffixSymbolIconConfig定义后缀Symbol图标的属性配置。 继承自[ChipV2SymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2symboliconconfig-i.md)。 |
| [ChipV2SymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2symboliconconfig-i.md) | ChipV2SymbolIconConfig定义Symbol图标的属性配置。 |
| [IChipV2OptionsConfig](arkts-arkui-arkui-advanced-chipv2-ichipv2optionsconfig-i.md) | IChipV2OptionsConfig定义ChipV2选项的配置接口。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ChipV2AccessibilitySelectedType](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityselectedtype-e.md) | ChipV2AccessibilitySelectedType是ChipV2可指定的选中态类型，用于控制无障碍辅助服务如何向用户传达组件的选中状态。不同的选中态类型提供了不同的语义和用户体验。 |
| [ChipV2Size](arkts-arkui-arkui-advanced-chipv2-chipv2size-e.md) | ChipV2Size是ChipV2可指定的尺寸类型，如普通型ChipV2。 |

