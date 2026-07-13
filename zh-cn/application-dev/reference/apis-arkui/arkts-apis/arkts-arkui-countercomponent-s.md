# CounterComponent

Counter组件用于精确调节数值。

> **说明：**

> - 如果Counter设置[通用属性](./@internal/component/ets/common)和[通用事件](./@internal/component/ets/common)，编译工具链会额外
> 生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到Counter本身。这可能导致开发者设置的通用属性或通用事件的效果不生效或不符合预期，因此，不建议Counter设置通用属性和通用事
> 件。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: CounterOptions
```

定义Counter组件的类型。

**类型：** CounterOptions

**起始版本：** 11

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

