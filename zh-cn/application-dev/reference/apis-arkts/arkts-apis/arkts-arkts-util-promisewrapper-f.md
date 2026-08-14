# promiseWrapper

## promiseWrapper

```TypeScript
function promiseWrapper(original: (err: Object, value: Object) => void): Object
```

接收一个使用错误优先回调模式的函数（即最后一个参数为 `(err, value) => callback`），并通过 promise 返回结果。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [promisify](arkts-arkts-util-promisify-f.md#promisify)

<!--Device-util-function promiseWrapper(original: (err: Object, value: Object) => void): Object--><!--Device-util-function promiseWrapper(original: (err: Object, value: Object) => void): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| original | (err: Object, value: Object) =&gt; void | 是 | 采用错误优先回调模式的函数，第一个参数err是拒绝原因，第二个参数value是已解决的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 错误优先风格（即最后一个参数为 (err, value) => ... ）的 promise。 |

