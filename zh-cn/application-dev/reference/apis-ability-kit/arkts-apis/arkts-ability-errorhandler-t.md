# ErrorHandler

```TypeScript
export type ErrorHandler = (errObject: Error) => void
```

当ArkTS运行时抛出用户未捕获异常时，将调用ErrorHandler。

**起始版本：** 21

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errObject | Error | 是 | 有关异常事件名字、消息、错误堆栈信息的对象。 |

