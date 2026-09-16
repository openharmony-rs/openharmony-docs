# @ohos.arkui.advanced.SubHeader

## 导入模块

```TypeScript
import { OperationOption, OperationType, SelectOptions, SubHeader, SymbolOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [OperationOption](arkts-arkui-arkui-advanced-subheader-operationoption-c.md) | Declare type OperationOption |
| [SelectOptions](arkts-arkui-arkui-advanced-subheader-selectoptions-c.md) | Declare type SelectOption |
| [SymbolOptions](arkts-arkui-arkui-advanced-subheader-symboloptions-c.md) | Declare type SymbolOptions |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [SubHeader](arkts-arkui-arkui-advanced-subheader-subheader-s.md) | 子标题组件，用于列表项或内容项顶部，将该列表或内容划分为一个区块，子标题名称用来概括该区块内容。支持多种样式配置，包括图标、主副标题、下拉选择器和操作按钮等，可满足不同场景下的内容分区和导航需求，提升界面的信息层次感和用户体验。适用于列表分组、内容分类展示、表单分区等场景。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [OperationType](arkts-arkui-arkui-advanced-subheader-operationtype-e.md) | 定义子标题操作区的元素样式。 |

## 示例

```TypeScript
### 示例1（效率型子标题）

该示例主要演示子标题左侧为icon、secondaryTitle，右侧operationType为按钮类型。


```

```TypeScript
### 示例2（双行文本内容型子标题）

该示例主要演示子标题左侧为primaryTitle、secondaryTitle，右侧operationType类型为TEXT_ARROW。


```

```TypeScript
### 示例3（spinner型内容型子标题）

该示例主要演示子标题左侧为select，右侧operationType类型为ICON_GROUP。


```

```TypeScript
### 示例4（设置左侧symbol图标）

该示例主要演示子标题左侧icon设置symbol图标。


```

```TypeScript
### 示例5（设置右侧symbol图标）

该示例主要演示子标题operationType设置为OperationType.ICON_GROUP，operationItem的value设置为symbol图标。


```

```TypeScript
### 示例6（自定义标题内容）

该示例主要演示SubHeader设置titleBuilder自定义标题内容的效果。设置titleBuilder后，primaryTitle、secondaryTitle属性将不生效。


```

```TypeScript
### 示例7（自定义标题样式）

该示例主要演示SubHeader设置标题和副标题字体样式以及标题内外边距的效果。


```

```TypeScript
### 示例8（右侧按钮自定义播报）

从API version 18开始，该示例通过设置SubHeader的右侧按钮属性accessibilityText、accessibilityDescription、accessibilityLevel自定义屏幕朗读播报文本。


```

```TypeScript
### 示例9（右侧按钮设置默认获焦）

在获焦状态下，该示例通过设置SubHeader的右侧按钮属性defaultFocus使其默认获焦。

从API version 18开始，在[OperationOption](arkts-arkui-arkui-advanced-subheader-operationoption-c.md)中新增defaultFocus接口。
```
