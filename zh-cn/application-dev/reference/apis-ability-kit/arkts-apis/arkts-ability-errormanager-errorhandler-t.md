# ErrorHandler

```TypeScript
export type ErrorHandler = (errObject: Error) => void
```

当ArkTS运行时抛出用户未捕获异常时，将调用ErrorHandler。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-export type ErrorHandler = (errObject: Error) => void--><!--Device-errorManager-export type ErrorHandler = (errObject: Error) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errObject | Error | 是 | 有关异常事件名字、消息、错误堆栈信息的对象。 |

