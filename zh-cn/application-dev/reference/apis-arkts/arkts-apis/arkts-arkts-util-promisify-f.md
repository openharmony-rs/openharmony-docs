# promisify

## 导入模块

```TypeScript
import { ArrayList } from '@kit.ArkTS';
import { ArrayListComparatorFn } from '@kit.ArkTS';
import { ArrayListForEachCb } from '@kit.ArkTS';
import { ArrayListReplaceCb } from '@kit.ArkTS';
import { util } from '@kit.ArkTS';
import { Deque } from '@kit.ArkTS';
import { DequeForEachCb } from '@kit.ArkTS';
import { HashMap } from '@kit.ArkTS';
import { HashMapCbFn } from '@kit.ArkTS';
import { HashSet } from '@kit.ArkTS';
import { HashSetCbFn } from '@kit.ArkTS';
import { LightWeightMap } from '@kit.ArkTS';
import { LightWeightMapCbFn } from '@kit.ArkTS';
import { LightWeightSet } from '@kit.ArkTS';
import { LightWeightSetForEachCb } from '@kit.ArkTS';
import { LinkedList } from '@kit.ArkTS';
import { LinkedListForEachCb } from '@kit.ArkTS';
import { List } from '@kit.ArkTS';
import { ListComparatorFn } from '@kit.ArkTS';
import { ListForEachCb } from '@kit.ArkTS';
import { ListReplaceCb } from '@kit.ArkTS';
import { PlainArray } from '@kit.ArkTS';
import { PlainArrayForEachCb } from '@kit.ArkTS';
import { Queue } from '@kit.ArkTS';
import { QueueForEachCb } from '@kit.ArkTS';
import { Stack } from '@kit.ArkTS';
import { StackForEachCb } from '@kit.ArkTS';
import { TreeMap } from '@kit.ArkTS';
import { TreeMapForEachCb } from '@kit.ArkTS';
import { TreeMapComparator } from '@kit.ArkTS';
import { TreeSet } from '@kit.ArkTS';
import { TreeSetForEachCb } from '@kit.ArkTS';
import { TreeSetComparator } from '@kit.ArkTS';
import { stream } from '@kit.ArkTS';
import { Vector } from '@kit.ArkTS';
import { JSON } from '@kit.ArkTS';
```

## promisify

```TypeScript
function promisify(original: (err: Object, value: Object) => void): Function
```

接收一个采用"错误优先"回调模式的函数，即以`(err, value) => callback`作为最后一个参数，并返回其Promise函数。 适用于将旧版回调式异步API转换为Promise风格，以便使用async/await语法进行调用，从而简化异步代码编写。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-util-function promisify(original: (err: Object, value: Object) => void): Function--><!--Device-util-function promisify(original: (err: Object, value: Object) => void): Function-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| original | (err: Object, value: Object) =&gt; void | 是 | 回调函数中第一个参数 **err** 是拒绝原因（如果Promise已解决，则为null），第二个参数 **value** 是已解决的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Function | 返回一个Promise函数，该Promise在原始回调函数成功执行时resolve为回调的value值，在原始回调函数执行出错时reject为错误对象。 |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
let func: Function =
  (val: Any, callback: (err: Error | null, ...value: FixedArray<Any>) => void) => {
  callback(null, val);
}
let val = util.promisify(func);
let res = await val(42);
console.info(new String(res)); // 输出结果：42
```

