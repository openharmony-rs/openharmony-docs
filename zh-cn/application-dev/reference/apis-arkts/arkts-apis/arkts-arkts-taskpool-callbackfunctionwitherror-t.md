# CallbackFunctionWithError

```TypeScript
type CallbackFunctionWithError = (e: Error) => void
```

注册接收错误对象的回调函数类型。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-type CallbackFunctionWithError = (e: Error) => void--><!--Device-taskpool-type CallbackFunctionWithError = (e: Error) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| e | Error | 是 | 错误信息对象。 |

