# CounterComponent

```TypeScript
declare struct CounterComponent
```

Counter组件用于精确调节数值，支持列表型、紧凑型、数值内联型和日期内联型四种样式，适用于购物数量调节、参数设置、日期选择等场景，具有灵活的样式配置和事件回调能力。

> **说明：** 
> 
> - 如果Counter设置[通用属性](../arkts-components/arkts-arkui-common-comp.md#common)和[通用事件](../arkts-components/arkts-arkui-common-comp.md#common)，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到Counter本身。这可能导致开发者设置的通用属性或通用事件的效果不生效或不符合预期，因此，不建议为Counter设置通用属性和通用事件。
## 导入模块

```ts
import { CounterType, CounterComponent, CounterOptions, DateData } from '@kit.ArkUI';
```

  
## 子组件

无

**起始版本：** 11

**装饰器类型：** @Component

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
