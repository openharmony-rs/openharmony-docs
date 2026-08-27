# List

List底层通过单向链表实现，每个节点有一个指向后一个元素的引用。查询元素必须从头遍历，因此查询效率低，但插入和删除效率高。List允许元素为null。

**起始版本：** 8

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，用于遍历List中的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator & lt;T & gt; | 返回一个迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);

// 使用方法一：
for (let item of list) {
  console.info("value: " + item);
}
// value: 2
// value: 4
// value: 5
// value: 4

// 使用方法二：
let iter = list[Symbol.iterator]();
let temp: IteratorResult<number> = iter.next();
while(!temp.done) {
  console.info("value: " + temp.value);
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

在List尾部插入元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 待添加的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 插入成功返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound. |

**示例**

```TypeScript
// 创建支持多种类型元素的List实例
let list = new List<string | number | boolean | object>();
let result1 = list.add("a");
console.info("result = ", result1); // result =  true
let result2 = list.add(1);
console.info("result = ", result2); // result =  true
let numArray = [1, 2, 3];
let result3 = list.add(numArray);
console.info("result = ", result3); // result =  true
class PersonInfo {
  name: string = "";
  age: string = "";
}
let personInfo: PersonInfo = {name : "Dylan", age : "13"};
let result4 = list.add(personInfo);
console.info("result = ", result4); // result =  true
let result5 = list.add(false);
console.info("result = ", result5); // result =  true
```

## clear

```TypeScript
clear(): void
```

清除List中的所有元素，并将length置为0。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);
list.clear();
let result = list.isEmpty();
console.info("result:", result);  // result: true
```

## constructor

```TypeScript
constructor()
```

List的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The List's constructor cannot be directly invoked. |

**示例**

```TypeScript
let list = new List<string | number | boolean | object>();
```

## convertToArray

```TypeScript
convertToArray(): Array<T>
```

把当前List实例转换成数组并返回。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;T & gt; | 返回转换后的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The convertToArray method cannot be bound. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.convertToArray();
console.info("result:", result);  // result: 2,4,5,4
```

## equal

```TypeScript
equal(obj: Object): boolean
```

比较指定对象与此List是否相等。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object | 是 | 用来比较的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果对象与此列表相同返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The equal method cannot be bound. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
let obj = new List<number>();
obj.add(2);
obj.add(4);
obj.add(5);
let result = list.equal(obj);
console.info("result:", result);  // result: true
```

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, List?: List<T>) => void, thisArg?: Object): void
```

