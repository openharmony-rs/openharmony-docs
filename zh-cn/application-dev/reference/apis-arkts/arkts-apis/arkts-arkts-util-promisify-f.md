# promisify

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## promisify

```TypeScript
function promisify(original: (err: Object, value: Object) => void): Function
```

接收一个使用错误优先回调模式的函数（即最后一个参数为 `(err, value) => callback`），并通过 promise 返回结果。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-util-function promisify(original: (err: Object, value: Object) => void): Function--><!--Device-util-function promisify(original: (err: Object, value: Object) => void): Function-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| original | (err: Object, value: Object) => void | 是 | 函数，其中第一个参数 **err** 表示拒绝的原因（如果 promise 已经 resolved，该值为**null**），第二个参数 **value** 表示 resolved 的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| function | 返回一个返回 promises 的函数。<br>**适用版本：** 9 - 11 |
| Function | Promise 函数。<br>**适用版本：** 10+ |

**示例：**

```TypeScript
async function fn() {
  return 'hello world';
}
const addCall = util.promisify(util.callbackWrapper(fn));
(async () => {
  try {
    let res: string = await addCall();
    console.info(res);
    // 输出结果：hello world
  } catch (err) {
    console.info(err);
  }
})();

```

