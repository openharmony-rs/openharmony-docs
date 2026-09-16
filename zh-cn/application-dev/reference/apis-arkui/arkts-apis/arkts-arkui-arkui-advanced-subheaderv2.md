# @ohos.arkui.advanced.SubHeaderV2(api/@ohos.arkui.advanced.SubHeaderV2.d.ts)

## 导入模块

```TypeScript
import { SubHeaderV2IconType, SubHeaderV2Title, SubHeaderV2Select, SubHeaderV2, SubHeaderV2OperationType, SubHeaderV2OperationItem, SubHeaderV2OperationItemType } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SubHeaderV2OperationItem](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationitem-c.md) | 操作区的设置项。 |
| [SubHeaderV2Select](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2select-c.md) | 下拉选择器配置项，包含下拉选项内容、选中状态及回调事件。 |
| [SubHeaderV2Title](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2title-c.md) | 标题设置项。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [SubHeaderV2](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2-s.md) | 子标题，用于列表项或内容项顶部，将该列表或内容划分为一个区块，子标题名称用来概括该区块内容。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [SubHeaderV2OperationItemOptions](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationitemoptions-i.md) | 用于构建SubHeaderV2OperationItem对象。 |
| [SubHeaderV2SelectOptions](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2selectoptions-i.md) | 用于构建SubHeaderV2Select对象。 |
| [SubHeaderV2TitleOptions](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2titleoptions-i.md) | 用于构建SubHeaderV2Title对象。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SubHeaderV2OperationType](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationtype-e.md) | 操作区元素样式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SubHeaderV2IconType](arkts-arkui-subheaderv2icontype-t.md) | [SubHeaderV2IconType](arkts-arkui-subheaderv2icontype-t.md) |
| [SubHeaderV2OperationItemAction](arkts-arkui-subheaderv2operationitemaction-t.md) | 操作区设置项的回调事件类型。 |
| [SubHeaderV2OperationItemType](arkts-arkui-subheaderv2operationitemtype-t.md) | [SubHeaderV2OperationItemType](arkts-arkui-subheaderv2operationitemtype-t.md) |
| [SubHeaderV2SelectOnSelect](arkts-arkui-subheaderv2selectonselect-t.md) | 下拉菜单选中某一项的回调类型。 |
| [SubHeaderV2TitleBuilder](arkts-arkui-subheaderv2titlebuilder-t.md) | 自定义标题区内容的回调事件类型。 |

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

该示例主要演示SubHeaderV2设置titleBuilder自定义标题内容的效果。


```

```TypeScript
### 示例7（自定义标题样式）

该示例主要演示SubHeaderV2设置标题和副标题字体样式。


```

```TypeScript
### 示例8（右侧按钮自定义播报）

该示例通过设置SubHeaderV2的右侧按钮属性accessibilityText、accessibilityDescription、accessibilityLevel自定义屏幕朗读播报文本。


```

```TypeScript
### 示例9（右侧按钮设置默认获焦）

在获焦状态下，该示例通过设置SubHeaderV2的右侧按钮属性defaultFocus使其默认获焦。

从API version 18开始，在[SubHeaderV2OperationItem](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationitemoptions-i.md)中新增defaultFocus接口。
```
