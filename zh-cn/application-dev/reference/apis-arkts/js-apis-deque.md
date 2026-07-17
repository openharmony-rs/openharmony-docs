# @ohos.util.Deque (线性容器Deque)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

Deque（double-ended queue）基于循环队列的数据结构实现，支持两端元素的插入和删除。Deque同时具备先进先出以及先进后出的特点，可根据操作端的不同同时作为队列和栈使用。当现有容量不足以容纳新插入的元素时，Deque会动态调整容量，每次扩容两倍，无需手动预设容量。

Deque和[Queue](js-apis-queue.md)相比，Deque允许在两端执行插入和删除操作，Queue只能在头部删除元素，尾部插入元素。

与[ArrayList](js-apis-arraylist.md)相比，它们都支持在两端插入和删除元素，但Deque不支持中间插入。Deque在头部插入删除元素的效率高于ArrayList，而ArrayList随机访问元素的效率高于Deque。

**推荐使用场景：** 需要在集合两端频繁增删元素时，推荐使用Deque。

文档中使用了泛型，涉及以下泛型标记符：
- T：Type，类型


> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 容器类使用静态语言实现，限制了内部存储方式和所支持的属性，不支持自定义属性和方法。


## 导入模块

```ts
import { Deque } from '@kit.ArkTS';
```

## Deque

### 属性

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 否 | Deque的元素个数。 |

### constructor

constructor()

Deque的构造函数，用于创建一个基于循环队列数据结构的空Deque实例。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200012 | The Deque's constructor cannot be directly invoked. |

**示例：**

ArkTS-Dyn示例：

```ts
// 创建Deque实例
let deque = new Deque<string | number | boolean | Object>();
```

ArkTS-Sta示例：

```ts
let deque: Deque<string | int | boolean | Object> = new Deque<string | int | boolean | Object>();
```

### insertFront

insertFront(element: T): void

在Deque头部插入元素。插入成功后Deque的元素个数增加1。Deque在头部插入元素的效率高于ArrayList。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| element | T | 是 | 在头部插入的元素，类型需与Deque实例化时指定的泛型类型T一致。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The insertFront method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
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

ArkTS-Sta示例：

```ts
class C1 {
  name: string = ""
  age: string = ""
}
let deque: Deque<string | int | boolean | Array<int> | C1> =
  new Deque<string | int | boolean | Array<int> | C1>();
deque.insertFront("a");
deque.insertFront(1);
let b: Array<int> = [1, 2, 3];
deque.insertFront(b);
let c: C1 = {name : "Dylan", age : "13"};
deque.insertFront(c);
deque.insertFront(false);
console.info("result:", deque[0]);  // result: false
```

### insertEnd

insertEnd(element: T): void

在Deque尾部插入元素。插入成功后Deque的元素个数增加1。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| element | T | 是 | 在尾部插入的元素。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The insertEnd method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
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

ArkTS-Sta示例：

```ts
class C1 {
  name: string = ""
  age: string = ""
}

let deque: Deque<string | int | boolean | Array<int> | C1> =
  new Deque<string | int | boolean | Array<int> | C1>();
deque.insertEnd("a");
deque.insertEnd(1);
let b: Array<int> = [1, 2, 3];
deque.insertEnd(b);
let c: C1 = {name : "Dylan", age : "13"};
deque.insertEnd(c);
deque.insertEnd(false);
console.info("result:", deque[0]);  // result: a
```

### has

has(element: T): boolean

判断此Deque中是否包含指定元素。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| element | T | 是 | 要在Deque中查找的指定元素，用于判断Deque是否包含该元素。类型需与Deque实例化时指定的泛型类型T一致。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 如果包含指定元素返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The has method cannot be bound. |

**示例：**

```ts
// 创建Deque实例
let deque = new Deque<string>();
// 在头部插入元素
deque.insertFront("squirrel");
// 判断Deque中是否包含指定元素
let result = deque.has("squirrel");
console.info("result:", result);  // result: true
```

### popFirst

popFirst(): T

删除并返回Deque的首元素。删除成功后Deque的元素个数减少1。Deque在头部删除元素的效率高于ArrayList。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回被删除的首元素。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200010 | Container is empty. <br> **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。|
| 10200011 | The popFirst method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
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

ArkTS-Sta示例：

```ts
let deque: Deque<int> = new Deque<int>();
deque.insertFront(2);
deque.insertFront(4);
deque.insertEnd(5);
deque.insertFront(2);
deque.insertFront(4);
let result = deque.popFirst();
console.info("result = ", result) // result =  4
```

### popLast

popLast(): T

删除并返回Deque的尾元素。删除成功后Deque的元素个数减少1。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回被删除的尾元素。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200010 | Container is empty. <br> **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。|
| 10200011 | The popLast method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
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

ArkTS-Sta示例：

```ts
let deque: Deque<int> = new Deque<int>();
deque.insertFront(2);
deque.insertEnd(6);
deque.insertFront(5);
deque.insertFront(2);
deque.insertFront(4);
let result = deque.popLast();
```

