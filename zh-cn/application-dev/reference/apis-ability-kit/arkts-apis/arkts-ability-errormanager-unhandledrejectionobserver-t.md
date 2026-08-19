# UnhandledRejectionObserver

```TypeScript
export type UnhandledRejectionObserver = (reason: Error | Any, promise: Promise<Any>) => void
```

当发生未处理的拒绝时，系统将调用此观测器。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-errorManager-export type UnhandledRejectionObserver = (reason: Error | Any, promise: Promise<Any>) => void--><!--Device-errorManager-export type UnhandledRejectionObserver = (reason: Error | Any, promise: Promise<Any>) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | Error \| Any | 是 | 拒绝的原因，通常为Error类型 |
| promise | Promise&lt;Any&gt; | 是 | 被拒绝的Promise |

