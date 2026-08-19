# ErrorCallback

```TypeScript
export type ErrorCallback<T extends Error = BusinessError> = (err: T) => void
```

通用回调函数，携带错误参数。回调返回的信息为[BusinessError](arkts-basicservices-base-businesserror-c.md)类型的信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export type ErrorCallback<T extends Error = BusinessError> = (err: T) => void--><!--Device-unnamed-export type ErrorCallback<T extends Error = BusinessError> = (err: T) => void-End-->

**系统能力：** SystemCapability.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| err | T | 是 | 接口调用失败的公共错误信息。 |

