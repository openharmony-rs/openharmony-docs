# Queue

Queue的特点是先进先出，在尾部增加元素，在头部删除元素。根据循环队列的数据结构实现。

**起始版本：** 8

<!--Device-unnamed-declare class Queue<T>--><!--Device-unnamed-declare class Queue<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { Queue } from '@kit.ArkTS';
```

<a id="[symbol.iterator]"></a>
## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，每一项都是一个JavaScript对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Queue-[Symbol.iterator](): IterableIterator<T>--><!--Device-Queue-[Symbol.iterator](): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | @throws { BusinessError } 10200011 - The Symbol.iterator method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例：**

```TypeScript
let queue = new Queue<number>();
queue.add(2);
queue.add(4);
queue.add(5);
queue.add(4);

// 使用方法一：
for (let value of queue) {
  console.info("value:", value);
}
// value: 2
// value: 4
// value: 5
// value: 4

// 使用方法二：
// 获取Queue的迭代器
let iter = queue[Symbol.iterator]();
// 通过迭代器的next方法遍历元素
let temp: IteratorResult<number> = iter.next().value;
while(temp != undefined) {
  console.info("value: " + temp);
  temp = iter.next().value;
}
// value: 2
// value: 4
// value: 5
// value: 4

```

<a id="add"></a>
## add

```TypeScript
add(element: T): boolean
```

在队列尾部插入元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Queue-add(element: T): boolean--><!--Device-Queue-add(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 要插入的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 插入成功返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound. |

**示例：**

```TypeScript
class PersonInfo {
  name: string = "";
  age: string = "";
}
// 创建支持多种类型的Queue实例
let queue = new Queue<number | string | PersonInfo | number[]>();
// 向队列尾部添加元素
queue.add("a");
queue.add(1);
let b = [1, 2, 3];
queue.add(b);
let c : PersonInfo = {name : "Dylan", age : "13"};
queue.add(c);
console.info("result:", queue.length);  // result: 4

```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

Queue的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Queue-constructor()--><!--Device-Queue-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Queue's constructor cannot be directly invoked. |

**示例：**

```TypeScript
// 创建Queue实例
let queue = new Queue<number | string | Object>();
console.info("queue length:", queue.length);  // queue length: 0

```

<a id="foreach"></a>
## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, Queue?: Queue<T>) => void, thisArg?: Object): void
```

在遍历Queue实例对象中每一个元素的过程中，对每个元素执行回调函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Queue-forEach(callbackFn: (value: T, index?: number, Queue?: Queue<T>) => void, thisArg?: Object): void--><!--Device-Queue-forEach(callbackFn: (value: T, index?: number, Queue?: Queue<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, Queue?: Queue&lt;T&gt;) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackfn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例：**

```TypeScript
let queue = new Queue<number>();
queue.add(2);
queue.add(4);
queue.add(5);
queue.add(4);
// 遍历Queue中的每个元素，对每个元素执行回调函数
queue.forEach((value: number, index: number): void => {
  console.info("value:" + value, "index:" + index);
});
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3

```

<a id="getfirst"></a>
## getFirst

```TypeScript
getFirst(): T
```

获取队列的头元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Queue-getFirst(): T--><!--Device-Queue-getFirst(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回获取的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getFirst method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let queue = new Queue<number>();
queue.add(2);
queue.add(4);
queue.add(5);
queue.add(2);
// 获取队列的头元素
let result = queue.getFirst();
console.info("result:", result);  // result: 2

```

<a id="pop"></a>
## pop

```TypeScript
pop(): T
```

删除头元素并返回该删除元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Queue-pop(): T--><!--Device-Queue-pop(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The pop method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let queue = new Queue<number>();
queue.add(2);
queue.add(4);
queue.add(5);
queue.add(2);
queue.add(4);
// 删除队列头部元素，并返回被删除元素
let result = queue.pop();
console.info("result:", result);  // result: 2

```

## length

```TypeScript
length: number
```

Queue的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Queue-length: number--><!--Device-Queue-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

