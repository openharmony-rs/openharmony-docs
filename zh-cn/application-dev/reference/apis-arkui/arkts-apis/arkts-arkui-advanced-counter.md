# @ohos.arkui.advanced.Counter

## 导入模块

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md) | CommonOptions定义了Counter的通用属性和事件。 |
| [CounterOptions](arkts-arkui-arkui-advanced-counter-counteroptions-c.md) | CounterOptions定义了Counter类型及样式。选择不同的Counter类型时，需选择对应的Counter样式。若样式参数与类型不匹配，将使用该类型对应的默认样式。 |
| [DateData](arkts-arkui-arkui-advanced-counter-datedata-c.md) | DateData定义了日期通用属性和方法，包括年、月、日。 |
| [DateStyleOptions](arkts-arkui-arkui-advanced-counter-datestyleoptions-c.md) | DateStyleOptions定义了日期内联型Counter的属性和事件。继承于[CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)。 |
| [InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md) | InlineStyleOptions定义了数值内联型Counter的属性和事件。继承于[CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)。 |
| [NumberStyleOptions](arkts-arkui-arkui-advanced-counter-numberstyleoptions-c.md) | NumberStyleOptions定义了列表型和紧凑型Counter的属性和事件。继承于[InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md)，包含该接口所有属性。本节仅展示新增属性，继承属性请参见父接口。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [CounterComponent](arkts-arkui-arkui-advanced-counter-countercomponent-s.md) | Counter组件用于精确调节数值，支持列表型、紧凑型、数值内联型和日期内联型四种样式，适用于购物数量调节、参数设置、日期选择等场景，具有灵活的样式配置和事件回调能力。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CounterType](arkts-arkui-arkui-advanced-counter-countertype-e.md) | CounterType指定Counter类型。 |
