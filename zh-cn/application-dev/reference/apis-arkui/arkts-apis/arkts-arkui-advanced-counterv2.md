# @ohos.arkui.advanced.CounterV2

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [CounterV2CommonOptions](arkts-arkui-counterv2commonoptions-c.md) | CounterV2CommonOptions定义了CounterV2的共通属性和事件。 |
| [CounterV2DateData](arkts-arkui-counterv2datedata-c.md) | CounterV2DateData定义了日期通用属性和方法，包括年、月、日。 |
| [CounterV2DateStyleOptions](arkts-arkui-counterv2datestyleoptions-c.md) | CounterV2DateStyleOptions定义日期内联型CounterV2的属性和事件。继承于[CounterV2CommonOptions](arkts-arkui-counterv2commonoptions-c.md)。 |
| [CounterV2InlineStyleOptions](arkts-arkui-counterv2inlinestyleoptions-c.md) | CounterV2InlineStyleOptions定义了数值内联型CounterV2的属性和事件。继承于[CounterV2CommonOptions](arkts-arkui-counterv2commonoptions-c.md)。 |
| [CounterV2NumberStyleOptions](arkts-arkui-counterv2numberstyleoptions-c.md) | CounterV2NumberStyleOptions定义了列表型和紧凑型CounterV2的属性和事件。继承于[CounterV2InlineStyleOptions](arkts-arkui-counterv2inlinestyleoptions-c.md)。 |
| [CounterV2Options](arkts-arkui-counterv2options-c.md) | CounterV2Options定义CounterV2类型及样式。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [CounterV2Component](arkts-arkui-counterv2component-s.md) | CounterV2组件用于精确调节数值。该组件基于[状态管理（V2）](../../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于[状态管理（V1）](../../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制Counter的数据和状态，实现更高效的用户界面刷新。@link ./@internal/component/ets/common}和[通用事件](./@internal/component/ets/common)，编译工具链会&gt; 额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到CounterV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议CounterV2设置通用属性和&gt; 通用事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CounterV2Type](arkts-arkui-counterv2type-e.md) | CounterV2Type指定CounterV2类型。各类型CounterV2组件的展示效果可参考[示例1（列表型CounterV2）](../../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-CounterV2.md#示例1列表型counterv2)、[示例2（紧凑型CounterV2）](../../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-CounterV2.md#示例2紧凑型counterv2)、[示例3（数值内联型CounterV2）](../../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-CounterV2.md#示例3数值内联型counterv2)、[示例4（日期内联型CounterV2）](../../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-CounterV2.md#示例4日期内联型counterv2)。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnCounterV2HoverCallback](arkts-arkui-oncounterv2hovercallback-t.md) | 定义CounterV2的鼠标悬浮回调类型。 |
| [OnDateCounterV2ChangeCallback](arkts-arkui-ondatecounterv2changecallback-t.md) | 定义日期型CounterV2的日期变化回调类型。 |
| [OnInlineCounterV2Change](arkts-arkui-oninlinecounterv2change-t.md) | 定义数值内联型CounterV2的值变化回调类型。 |

