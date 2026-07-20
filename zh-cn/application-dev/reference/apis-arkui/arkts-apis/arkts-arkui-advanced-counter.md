# @ohos.arkui.advanced.Counter

## 导入模块

```TypeScript
import { CounterType, DateData, CounterComponent, CounterOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md) | CommonOptions定义了Counter的共通属性和事件。 |
| [CounterOptions](arkts-arkui-arkui-advanced-counter-counteroptions-c.md) | CounterOptions定义Counter类型及样式。 |
| [DateData](arkts-arkui-arkui-advanced-counter-datedata-c.md) | DateData定义了日期通用属性和方法，包括年、月、日。 |
| [DateStyleOptions](arkts-arkui-arkui-advanced-counter-datestyleoptions-c.md) | DateStyleOptions定义日期内联型Counter的属性和事件。  继承于[CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)。 |
| [InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md) | InlineStyleOptions定义了数值内联型Counter的属性和事件。  继承于[CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)。 |
| [NumberStyleOptions](arkts-arkui-arkui-advanced-counter-numberstyleoptions-c.md) | NumberStyleOptions定义了列表型和紧凑型Counter的属性和事件。  继承于[InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md)。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [CounterComponent](arkts-arkui-arkui-advanced-counter-countercomponent-s.md) | Counter组件用于精确调节数值。  @internal/component/ets/common}和[通用事件](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)，编译工具链会额外  > 生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到Counter本身。这可能导致开发者设置的通用属性或通用事件的效果不生效或不符合预期，因此，不建议Counter设置通用属性和通用事  > 件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CounterType](arkts-arkui-arkui-advanced-counter-countertype-e.md) | CounterType指定Counter类型。 |

