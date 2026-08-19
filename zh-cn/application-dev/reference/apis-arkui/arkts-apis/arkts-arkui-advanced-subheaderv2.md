# @ohos.arkui.advanced.SubHeaderV2

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
| [SubHeaderV2](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2-s.md) | 子标题，用于列表项或内容项顶部，将该列表或内容划分为一个区块，子标题名称用来概括该区块内容。 该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于 [状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制子标题的数据和状态，实现更高效的用户界面刷新。 @internal/component/ets/common}和通用事件，编译工具 > 链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到SubHeaderV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议SubHeaderV2设 > 置通用属性和通用事件。 |

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
| [SubHeaderV2IconType](arkts-arkui-subheaderv2icontype-t.md) | SubHeaderV2IconType |
| [SubHeaderV2OperationItemAction](arkts-arkui-subheaderv2operationitemaction-t.md) | 操作区设置项的回调事件类型。 |
| [SubHeaderV2OperationItemType](arkts-arkui-subheaderv2operationitemtype-t.md) | SubHeaderV2OperationItemType |
| [SubHeaderV2SelectOnSelect](arkts-arkui-subheaderv2selectonselect-t.md) | 下拉菜单选中某一项的回调类型。 |
| [SubHeaderV2TitleBuilder](arkts-arkui-subheaderv2titlebuilder-t.md) | 自定义标题区内容的回调事件类型。 |

