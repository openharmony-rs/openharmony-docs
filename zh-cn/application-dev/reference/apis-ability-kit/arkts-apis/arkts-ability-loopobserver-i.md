# LoopObserver

定义异常监听，可以作为
[ErrorManager.on](arkts-ability-on-f.md#on-2)
的入参监听当前应用主线程事件处理事件。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onLoopTimeOut

```TypeScript
onLoopTimeOut?(timeout: number): void
```

将在js运行时应用主线程处理事件超时的回调。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 返回应用主线程消息实际执行时间。阈值必须大于0。 单位为毫秒（ms）。 |

