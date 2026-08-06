# AsyncCallback

```TypeScript
export type AsyncCallback<T, E = void> = (err: BusinessError<E> | null, data: T | undefined) => void
```

通用回调函数，携带错误参数和异步返回值。错误参数为[BusinessError]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型的信息。异步返回值的类型由开发者自定义，回调将返回对应类型的信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export type AsyncCallback<T, E = void> = (err: BusinessError<E> | null, data: T | undefined) => void--><!--Device-unnamed-export type AsyncCallback<T, E = void> = (err: BusinessError<E> | null, data: T | undefined) => void-End-->

**系统能力：** SystemCapability.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| err | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;E&gt; \| null | 是 | 接口调用失败的公共错误信息。  |
| data | T \| undefined | 是 | 接口调用时的公共回调信息。  |

