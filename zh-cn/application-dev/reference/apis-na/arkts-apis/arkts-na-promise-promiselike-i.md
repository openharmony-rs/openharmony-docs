# PromiseLike(定义ArkTS的异步操作)

表示一个thenable对象。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export interface PromiseLike--><!--Device-unnamed-export interface PromiseLike-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## then

```TypeScript
then<U = T, E = never>(onFulfilled: (value: T) => PromiseLike<U> | U,
        onRejected?: (error: Error) => PromiseLike<E> | E): PromiseLike<Awaited<U | E>>
```

为Promise的解析和/或拒绝添加回调函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromiseLike-then<U = T, E = never>(onFulfilled: (value: T) => PromiseLike<U> | U,        onRejected?: (error: Error) => PromiseLike<E> | E): PromiseLike<Awaited<U | E>>--><!--Device-PromiseLike-then<U = T, E = never>(onFulfilled: (value: T) => PromiseLike<U> | U,        onRejected?: (error: Error) => PromiseLike<E> | E): PromiseLike<Awaited<U | E>>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onFulfilled | (value: T) =&gt; PromiseLike&lt;U&gt; \| U | 是 | Promise解析时执行的回调函数。 |
| onRejected | (error: Error) =&gt; PromiseLike&lt;E&gt; \| E | 否 | Promise拒绝时执行的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PromiseLike](arkts-na-promise-promiselike-i.md)&lt;Awaited&lt;U \| E&gt;&gt; | 回调函数结果的PromiseLike。 |

