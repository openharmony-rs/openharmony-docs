# Deque

Deque（double ended queue）是基于队列数据结构实现的序列容器，具备先进先出和先进后出的特点。支持在两端进行元素的插入和删除。

**起始版本：** 8

<!--Device-unnamed-declare class Deque<T>--><!--Device-unnamed-declare class Deque<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { Deque } from '@kit.ArkTS';
```

<a id="[symbol.iterator]"></a>
## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Deque-[Symbol.iterator](): IterableIterator<T>--><!--Device-Deque-[Symbol.iterator](): IterableIterator<T>-End-->

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
let deque = new Deque<number>();
deque.insertFront(2);
deque.insertFront(4);
deque.insertFront(5);
deque.insertFront(4);

// 使用方法一：
for (let item of deque) {
  console.info("value:" + item);
}
/*
输出结果：
value:4
value:5
value:4
value:2
 */

// 使用方法二：
let iter = deque[Symbol.iterator]();
let iterResult: IteratorResult<number> = iter.next();
while (!iterResult.done) {
  console.info("value:" + iterResult.value);
  iterResult = iter.next();
}
/*
输出结果：
value:4
value:5
value:4
value:2
 */

```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

Deque的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Deque-constructor()--><!--Device-Deque-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Deque's constructor cannot be directly invoked. |

**示例：**

```TypeScript
// 创建Deque实例
let deque = new Deque<string | number | boolean | Object>();

```

<a id="foreach"></a>
## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, deque?: Deque<T>) => void, thisArg?: Object): void
```

在遍历Deque实例对象中每一个元素的过程中，对每个元素执行回调函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Deque-forEach(callbackFn: (value: T, index?: number, deque?: Deque<T>) => void, thisArg?: Object): void--><!--Device-Deque-forEach(callbackFn: (value: T, index?: number, deque?: Deque<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, deque?: Deque&lt;T&gt;) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例：**

```TypeScript
// 创建Deque实例并插入元素
let deque = new Deque<number>();
deque.insertFront(2);
deque.insertEnd(3);
deque.insertFront(1);
deque.insertEnd(4);
// 使用forEach遍历Deque中每个元素并执行回调函数
deque.forEach((value: number, index: number): void => {
  console.info("value:" + value, "index:" + index);
});
/*
输出结果：value:1 index:0
         value:2 index:1
         value:3 index:2
         value:4 index:3
 */

```

<a id="getfirst"></a>
## getFirst

```TypeScript
getFirst(): T
```

获取Deque实例的头元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Deque-getFirst(): T--><!--Device-Deque-getFirst(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回T类型的头元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getFirst method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
// 创建Deque实例并插入元素
let deque = new Deque<number>();
deque.insertEnd(2);
deque.insertEnd(4);
deque.insertFront(5);
deque.insertFront(4);
// 获取Deque的头元素
let result = deque.getFirst();
console.info("result:", result);  // result: 4

```

<a id="getlast"></a>
## getLast

```TypeScript
getLast(): T
```

获取Deque实例的尾元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Deque-getLast(): T--><!--Device-Deque-getLast(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回T类型的尾元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getLast method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
// 创建Deque实例并插入元素
let deque = new Deque<number>();
deque.insertFront(2);
deque.insertFront(4);
deque.insertFront(5);
deque.insertFront(4);
// 获取Deque的尾元素
let result = deque.getLast();
console.info("result:", result);  // result: 2

```

<a id="has"></a>
## has

```TypeScript
has(element: T): boolean
```

判断此Deque中是否包含指定元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Deque-has(element: T): boolean--><!--Device-Deque-has(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果包含指定元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound. |

**示例：**

```TypeScript
// 创建Deque实例
let deque = new Deque<string>();
// 在头部插入元素
deque.insertFront("squirrel");
// 判断Deque中是否包含指定元素
let result = deque.has("squirrel");
console.info("result:", result);  // result: true

```

<a id="insertend"></a>
## insertEnd

```TypeScript
insertEnd(element: T): void
```

在deque尾部插入元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Deque-insertEnd(element: T): void--><!--Device-Deque-insertEnd(element: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 插入的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The insertEnd method cannot be bound. |

**示例：**

```TypeScript
class PersonInfo {
  name: string = "";
  age: string = "";
}

// 创建支持多种类型的Deque实例
let deque = new Deque<string | number | boolean | Array<number> | PersonInfo>();
// 在尾部插入字符串元素
deque.insertEnd("a");
// 在尾部插入数字元素
deque.insertEnd(1);
let numArray = [1, 2, 3];
deque.insertEnd(numArray);
let person: PersonInfo = {name : "Dylan", age : "13"};
deque.insertEnd(person);
deque.insertEnd(false);
console.info("result:", deque[0]);  // result: a

```

<a id="insertfront"></a>
## insertFront

```TypeScript
insertFront(element: T): void
```

在deque头部插入元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Deque-insertFront(element: T): void--><!--Device-Deque-insertFront(element: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 插入的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The insertFront method cannot be bound. |

**示例：**

```TypeScript
class PersonInfo {
  name: string = "";
  age: string = "";
}

// 创建支持多种类型的Deque实例
let deque = new Deque<string | number | boolean | Array<number> | PersonInfo>();
// 在头部插入字符串元素
deque.insertFront("a");
// 在头部插入数字元素
deque.insertFront(1);
let numArray = [1, 2, 3];
deque.insertFront(numArray);
let person: PersonInfo = {name : "Dylan", age : "13"};
deque.insertFront(person);
deque.insertFront(false);
console.info("result:", deque[0]);  // result: false

```

<a id="popfirst"></a>
## popFirst

```TypeScript
popFirst(): T
```

删除并返回双端队列的首元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Deque-popFirst(): T--><!--Device-Deque-popFirst(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回被删除的首元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The popFirst method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
// 创建Deque实例并插入元素
let deque = new Deque<number>();
deque.insertFront(2);
deque.insertFront(4);
deque.insertEnd(5);
deque.insertFront(2);
deque.insertFront(4);
// 删除并返回双端队列的首元素
let result = deque.popFirst();
console.info("result:", result);  // result: 4

```

<a id="poplast"></a>
## popLast

```TypeScript
popLast(): T
```

删除并返回双端队列的尾元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Deque-popLast(): T--><!--Device-Deque-popLast(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回被删除的尾元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The popLast method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
// 创建Deque实例并插入元素
let deque = new Deque<number>();
deque.insertFront(2);
deque.insertEnd(6);
deque.insertFront(5);
deque.insertFront(2);
deque.insertFront(4);
// 删除并返回双端队列的尾元素
let result = deque.popLast();
console.info("result:", result);  // result: 6

```

## length

```TypeScript
length: number
```

Deque的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Deque-length: number--><!--Device-Deque-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