### forEach

forEach(callbackFn: (value: T, index?: number, deque?: Deque&lt;T&gt;) => void, thisArg?: Object): void

通过回调函数遍历Deque实例中的每个元素。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[forEach](#foreach23)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | function | 是 | 遍历每个元素时执行的回调函数，执行时的this值可通过thisArg参数指定。在回调函数执行过程中，不建议修改Deque（如插入或删除元素），否则可能导致遍历行为异常。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值。当需要改变回调函数中的this指向时传入此参数；不传入时默认值为当前实例对象。 |

callbackFn的参数说明：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 当前遍历到的元素。 |
| index | number | 否 | 当前遍历到的下标值，从0开始递增。 |
| deque | [Deque](#deque)&lt;T&gt; | 否 | 当前调用forEach方法的实例对象，即正在遍历的Deque实例。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**示例：**

```ts
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

### forEach<sup>23+</sup>

forEach(callbackFn: DequeForEachCb\<T\>): void

通过回调函数来遍历Deque实例对象上的元素以及元素对应的下标。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[forEach](#foreach)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | [DequeForEachCb\<T\>](#dequeforeachcbt23) | 是 | 回调函数。 |

**示例：**

```ts
import { DequeForEachCb } from '@kit.ArkTS'

let deque: Deque<int> = new Deque<int>();
deque.insertFront(2);
deque.insertEnd(4);
deque.insertFront(5);
deque.insertEnd(4);
let dequeCb: DequeForEachCb<int> = (value: int, index: int, deque: Deque<int>):void => {
  console.info("value:" + value, "index:" + index);
};

deque.forEach(dequeCb);

```

### getFirst

getFirst(): T

获取Deque实例的头元素，不删除该元素。调用后，Deque的内容和长度不变。如需删除并返回首元素，请使用popFirst。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回Deque实例的头元素。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200010 | Container is empty. <br> **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。|
| 10200011 | The getFirst method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
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

ArkTS-Sta示例：

```ts
let deque: Deque<int> = new Deque<int>();
deque.insertEnd(2);
deque.insertEnd(4);
deque.insertFront(5);
deque.insertFront(4);
let result = deque.getFirst();
```

### getLast

getLast(): T

获取Deque实例的尾元素，不删除该元素。调用后，Deque的内容和长度不变。如需删除并返回尾元素，请使用popLast。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回Deque实例的尾元素。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200010 | Container is empty. <br> **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。|
| 10200011 | The getLast method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
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

ArkTS-Sta示例：

```ts
let deque: Deque<int> = new Deque<int>();
deque.insertFront(2);
deque.insertFront(4);
deque.insertFront(5);
deque.insertFront(4);
let result = deque.getLast();
```

### \[index: int\]<sup>23+</sup>

\[index: int\]: T

获取指定索引值对应位置的元素。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | int | 是 | 元素的位置索引。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 容器中对应索引值为index的元素。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
let deque: Deque<int> = new Deque<int>();
deque.insertEnd(2);
deque.insertEnd(4);
deque.insertFront(5);
deque.insertFront(4);
let result1: int = deque[2];
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

返回一个迭代器，按插入顺序遍历Deque中的元素，迭代器每项为T类型的元素。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[$_iterator](#_iterator23)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;T&gt; | 返回一个迭代器，用于遍历Deque实例中的所有元素。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**示例：**
```ts
let deque = new Deque<number>();
deque.insertFront(2);
deque.insertFront(4);
deque.insertFront(5);
deque.insertFront(4);

// 使用方法一：
let nums: Array<number> = Array.from(deque);
for (let item of nums) {
  console.info("value:" + item);
}

// 使用方法二：
let iter = deque[Symbol.iterator]();
let temp:IteratorResult<number> = iter.next();
while(!temp.done) {
  console.info("value:" + temp.value);
  temp = iter.next();
}
```

### $_iterator<sup>23+</sup>

\$_iterator\(): IterableIterator&lt;T&gt;

返回一个迭代器，迭代器的每一项都是一个JavaScript对象，并返回该对象。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Symbol.iterator](#symboliterator)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;T&gt; | 返回一个迭代器。 |

**示例：**

```ts
let deque: Deque<int> = new Deque<int>();
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
let iter = deque.$_iterator();
let temp:IteratorResult<int> = iter.next();
while(!temp.done) {
  console.info("value:" + temp.value);
  temp = iter.next();
}
/*
输出结果：
value:4
value:5
value:4
value:2
 */
```

### DequeForEachCb\<T\><sup>23+</sup>

type DequeForEachCb\<T\> = (value: T, index: int, deque: Deque\<T\>) => void

Deque中forEach方法的回调函数。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 当前遍历到的元素。 |
| index | int | 是 | 当前遍历到的下标值。 |
| deque | [Deque&lt;T&gt;](#deque) | 是 | 当前调用[forEach](#foreach23)方法的实例对象。 |