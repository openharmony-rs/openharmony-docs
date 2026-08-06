# GlobalObserver

```TypeScript
export type GlobalObserver = (reason: GlobalError) => void
```

定义异常监听，可以作为 [errorManager.on('globalErrorOccurred')]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 和 [errorManager.on('globalUnhandledRejectionDetected')]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 的入参监听当前应用主线程事件处理事件。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-export type GlobalObserver = (reason: GlobalError) => void--><!--Device-errorManager-export type GlobalObserver = (reason: GlobalError) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 有关异常事件名字、消息、错误堆栈信息、异常线程名称和类型的对象。  |

