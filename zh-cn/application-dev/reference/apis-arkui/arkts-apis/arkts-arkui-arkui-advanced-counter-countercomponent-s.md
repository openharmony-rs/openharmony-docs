# CounterComponent

```TypeScript
declare struct CounterComponent
```

创建Counter组件实例。

**起始版本：** 11

**装饰器类型：** @Component

<!--Device-unnamed-declare struct CounterComponent--><!--Device-unnamed-declare struct CounterComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## options

```TypeScript
options: CounterOptions
```

配置选项，用于配置Counter组件的类型和样式。包含type（Counter类型）、direction（布局方向）、numberOptions（列表型和紧凑型样式）、inlineOptions（数值内联样式）、dateOptions（日期内联样式）等配置项。

**类型：** [CounterOptions](arkts-arkui-arkui-advanced-counter-counteroptions-c.md)

**起始版本：** 11

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-CounterComponent-options: CounterOptions--><!--Device-CounterComponent-options: CounterOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
