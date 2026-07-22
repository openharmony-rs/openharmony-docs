# LinkedList

LinkedList底层基于双向链表实现。双向链表的每个节点都有一个指向上一元素的引用和指向下一元素的引用。查询元素时，从头或尾开始遍历。

**起始版本：** 8

<!--Device-unnamed-declare class LinkedList<T>--><!--Device-unnamed-declare class LinkedList<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { LinkedList } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-[Symbol.iterator](): IterableIterator<T>--><!--Device-LinkedList-[Symbol.iterator](): IterableIterator<T>-End-->

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
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(4);

// 使用方法一：
for (let item of linkedList) {
  console.info("value:", item);
}
// value: 2
// value: 4
// value: 5
// value: 4

// 使用方法二：
let iter = linkedList[Symbol.iterator]();
let temp: IteratorResult<number> = iter.next();
while(!temp.done) {
  console.info("value:", temp.value);
  temp = iter.next();
}
// value: 2
// value: 4
// value: 5
// value: 4

```

## add

```TypeScript
add(element: T): boolean
```

在LinkedList尾部添加元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-add(element: T): boolean--><!--Device-LinkedList-add(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 添加的成员数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功添加元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound. |

**示例：**

```TypeScript
let linkedList = new LinkedList<string | number | boolean | object>();
let result = linkedList.add("a");
console.info("result = ", result); // result =  true
let result1 = linkedList.add(1);
console.info("result = ", result1); // result =  true
let numArray = [1, 2, 3];
let result2 = linkedList.add(numArray);
console.info("result = ", result2); // result =  true
class PersonInfo {
  name: string = '';
  age: string = '';
}
let personInfo: PersonInfo = {name : "Dylan", age : "13"};
let result3 = linkedList.add(personInfo);
console.info("result = ", result3); // result =  true
let result4 = linkedList.add(false);
console.info("result = ", result4); // result =  true

```

## addFirst

```TypeScript
addFirst(element: T): void
```

在LinkedList头部添加元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-addFirst(element: T): void--><!--Device-LinkedList-addFirst(element: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 添加的成员数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The addFirst method cannot be bound. |

**示例：**

```TypeScript
let linkedList = new LinkedList<string | number | boolean | object>();
linkedList.addFirst("a");
linkedList.addFirst(1);
let numArray = [1, 2, 3];
linkedList.addFirst(numArray);
class PersonInfo {
  name: string = '';
  age: string = '';
}
let personInfo: PersonInfo = {name : "Dylan", age : "13"};
linkedList.addFirst(personInfo);
linkedList.addFirst(false);
let result = linkedList.get(2);
console.info("result:", result);  // result: 1,2,3

```

## clear

```TypeScript
clear(): void
```

清除LinkedList中的所有元素，并将length置为0。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-clear(): void--><!--Device-LinkedList-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(4);
linkedList.clear();
let result = linkedList.has(2);
console.info("result:", result);  // result: false

```

## clone

```TypeScript
clone(): LinkedList<T>
```

克隆一个与LinkedList相同的实例，并返回克隆后的实例。修改克隆后的实例并不会影响原实例。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-clone(): LinkedList<T>--><!--Device-LinkedList-clone(): LinkedList<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LinkedList](arkts-arkts-util-linkedlist-linkedlist-c.md)&lt;T&gt; | 返回新的LinkedList实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clone method cannot be bound. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(4);
let result = linkedList.clone();
console.info("result:", result.has(4));  // result: true

```

## constructor

```TypeScript
constructor()
```

LinkedList的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-constructor()--><!--Device-LinkedList-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The LinkedList's constructor cannot be directly invoked. |

**示例：**

```TypeScript
let linkedList = new LinkedList<string | number | boolean | object>();

```

## convertToArray

```TypeScript
convertToArray(): Array<T>
```

将LinkedList实例转换为数组。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-convertToArray(): Array<T>--><!--Device-LinkedList-convertToArray(): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 返回数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The convertToArray method cannot be bound. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(4);
let result = linkedList.convertToArray();
console.info("result:", result);  // result: 2,4,5,4

```

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, LinkedList?: LinkedList<T>) => void, thisArg?: Object): void
```

通过回调函数来遍历LinkedList实例对象上的元素以及元素对应的下标。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-forEach(callbackFn: (value: T, index?: number, LinkedList?: LinkedList<T>) => void, thisArg?: Object): void--><!--Device-LinkedList-forEach(callbackFn: (value: T, index?: number, LinkedList?: LinkedList<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, LinkedList?: LinkedList&lt;T&gt;) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(4);
linkedList.forEach((value: number, index: number) => {
  console.info("value:" + value, "index:" + index);
});
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3

```

## get

```TypeScript
get(index: number): T
```

获取指定下标位置的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-get(index: int): T--><!--Device-LinkedList-get(index: int): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 查找的下标位置。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回指定下标位置的元素，如果元素不存在返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The get method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(2);
linkedList.add(1);
linkedList.add(2);
linkedList.add(4);
let result = linkedList.get(2);
console.info("result:", result);  // result: 5

```

## getFirst

```TypeScript
getFirst(): T
```

获取LinkedList实例中的第一个元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-getFirst(): T--><!--Device-LinkedList-getFirst(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回获取的元素，如果为空返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getFirst method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(4);
let result = linkedList.getFirst();
console.info("result:", result);  // result: 2

```

## getIndexOf