在遍历List实例对象中每一个元素的过程中，对每个元素执行回调函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, List?: List & lt;T & gt;) = & gt; void | 是 | 回调函数。 callbackFn（必填）接受最多三个参数的函数。 value 当前遍历到的元素。 index 当前遍历到的下标值，默认值为0。 List 当前调用forEach方法的实例对象，默认值为当前实例对象。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);
// 遍历List中的每个元素并打印值和下标
list.forEach((value: number, index: number) => {
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

根据下标获取List中的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 要查找的下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 根据下标查找到的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The get method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(2);
list.add(1);
list.add(2);
list.add(4);
let result = list.get(2);
console.info("result:", result);  // result: 5
```

## getFirst

```TypeScript
getFirst(): T
```

获取List实例中的第一个元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回实例的第一个元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getFirst method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.getFirst();
console.info("result:", result);  // result: 2
```

## getIndexOf

```TypeScript
getIndexOf(element: T): number
```

查找指定元素第一次出现的下标，查找失败返回-1。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回第一次找到指定元素的下标，没有找到返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getIndexOf method cannot be bound. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(2);
list.add(1);
list.add(2);
list.add(4);
let result = list.getIndexOf(2);
console.info("result:", result); // result: 0
```

## getLast

```TypeScript
getLast(): T
```

获取List实例中的最后一个元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回实例的最后一个元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getLast method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-容器为空) | Container is empty.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.getLast();
console.info("result:", result);  // result: 4
```

## getLastIndexOf

```TypeScript
getLastIndexOf(element: T): number
```

查找指定元素最后一次出现的下标值，查找失败返回-1。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定元素最后一次出现的下标值，没有找到返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getLastIndexOf method cannot be bound. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(2);
list.add(1);
list.add(2);
list.add(4);
let result = list.getLastIndexOf(2);
console.info("result:", result); // result: 5
```

## getSubList

```TypeScript
getSubList(fromIndex: number, toIndex: number): List<T>
```

根据下标截取List中的一段元素，并返回这一段List实例，包括起始值但不包括终止值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromIndex | number | 是 | 起始下标。 |
| toIndex | number | 是 | 终止下标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [List](arkts-arkts-util-list-list-c.md)&lt;T&gt; | 返回List对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getSubList method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of fromIndex or toIndex is out of range. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(6);
list.add(8);
let result = list.getSubList(1, 3);
console.info("result:", result.convertToArray());  // result: 4,6
```

## has

```TypeScript
has(element: T): boolean
```

判断List中是否包含指定元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 包含指定元素返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound. |

**示例**

```TypeScript
let list = new List<string>();
list.add("squirrel");
let result = list.has("squirrel");
console.info("result:", result);  // result: true
```

## insert

```TypeScript
insert(element: T, index: number): void
```

在长度范围内任意位置插入指定元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 待插入元素。 |
| index | number | 是 | 插入的位置索引，可插入位置区间为[0, List.length]，需要小于等于int32_max即2147483647。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The insert method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例**

```TypeScript
let list = new List<string | number | boolean>();
list.insert("A", 0);
list.insert(0, 1);
list.insert(true, 2);
console.info("result:", list.get(1));  // result: 0
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断List是否为空。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.isEmpty();
console.info("result:", result);  // result: false
```

## remove

```TypeScript
remove(element: T): boolean
```

删除查找到的第一个指定的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 删除成功返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.remove(2);
console.info("result:", result);  // result: true
```

## removeByIndex

```TypeScript
removeByIndex(index: number): T
```

根据元素的下标值查找元素，并将其删除。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定元素的下标值，取值范围[0, List.length-1]，需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回被删除的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeByIndex method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(2);
list.add(4);
let result = list.removeByIndex(2);
console.info("result:", result);  // result: 5
```

## replaceAllElements

```TypeScript
replaceAllElements(callbackFn: (value: T, index?: number, list?: List<T>) => T, thisArg?: Object): void
```

遍历List中的元素，并用回调函数返回的新值替换原List中的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, list?: List & lt;T & gt;) = & gt; T | 是 | 回调函数。 callbackFn（必填）接受最多三个参数的函数。 value 当前遍历到的元素。 index 当前遍历到的下标值，默认值为0。 list 当前调用replaceAllElements方法的实例对象，默认值为当前实例对象。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The replaceAllElements method cannot be bound. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);
list.replaceAllElements((value: number) => {
  // 用户操作逻辑根据实际场景进行添加
  if (value === 5) {
    return value * 2;
  }
  return value;
});

console.info("result:", list.get(2));  // result: 10
```

## set

```TypeScript
set(index: number, element: T): T
```

替换List指定位置的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 查找的下标值。取值范围[0, List.length-1]，需要小于等于int32_max即2147483647。 |
| element | T | 是 | 用来替换的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回替换后的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The set method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |

**示例**

```TypeScript
let list = new List<number | string>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.set(2, "b");
console.info("result:", JSON.stringify(list));  // result: {"0":2,"1":4,"2":"b","3":4}
```

## sort

```TypeScript
sort(comparator: ListComparatorFn<T>): void
```

对List中的元素进行排序。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| comparator | [ListComparatorFn](arkts-arkts-listcomparatorfn-t.md)&lt;T&gt; | 是 | 回调函数。API version 23开始发生兼容性变更，在API version 22及之前的版本其类型为：`(firstValue: T, secondValue: T) =&gt; number`。<br>**起始版本：** 23 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The sort method cannot be bound. |

**示例**

```TypeScript
let list = new List<number>();
list.add(2);
list.add(1);
list.add(3);
list.add(4);
list.sort((a: number, b: number) => a - b);  // 结果为升序排列
console.info("result:", list.convertToArray());  // result: 1,2,3,4

list.sort((a: number, b: number) => b - a);  // 结果为降序排列
console.info("result:", list.convertToArray());  // result: 4,3,2,1
```

## length

```TypeScript
length: number
```

List的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
