# @ohos.arkui.advanced.Chip

## 导入模块

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [Chip](arkts-arkui-arkui-advanced-chip-chip-f.md) | Chip组件用于标签展示和交互场景，支持自定义样式、图标、激活态等功能，适用于搜索框历史记录、邮件发送列表等场景，可快速实现标签的创建、删除和交互能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityOptions](arkts-arkui-arkui-advanced-chip-accessibilityoptions-i.md) | 后缀图标的无障碍朗读功能属性。 |
| [ChipOptions](arkts-arkui-arkui-advanced-chip-chipoptions-i.md) | ChipOptions定义Chip的样式及具体样式参数。 |
| [ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md) | symbol类型后缀图标的无障碍朗读功能属性及点击事件回调。 |
| [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md) | ChipSymbolGlyphOptions定义前缀图标和后缀图标的属性。 |
| [CloseOptions](arkts-arkui-arkui-advanced-chip-closeoptions-i.md) | CloseOptions用于定义Chip组件默认的关闭图标功能属性，包括无障碍功能属性，其中accessibilityText默认为"删除"。 |
| [IconCommonOptions](arkts-arkui-arkui-advanced-chip-iconcommonoptions-i.md) | IconCommonOptions定义图标的共通属性。 |
| [LabelMarginOptions](arkts-arkui-arkui-advanced-chip-labelmarginoptions-i.md) | LabelMarginOptions用于定义文本与左右侧图标之间间距。 |
| [LabelOptions](arkts-arkui-arkui-advanced-chip-labeloptions-i.md) | LabelOptions定义文本属性。 |
| [LocalizedLabelMarginOptions](arkts-arkui-arkui-advanced-chip-localizedlabelmarginoptions-i.md) | LocalizedLabelMarginOptions用于定义本地化文本与左右侧图标之间间距。 |
| [PrefixIconOptions](arkts-arkui-arkui-advanced-chip-prefixiconoptions-i.md) | PrefixIconOptions定义前缀图标的属性。 |
| [SuffixIconOptions](arkts-arkui-arkui-advanced-chip-suffixiconoptions-i.md) | SuffixIconOptions定义后缀图标的属性。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccessibilitySelectedType](arkts-arkui-arkui-advanced-chip-accessibilityselectedtype-e.md) | AccessibilitySelectedType定义Chip可指定的选中态类型，用于控制无障碍服务如何向用户传达组件的选中状态。不同的选中态类型提供了不同的语义和用户体验。 |
| [ChipSize](arkts-arkui-arkui-advanced-chip-chipsize-e.md) | Enum for ChipSize |

## 示例

```TypeScript
### 示例1（自定义后缀图标）

通过配置suffixIcon实现自定义操作块的后缀图标。


```

```TypeScript
### 示例2（设置默认后缀图标）

配置allowClose为true，显示关闭图标。


```

```TypeScript
### 示例3（不显示后缀图标）

配置allowClose为false，隐藏关闭图标。


```

```TypeScript
### 示例4（激活态操作块）

该示例通过配置activated实现激活态操作块。


```

```TypeScript
### 示例5（设置symbol类型图标）

Chip组件的前缀图标使用symbol类型资源展示。


```

```TypeScript
### 示例6（设置镜像效果）

配置direction实现Chip布局镜像化展示。


```

```TypeScript
### 示例7（Image类型无障碍朗读）

该示例代码实现Chip组件Image类型后缀图标的无障碍朗读功能，点击后缀图标播报“图标，按钮，新手提醒”。


```

```TypeScript
### 示例8（symbol类型无障碍朗读）

该示例代码实现Chip组件symbol类型后缀图标的无障碍朗读功能，点击后缀图标播报“音乐，按钮，新手提醒”。


```

```TypeScript
### 示例9（Chip组件无障碍朗读）

示例展示Chip组件的无障碍属性设置，包括不同的accessibilitySelectedType类型和各种无障碍属性。


```

```TypeScript
### 示例10（设置系统材质样式）

该示例通过配置backgroundSystemMaterial和activatedBackgroundSystemMaterial实现系统材质样式，启用自动反色功能适配标签文本颜色。

从API版本26.0.0开始，[ChipOptions](arkts-arkui-arkui-advanced-chip-chipoptions-i.md)新增backgroundSystemMaterial和activatedBackgroundSystemMaterial属性。
```
