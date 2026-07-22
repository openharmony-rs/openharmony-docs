# @ohos.arkui.advanced.Filter

## 导入模块

```TypeScript
import { FilterType, Filter, FilterParams, FilterResult } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [FilterParams](arkts-arkui-arkui-advanced-filter-filterparams-c.md) | This parameter is used to define the input of each filtering dimension. |
| [FilterResult](arkts-arkui-arkui-advanced-filter-filterresult-c.md) | This parameter specifies the selection result of a filtering dimension.The index starts from 0. |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [Filter](arkts-arkui-arkui-advanced-filter-filter-s.md) | 多条件筛选，帮助用户在大量信息中找到所需内容，应结合具体场景选择合适筛选方式。多条件筛选控件由筛选器与悬浮条构成，悬浮条可下拉展示悬浮筛选器。筛选器样式可分为多行可折叠类型与多行列表类型，并可以在筛选器最后一行附加快捷筛选器。 @internal/component/ets/common}和[通用事件](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)，编译工具链会额外生  > 成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到Filter本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议Filter设置通用属性和通用事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FilterType](arkts-arkui-arkui-advanced-filter-filtertype-e.md) | 声明筛选器类型 |

