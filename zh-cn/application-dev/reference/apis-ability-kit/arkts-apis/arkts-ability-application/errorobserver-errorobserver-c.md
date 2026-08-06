# ErrorObserver

定义异常监听，可以作为 [errorManager.on('error')]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 的入参监听当前应用发生的异常。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

<!--Device-unnamed-export default class ErrorObserver--><!--Device-unnamed-export default class ErrorObserver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onException

```TypeScript
onException?(errObject: Error): void
```

应用产生异常，上报js层时的回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ErrorObserver-onException?(errObject: Error): void--><!--Device-ErrorObserver-onException?(errObject: Error): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errObject | Error | 是 | 有关异常事件名字、消息和错误堆栈信息的对象。 |

## onUnhandledException

```TypeScript
onUnhandledException(errMsg: string): void
```

应用产生未捕获的异常时的回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ErrorObserver-onUnhandledException(errMsg: string): void--><!--Device-ErrorObserver-onUnhandledException(errMsg: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errMsg | string | 是 | 有关异常的消息和错误堆栈跟踪。 |

