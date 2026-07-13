# Stack

Stack基于数组的数据结构实现，特点是先进后出，只能在一端进行数据的插入和删除。

**起始版本：** 8

**系统能力：** SystemCapability.Utils.Lang

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

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
let iter = stack[Symbol.iterator]();
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

## constructor

```TypeScript
constructor()
```

Stack的构造函数。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Stack's constructor cannot be directly invoked. |

**示例：**

```TypeScript
let stack = new Stack<number | string | Object>();

```

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, stack?: Stack<T>) => void, thisArg?: Object): void
```

在遍历Stack实例对象中每一个元素的过程中，对每个元素执行回调函数。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, stack?: Stack&lt;T&gt;) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例：**

```TypeScript
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);
stack.forEach((value : number, index: number) :void => {
  console.info("value:" + value, "index:" + index);
});
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3

```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断栈是否为空。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 为空返回true，不为空返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The isEmpty method cannot be bound. |

**示例：**

```TypeScript
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);
let result = stack.isEmpty();
console.info("result:", result);  // result: false

```

## locate

```TypeScript
locate(element: T): number
```

查找指定元素首次出现的下标值，查找失败则返回-1。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 对应元素下标值，查找失败则返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The locate method cannot be bound. |

**示例：**

```TypeScript
let stack = new Stack<number>();
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

返回栈顶元素，栈为空时返回undefined。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回栈顶元素，栈为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The peek method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+**ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let stack = new Stack<number>();
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

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回栈顶元素，栈为空时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The pop method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+**ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let stack = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
stack.push(4);
let result = stack.pop(); 
console.info("result = " + result); // result = 4

```

## push

```TypeScript
push(item: T): T
```

在栈顶插入元素，并返回该元素。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | T | 是 | 添加进去的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回被添加进去的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The push method cannot be bound. |

**示例：**

```TypeScript
class C1 {
  name: string = ""
  age: string = ""
}
let stack = new Stack<number | string | C1>();
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

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

