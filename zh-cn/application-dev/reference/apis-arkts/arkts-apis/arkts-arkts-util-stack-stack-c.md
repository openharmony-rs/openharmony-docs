# Stack

Stack基于数组的数据结构实现，特点是先进后出，只能在一端进行数据的插入和删除。

**起始版本：** 23

<!--Device-unnamed-declare class Stack--><!--Device-unnamed-declare class Stack-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { Stack } from '@kit.ArkTS';
import { StackForEachCb } from '@kit.ArkTS';
```

## $_iterator

```TypeScript
$_iterator(): IterableIterator<T>
```

返回一个迭代器，每一项都是一个ArkTS对象。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Stack-$_iterator(): IterableIterator<T>--><!--Device-Stack-$_iterator(): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; |  |

**示例**

```TypeScript
let stack : Stack<int> = new Stack<int>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);

let iter = stack.$_iterator();
let temp = iter.next().value;
while(temp != undefined) {
  console.info("value:" + temp);
  temp = iter.next().value;
}
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项为T类型的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Stack-[Symbol.iterator](): IterableIterator<T>--><!--Device-Stack-[Symbol.iterator](): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 返回一个迭代器，用于按栈的存储顺序依次遍历Stack中的所有元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例**

```TypeScript
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);

// 使用方法一：
for (let value of stack) {
  console.info("value:", value);
}
// value: 2
// value: 4
// value: 5
// value: 4

// 使用方法二：
// 创建迭代器
let iter = stack[Symbol.iterator]();
// 获取第一个迭代结果
let currentValue: IteratorResult<number> = iter.next().value;
// 循环遍历迭代器中的元素
while (currentValue != undefined) {
  console.info("value: " + currentValue);
  currentValue = iter.next().value;
}
// value: 2
// value: 4
// value: 5
// value: 4
```

## constructor

```TypeScript
constructor()
```

Stack的构造函数。调用后创建一个空的Stack实例对象，初始length为0。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Stack-constructor()--><!--Device-Stack-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Stack's constructor cannot be directly invoked. |

**示例**

ArkTS-Dyn示例：

```TypeScript
// 创建Stack实例
let stack = new Stack<number | string | Object>();
console.info("length:", stack.length);  // length: 0
```

ArkTS-Sta示例：

```TypeScript
let stack : Stack<int | string | Object> = new Stack<int | string | Object>();
```

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, stack?: Stack<T>) => void, thisArg?: Object): void
```

按照从栈底到栈顶的顺序遍历Stack实例对象中每一个元素，对每个元素执行回调函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Stack-forEach(callbackFn: (value: T, index?: number, stack?: Stack<T>) => void, thisArg?: Object): void--><!--Device-Stack-forEach(callbackFn: (value: T, index?: number, stack?: Stack<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, stack?: Stack&lt;T&gt;) =&gt; void | 是 | 遍历每个元素时执行的回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值。不传入时默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例**

```TypeScript
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);
// 遍历stack中每个元素并执行回调函数
stack.forEach((value: number, index: number): void => {
  console.info("value:" + value, "index:" + index);
});
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3
```

## forEach

```TypeScript
forEach(callbackfn: StackForEachCb<T>): void
```

按照从栈底到栈顶的顺序遍历Stack实例对象中每一个元素，对每个元素执行回调函数。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Stack-forEach(callbackfn: StackForEachCb<T>): void--><!--Device-Stack-forEach(callbackfn: StackForEachCb<T>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackfn | [StackForEachCb](arkts-arkts-stackforeachcb-t.md)&lt;T&gt; | 是 |  |

**示例**

```TypeScript
import { StackForEachCb } from '@kit.ArkTS';

let stack : Stack<int> = new Stack<int>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);
let stackCb: StackForEachCb<int> = (value: int, index: int, stack: Stack<int>) :void => {
  console.info("value:" + value, "index:" + index);
};

stack.forEach(stackCb);
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断栈是否为空。为空返回true，不为空返回false。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Stack-isEmpty(): boolean--><!--Device-Stack-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 为空返回true，不为空返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The isEmpty method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);
// 判断栈是否为空
let result = stack.isEmpty();
console.info("result:", result);  // result: false
```

ArkTS-Sta示例：

```TypeScript
let stack = new Stack<int>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);
let result = stack.isEmpty();
console.info("result:", result);  // result: false
```

## locate

```TypeScript
locate(element: T): int
```

查找指定元素首次出现的下标值，查找失败则返回-1。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Stack-locate(element: T): int--><!--Device-Stack-locate(element: T): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 待查找的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 对应元素下标值，查找失败则返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The locate method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
// 查找元素5首次出现的下标
let result = stack.locate(5);
console.info("result:", result);  // result: 2
```

ArkTS-Sta示例：

```TypeScript
let stack = new Stack<int>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
let result = stack.locate(5);
console.info("result:", result);  // result: 2
```

## peek

```TypeScript
peek(): T
```

返回栈顶元素，栈为空时返回undefined。调用后栈的内容不变。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Stack-peek(): T--><!--Device-Stack-peek(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回栈顶元素，栈为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The peek method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+ |

**示例**

ArkTS-Dyn示例：

```TypeScript
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
// 查看栈顶元素，但不删除
let result = stack.peek();
console.info("result:", result);  // result: 2
```

ArkTS-Sta示例：

```TypeScript
let stack = new Stack<int>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
let result = stack.peek();
console.info("result:", result);  // result: 2
```

## pop

```TypeScript
pop(): T
```

删除栈顶元素并返回，栈为空时返回undefined。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Stack-pop(): T--><!--Device-Stack-pop(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回栈顶元素，栈为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The pop method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+ |

**示例**

ArkTS-Dyn示例：

```TypeScript
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
stack.push(4);
// 删除栈顶元素并返回该元素
let result = stack.pop();
```

ArkTS-Sta示例：

```TypeScript
let stack = new Stack<int>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
stack.push(4);
// 删除栈顶元素并返回该元素
let result = stack.pop(); 
console.info("result = " + result); // result = 4
```

## push

```TypeScript
push(item: T): T
```

在栈顶插入元素，并返回该元素。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Stack-push(item: T): T--><!--Device-Stack-push(item: T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | T | 是 | 需要在栈顶插入的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回插入栈顶的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The push method cannot be bound. |

**示例**

ArkTS-Dyn示例：

```TypeScript
class PersonInfo {
  name: string = "";
  age: string = "";
  constructor(name: string, age: string) {
    this.name = name;
    this.age = age;
  }
}
// 创建支持多种类型的Stack实例
let stack = new Stack<number | string | PersonInfo>();
// 向栈中push字符串元素
console.info("push:", stack.push("a"));  // push: a
// 向栈中push数字元素
console.info("push:", stack.push(1));  //  push: 1
// 创建类实例并push到栈中
let person1: PersonInfo = new PersonInfo("Dylan", "13");
let result = stack.push(person1);
console.info("result instanceof PersonInfo:", result instanceof PersonInfo);  // result instanceof PersonInfo: true
console.info("length:", stack.length);  // length: 3
```

ArkTS-Sta示例：

```TypeScript
class C1 {
  name: string = ""
  age: string = ""
}
let stack = new Stack<int | string | C1>();
let result = stack.push("a");
let result1 = stack.push(1);
let c : C1  = {name : "Dylan", age : "13"};
let result2 = stack.push(c);
console.info("length:", stack.length);  // length: 3
```

## length

```TypeScript
length: number
```

Stack的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Stack-length: number--><!--Device-Stack-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

