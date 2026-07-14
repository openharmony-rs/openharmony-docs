# GlobalObserver

```TypeScript
export type GlobalObserver = (reason: GlobalError) => void
```

定义异常监听，可以作为
[errorManager.on('globalErrorOccurred')](arkts-ability-on-f.md#on-6)
和
[errorManager.on('globalUnhandledRejectionDetected')](arkts-ability-on-f.md#on-4)
的入参监听当前应用主线程事件处理事件。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | GlobalError | 是 | 有关异常事件名字、消息、错误堆栈信息、异常线程名称和类型的对象。 |

