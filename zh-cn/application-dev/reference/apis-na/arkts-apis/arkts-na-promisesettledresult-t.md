# PromiseSettledResult(定义ArkTS的异步操作)

```TypeScript
export type PromiseSettledResult<T> = PromiseFulfilledResult<T> | PromiseRejectedResult
```

表示Promise的完成结果。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type PromiseSettledResult<T> = PromiseFulfilledResult<T> | PromiseRejectedResult--><!--Device-unnamed-export type PromiseSettledResult<T> = PromiseFulfilledResult<T> | PromiseRejectedResult-End-->

**系统能力：** SystemCapability.Utils.Lang

| 类型 | 说明 |
| --- | --- |
| PromiseFulfilledResult&lt;T&gt; |  |
| PromiseRejectedResult |  |

