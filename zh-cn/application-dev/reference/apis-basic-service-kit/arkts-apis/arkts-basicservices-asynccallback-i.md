# AsyncCallback

通用回调函数，携带错误参数和异步返回值，用于在异步操作完成时同时回传错误信息或成功数据。错误参数为[BusinessError](arkts-basicservices-businesserror-i.md)类型的信息。
异步返回值的类型由开发者自定义，回调将返回对应类型。

**起始版本：** 6

**系统能力：** SystemCapability.Base

## constructor

```TypeScript
(err: BusinessError<E>, data: T): void
```

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| err | BusinessError&lt;E&gt; | 是 | 接口调用失败的公共错误信息。接口调用成功时，此参数返回null。 |
| data | T | 是 | 接口调用成功时的异步返回数据，类型由开发者自定义。接口调用失败时，此参数不返回。 |

