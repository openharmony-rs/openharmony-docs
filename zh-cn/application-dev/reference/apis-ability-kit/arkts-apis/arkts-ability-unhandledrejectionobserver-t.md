# UnhandledRejectionObserver

```TypeScript
export type UnhandledRejectionObserver = (reason: Error | any, promise: Promise<any>) => void
```

定义异常监听，用于捕获Promise异步操作失败的原因。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | Error \| any | 是 | 通常是`Error`类型，表示被拒绝的理由。 |
| promise | Promise&lt;any&gt; | 是 | 被拒绝的promise。 |

