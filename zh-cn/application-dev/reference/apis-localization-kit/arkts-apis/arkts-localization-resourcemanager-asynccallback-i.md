# AsyncCallback

异步回调接口

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)

<!--Device-resourceManager-export interface AsyncCallback--><!--Device-resourceManager-export interface AsyncCallback-End-->

**系统能力：** SystemCapability.Global.ResourceManager

## constructor

```TypeScript
(err: Error, data: T): void
```

异步回调函数，携带错误参数和异步返回值。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)

<!--Device-AsyncCallback-(err: Error, data: T): void--><!--Device-AsyncCallback-(err: Error, data: T): void-End-->

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| err | Error | 是 | 接口调用失败的错误信息。 |
| data | T | 是 | 接口调用时的回调信息。 |

