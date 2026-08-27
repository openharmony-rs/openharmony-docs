# MonitorDecorator

```TypeScript
declare type MonitorDecorator = (value: string | MonitorDecoratorOptions, ...args: string[]) => MethodDecorator
```

@Monitor装饰器的实际类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| [MonitorDecoratorOptions](arkts-arkui-monitordecoratoroptions-i.md) | 是 | 从API版本26.0.0开始，该参数也可以为MonitorDecoratorOptions类型的对象， 用于配置通配符能力。 |
| args | string[] | 是 | 用于监听的状态变量名路径数组，路径以点号（.）分隔表示嵌套属性（如'a.b.c'），内容由开发者指定。 当开发者已使用MonitorDecoratorOptions或传入多个字符串时，入参为该类型。不传该参数时默认为空，当value为string类型时，仅监听value参数指定的状态变量路径； 当value为MonitorDecoratorOptions类型时，需通过该参数指定监听的状态变量路径。传入undefined时，对应的监听不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| MethodDecorator | 方法装饰器，开发者无需关注该返回值。 |