```TypeScript
getIndexOf(element: T): number
```

获取指定元素第一次出现的下标值，如果未找到则返回-1。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-getIndexOf(element: T): int--><!--Device-LinkedList-getIndexOf(element: T): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定元素第一次出现时的下标值，查找失败返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getIndexOf method cannot be bound. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(2);
linkedList.add(1);
linkedList.add(2);
linkedList.add(4);
let result = linkedList.getIndexOf(2);
console.info("result:", result);  // result: 0

```

## getLast

```TypeScript
getLast(): T
```

获取LinkedList实例中的最后一个元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-getLast(): T--><!--Device-LinkedList-getLast(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回获取的元素，如果为空返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getLast method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(4);
let result = linkedList.getLast();
console.info("result:", result);  // result: 4

```

## getLastIndexOf

```TypeScript
getLastIndexOf(element: T): number
```

获取指定元素最后一次出现的下标值，如果未找到则返回-1。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-getLastIndexOf(element: T): int--><!--Device-LinkedList-getLastIndexOf(element: T): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定元素最后一次出现时的下标值，查找失败返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getLastIndexOf method cannot be bound. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(2);
linkedList.add(1);
linkedList.add(2);
linkedList.add(4);
let result = linkedList.getLastIndexOf(2);
console.info("result:", result);  // result: 5

```

## has

```TypeScript
has(element: T): boolean
```

判断容器中是否包含指定元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-has(element: T): boolean--><!--Device-LinkedList-has(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound. |

**示例：**

```TypeScript
let linkedList = new LinkedList<string>();
linkedList.add("squirrel");
let result = linkedList.has("squirrel");
console.info("result:", result);  // result: true

```

## insert

```TypeScript
insert(index: number, element: T): void
```

在LinkedList的指定位置插入元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-insert(index: int, element: T): void--><!--Device-LinkedList-insert(index: int, element: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 插入数据的位置下标。需要小于等于int32_max即2147483647。 |
| element | T | 是 | 插入的成员数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The insert method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例：**

```TypeScript
let linkedList = new LinkedList<string | number | boolean | object>();
linkedList.insert(0, "A");
linkedList.insert(1, 0);
linkedList.insert(2, true);
let result = linkedList.get(1);
console.info("result:", result);  // result: 0

```

## remove

```TypeScript
remove(element: T): boolean
```

删除指定元素第一次出现的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-remove(element: T): boolean--><!--Device-LinkedList-remove(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 待删除的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功删除元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(4);
let result = linkedList.remove(2);
console.info("result:", result);  // result: true

```

## removeByIndex

```TypeScript
removeByIndex(index: number): T
```

根据下标删除元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-removeByIndex(index: number): T--><!--Device-LinkedList-removeByIndex(index: number): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 待删除元素的下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除的元素，如果元素不存在返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeByIndex method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(2);
linkedList.add(4);
let result = linkedList.removeByIndex(2);
console.info("result:", result);  // result: 5

```

## removeFirst

```TypeScript
removeFirst(): T
```

删除LinkedList实例中的第一个元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-removeFirst(): T--><!--Device-LinkedList-removeFirst(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeFirst method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(2);
linkedList.add(4);
let result = linkedList.removeFirst();
console.info("result:", result);  // result: 2

```

## removeFirstFound

```TypeScript
removeFirstFound(element: T): boolean
```

删除指定元素第一次出现的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-removeFirstFound(element: T): boolean--><!--Device-LinkedList-removeFirstFound(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 待删除的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功删除元素返回true；删除失败或元素不存在返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeFirstFound method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty. |
| [10200017](../errorcode-utils.md#10200017-删除不存在的元素错误) | The element does not exist in this container. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(4);
let result = linkedList.removeFirstFound(4);
console.info("result:", result);  // result: true

```

## removeLast

```TypeScript
removeLast(): T
```

删除LinkedList实例中的最后一个元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-removeLast(): T--><!--Device-LinkedList-removeLast(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeLast method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(2);
linkedList.add(4);
let result = linkedList.removeLast();
console.info("result:", result);  // result: 4

```

## removeLastFound

```TypeScript
removeLastFound(element: T): boolean
```

删除指定元素最后一次出现的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-removeLastFound(element: T): boolean--><!--Device-LinkedList-removeLastFound(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 待删除的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功删除元素返回true；删除失败或元素不存在返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeLastFound method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty. |
| [10200017](../errorcode-utils.md#10200017-删除不存在的元素错误) | The element does not exist in this container. |

**示例：**

```TypeScript
let linkedList = new LinkedList<number>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(4);
let result = linkedList.removeLastFound(4);
console.info("result:", result);  // result: true

```

## set

```TypeScript
set(index: number, element: T): T
```

替换LinkedList实例中指定下标位置的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-set(index: int, element: T): T--><!--Device-LinkedList-set(index: int, element: T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 替换元素的下标位置。需要小于等于int32_max即2147483647。 |
| element | T | 是 | 替换的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回替换后的新元素，如果为空返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The set method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

```TypeScript
let linkedList = new LinkedList<number | string>();
linkedList.add(2);
linkedList.add(4);
linkedList.add(5);
linkedList.add(4);
let result = linkedList.set(2, "b");
console.info("result:", result);  // result: b

```

## length

```TypeScript
length: number
```

LinkedList的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinkedList-length: number--><!--Device-LinkedList-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

