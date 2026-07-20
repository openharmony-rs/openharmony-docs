# @ohos.arkui.advanced.ComposeListItemV2

## 导入模块

```TypeScript
import { OperateCheckV2Options, ComposeListItemV2, IconTypeV2, OperateIconV2, OperateCheckV2, OperateItemV2, OperateItemV2Options, OperateIconV2Options, OperateButtonV2, OperateButtonV2Options, ContentItemV2, ContentItemV2Options } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ContentItemV2](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2-c.md) | 列表左侧显示的图标、图标大小以及中间元素文字内容。 |
| [OperateButtonV2](arkts-arkui-arkui-advanced-composelistitemv2-operatebuttonv2-c.md) | 列表项右侧按钮元素的类型。 |
| [OperateCheckV2](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2-c.md) | 列表项右侧元素为Switch、CheckBox、Radio的类型。当列表项右侧元素需要使用Switch、CheckBox、Radio时，可通过该类型配置对应属性。 |
| [OperateIconV2](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2-c.md) | 列表项右侧图标元素的类型。 |
| [OperateItemV2](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2-c.md) | 列表项右侧显示的元素类型。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ComposeListItemV2](arkts-arkui-arkui-advanced-composelistitemv2-composelistitemv2-s.md) | 该组件用于展示一系列宽度相同的列表项，适用于展示连续、多行的同类数据组合（如图片与文本）。  该组件基于[状态管理（V2）](docroot://ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于[状态管理（V1）](docroot://ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制列表项的数据和状态，实现更高效的用户界面刷新。  > **说明:**  >  > - 该组件仅可在Stage模型下使用。  >  > - 如果ComposeListItemV2设置[通用属性](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)和  > [通用事件](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到  > ComposeListItemV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议ComposeListItemV2设置通用属性和通用事件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ContentItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2options-i.md) | ContentItemV2构造函数的参数选项。 |
| [OperateButtonV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operatebuttonv2options-i.md) | OperateButtonV2构造函数的参数选项。 |
| [OperateCheckV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2options-i.md) | OperateCheckV2构造函数的参数选项。 |
| [OperateIconV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2options-i.md) | OperateIconV2构造函数的参数选项。 |
| [OperateItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2options-i.md) | OperateItemV2构造函数的参数选项。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [IconTypeV2](arkts-arkui-arkui-advanced-composelistitemv2-icontypev2-e.md) | 列表左侧图标类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnActionCallback](arkts-arkui-onactioncallback-t.md) | 列表项右侧元素为图标/箭头，通过点击触发回调函数的类型。 |
| [OnChangeCallback](arkts-arkui-onchangecallback-t.md) | 列表项右侧元素为Switch/CheckBox/Radio时，当状态发生改变时的回调函数对应的类型。 |

