# @ohos.util.Stack (线性容器Stack)

Stack基于数组的数据结构实现，特点是先进后出，只能在一端进行数据的插入和删除。

Stack和[Queue](js-apis-queue.md)相比，Queue基于循环队列实现，只能在一端删除另一端插入，而Stack都在一端操作。

**推荐使用场景：** 一般符合先进后出的场景可以使用Stack。

文档中使用了泛型，涉及以下泛型标记符：
- T：Type，类

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```ts
import { Stack } from '@kit.ArkTS';
```

## Stack

### 属性

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 20

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 否 | Stack的元素个数。 |


### constructor

constructor()

Stack的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 20

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200012 | The Stack's constructor cannot be directly invoked. |

**示例：**

ArkTS-Dyn示例：

```ts
let stack : Stack<number | string | Object> = new Stack<number | string | Object>();
```

ArkTS-Sta示例：

```ts
let stack : Stack<int | string | Object> = new Stack<int | string | Object>();
```


### push

push(item: T): T

在栈顶插入元素，并返回该元素。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| item | T | 是 | 添加进去的元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回被添加进去的元素。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The push method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```
class C1 {
  name: string = ""
  age: string = ""
}
let stack : Stack<number | string | C1> = new Stack<number | string | C1>();
let result = stack.push("a");
let result1 = stack.push(1);
let c : C1  = {name : "Dylan", age : "13"};
let result2 = stack.push(c);
```

ArkTS-Sta示例：

```
class C1 {
  name: string = ""
  age: string = ""
}
let stack : Stack<int | string | C1> = new Stack<int | string | C1>();
let result = stack.push("a");
let result1 = stack.push(1);
let c : C1  = {name : "Dylan", age : "13"};
let result2 = stack.push(c);
```

### pop

pop(): T

删除栈顶元素并返回，栈为空时返回undefined。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回栈顶元素，栈为空时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The pop method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let stack : Stack<number> = new Stack();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
stack.push(4);
let result = stack.pop(); 
console.info("result = " + result); // result = 4
```

ArkTS-Sta示例：

```ts
let stack : Stack<int> = new Stack<int>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
stack.push(4);
let result = stack.pop();
```

### peek

peek(): T

返回栈顶元素。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回栈顶元素。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The peek method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let stack : Stack<number> = new Stack();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
let result = stack.peek();
```

ArkTS-Sta示例：

```ts
let stack : Stack<int> = new Stack<int>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
let result = stack.peek();
```

### locate

ArkTS-Dyn: locate(element: T): number

ArkTS-Sta: locate(element: T): int

查找指定元素首次出现的下标值，查找失败则返回-1。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: number <br> ArkTS-Sta: int | 对应元素下标值，查找失败则返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The locate method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let stack : Stack<number> = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
let result = stack.locate(2);
```

ArkTS-Sta示例：

```ts
let stack : Stack<int> = new Stack<int>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(2);
let result = stack.locate(2);
```

### forEach

forEach(callbackFn: (value: T, index?: number, stack?: Stack&lt;T&gt;) => void,
thisArg?: Object): void

在遍历Stack实例对象中每一个元素的过程中，对每个元素执行回调函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | function | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

callbackFn的参数说明：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 当前遍历到的元素。 |
| index | number | 否 | 当前遍历到的下标值，默认值为0。 |
| stack | Stack&lt;T&gt; | 否 | 当前调用forEach方法的实例对象，默认值为当前实例对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 10200011 | The forEach method cannot be bound. |

**示例：**

```ts
let stack : Stack<number> = new Stack();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);
stack.forEach((value : number, index ?: number) :void => {
  console.info("value:" + value, "index:" + index);
});
/**
 * value:2 index:0
 * value:4 index:1
 * value:5 index:2
 * value:4 index:3
 */
```

### forEach<sup>20+</sup>

forEach(callbackfn: StackForEachCb\<T\>): void

通过回调函数来遍历Stack实例对象上的元素以及元素对应的下标。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | [StackForEachCb\<T\>](#stackforeachcbt20) | 是 | 回调函数。 |

**示例：**

```ts
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
```

### isEmpty

isEmpty(): boolean

判断栈是否为空。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 为空返回true，不为空返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let stack : Stack<number> = new Stack<number>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);
let result = stack.isEmpty();
```

ArkTS-Sta示例：

```ts
let stack : Stack<int> = new Stack<int>();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);
let result = stack.isEmpty();
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;T&gt; | 返回一个迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**示例：**
```ts
let stack : Stack<number> = new Stack();
stack.push(2);
stack.push(4);
stack.push(5);
stack.push(4);

// 使用方法一：
while(!stack.isEmpty()) {
  // 业务逻辑
  let item = stack.pop();
  console.info("value:" + item);
}

// 使用方法二：
let iter = stack[Symbol.iterator]();
let temp: IteratorResult<number> = iter.next().value;
while(temp != undefined) {
  console.info("value:" + temp);
  temp = iter.next().value;
}
```

### $_iterator<sup>20+</sup>

\$_iterator\(): IterableIterator&lt;T&gt;

返回一个迭代器，迭代器的每一项都是一个JavaScript对象，并返回该对象。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;T&gt; | 返回一个迭代器。 |

**示例：**

```ts
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

### StackForEachCb\<T\><sup>20+</sup>

type StackForEachCb\<T\> = (value: T, index: int, stack: Stack\<T\>) => void

Stack中forEach方法的回调函数。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 当前遍历到的元素。 |
| index | int | 是 | 当前遍历到的下标值。 |
| stack | [Stack&lt;T&gt;](#stack) | 是 | 当前调用[forEach](#foreach20)方法的实例对象。 |
