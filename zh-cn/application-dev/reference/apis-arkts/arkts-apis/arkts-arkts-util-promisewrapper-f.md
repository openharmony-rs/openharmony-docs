# promiseWrapper

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

<a id="promisewrapper"></a>
## promiseWrapper

```TypeScript
function promiseWrapper(original: (err: Object, value: Object) => void): Object
```

接收一个使用错误优先回调模式的函数（即最后一个参数为 `(err, value) => callback`），并通过 promise 返回结果。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [promisify](arkts-arkts-util-promisify-f.md#promisify-1)

<!--Device-util-function promiseWrapper(original: (err: Object, value: Object) => void): Object--><!--Device-util-function promiseWrapper(original: (err: Object, value: Object) => void): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| original | (err: Object, value: Object) =&gt; void | 是 | 异步函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 错误优先风格（即最后一个参数为 (err, value) => ... ）的 promise。 |

