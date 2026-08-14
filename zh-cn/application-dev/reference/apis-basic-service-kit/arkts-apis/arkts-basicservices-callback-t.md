# Callback

```TypeScript
export type Callback<T> = (data: T) => void
```

通用回调函数。开发者在使用时，可自定义data的类型，回调将返回对应类型的信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export type Callback<T> = (data: T) => void--><!--Device-unnamed-export type Callback<T> = (data: T) => void-End-->

**系统能力：** SystemCapability.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | T | 是 | 接口调用时的公共回调信息。 |

