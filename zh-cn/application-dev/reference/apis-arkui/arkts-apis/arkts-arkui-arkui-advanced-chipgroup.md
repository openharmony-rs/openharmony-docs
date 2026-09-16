# @ohos.arkui.advanced.ChipGroup

## 导入模块

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ChipGroup](arkts-arkui-arkui-advanced-chipgroup-chipgroup-s.md) | ChipGroup组件提供操作块群组能力，支持单选或多选模式，可自定义样式、图标和间距，支持选中状态管理和事件回调。适用于文件分类、资源筛选、标签选择、内容分组等多种场景，帮助开发者快速实现选择功能，提供统一的视觉和交互体验。 |
| [IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md) | ChipGroup组件提供操作块群组能力，支持单选或多选模式，可自定义样式、图标和间距，支持选中状态管理和事件回调。适用于文件分类、资源筛选、标签选择、内容分组等多种场景，帮助开发者快速实现选择功能，提供统一的视觉和交互体验。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChipGroupItemOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupitemoptions-i.md) | ChipGroupItemOptions定义每个Chip的非通用属性。 |
| [ChipGroupPaddingOptions](arkts-arkui-arkui-advanced-chipgroup-chipgrouppaddingoptions-i.md) | ChipGroupPaddingOptions定义了ChipGroup的上下内边距，用于控制其整体高度。 |
| [ChipGroupSpaceOptions](arkts-arkui-arkui-advanced-chipgroup-chipgroupspaceoptions-i.md) | ChipGroupSpaceOptions 定义了ChipGroup左右内边距，以及Chip与Chip之间的间距。 |
| [ChipItemStyle](arkts-arkui-arkui-advanced-chipgroup-chipitemstyle-i.md) | ChipItemStyle定义了Chip的通用属性。 |
| [IconItemOptions](arkts-arkui-arkui-advanced-chipgroup-iconitemoptions-i.md) | 定义了尾部builder接口，用于配置尾部图标及其背景区域的显示属性。 |
| [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md) | IconOptions定义图标的通用属性。 |
| [LabelOptions](arkts-arkui-arkui-advanced-chipgroup-labeloptions-i.md) | LabelOptions定义文本属性。 |
| [SuffixImageIconOptions](arkts-arkui-arkui-advanced-chipgroup-suffiximageiconoptions-i.md) | 后缀图标选项的类型。 |
| [SymbolItemOptions](arkts-arkui-arkui-advanced-chipgroup-symbolitemoptions-i.md) | ChipGroup的后缀图标选项类型。 |

## 示例

```TypeScript
### 示例1（无最右侧的builder）

该示例实现了在没有最右侧builder时的效果。


```

```TypeScript
### 示例2（有最右侧的builder）

通过配置suffix实现最右侧的自定义组件效果。


```

```TypeScript
### 示例3（设置Symbol类型图标）

该示例实现了IconGroupSuffix和ChipGroup传入SymbolGlyph资源。


```

```TypeScript
### 示例4（单选时无障碍朗读）

该示例实现ChipGroup在单选模式下，有后缀区域和无后缀区域的屏幕朗读功能，具体播报内容为accessibilityText属性中的内容。


```

```TypeScript
### 示例5（多选时无障碍朗读）

该示例实现了ChipGroup在多选模式下，有后缀区域和无后缀区域的屏幕朗读功能，具体播报内容为accessibilityText属性中的内容。


```

```TypeScript
### 示例6（设置系统材质样式）

该示例通过配置backgroundSystemMaterial和iconBackgroundSystemMaterial实现系统材质样式，开启自动反色功能使文本颜色适配背景色。

从API版本26.0.0开始，[ChipGroup](#chipgroup-1)新增backgroundSystemMaterial属性，[IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md)新增iconBackgroundSystemMaterial属性。

该示例配图为高算力设备强档效果。


```

```TypeScript
### 示例7（设置组件选中状态的系统材质样式）

该示例通过配置selectedBackgroundSystemMaterial实现组件选中状态的系统材质样式，开启自动反色功能使文本颜色适配背景色。

从API版本26.0.0开始，[ChipGroup](#chipgroup-1)新增selectedBackgroundSystemMaterial属性。
```
