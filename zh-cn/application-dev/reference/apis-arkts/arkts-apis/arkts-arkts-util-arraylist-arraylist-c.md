# ArrayList

ArrayList是一种线性数据结构，底层基于数组实现。ArrayList会根据实际需要动态调整容量，每次扩容增加50%。

**起始版本：** 8

<!--Device-unnamed-declare class ArrayList<T>--><!--Device-unnamed-declare class ArrayList<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { ArrayList } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，每一项都是一个JavaScript对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-[Symbol.iterator](): IterableIterator<T>--><!--Device-ArrayList-[Symbol.iterator](): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<T> | @throws { BusinessError } 10200011 - The Symbol.iterator method cannot be bound. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);

// 使用方法一：
for (let value of arrayList) {
  console.info('value:', value);
}
// value: 2
// value: 4
// value: 5
// value: 4

// 使用方法二：
let iterator = arrayList[Symbol.iterator]();
let iteratorResult: IteratorResult<number> = iterator.next();
while (!iteratorResult.done) {
  console.info('value:', iteratorResult.value);
  iteratorResult = iterator.next();
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

在ArrayList尾部插入元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-add(element: T): boolean--><!--Device-ArrayList-add(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 待插入的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 插入成功返回true，失败返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound. |

**示例：**

```TypeScript
class Person {
  name: string = '';
  age: string = '';
}
let arrayList = new ArrayList<string | number | boolean | Array<number> | Person>();
// 添加字符串类型元素
arrayList.add('a');
// 添加数字类型元素
arrayList.add(1);
let numberArray = [1, 2, 3];
// 添加数组类型元素
arrayList.add(numberArray);
let person: Person = {name: 'Dylan', age: '13'};
// 添加自定义对象类型元素
let addPersonResult = arrayList.add(person);
// 添加布尔类型元素
let addBooleanResult = arrayList.add(false);
console.info('addPersonResult:', addPersonResult);  // addPersonResult: true
console.info('addBooleanResult:', addBooleanResult);  // addBooleanResult: true
console.info('length:', arrayList.length);  // length: 5

```

## clear

```TypeScript
clear(): void
```

清除ArrayList中的所有元素，并把length置为0。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-clear(): void--><!--Device-ArrayList-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.clear();

```

## clone

```TypeScript
clone(): ArrayList<T>
```

克隆一个与ArrayList相同的实例，并返回克隆后的实例。修改克隆后的实例并不会影响原实例。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-clone(): ArrayList<T>--><!--Device-ArrayList-clone(): ArrayList<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArrayList](arkts-arkts-util-arraylist-arraylist-c.md)<T> | 返回ArrayList对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clone method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: ArrayList<number> = arrayList.clone();
console.info('result = ', result.length); // result = 4

```

## constructor

```TypeScript
constructor()
```

ArrayList的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-constructor()--><!--Device-ArrayList-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The ArrayList's constructor cannot be directly invoked. |

**示例：**

```TypeScript
let arrayList = new ArrayList<string | number>();

```

## convertToArray

```TypeScript
convertToArray(): Array<T>
```

把当前ArrayList实例转换成数组，并返回转换后的数组。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-convertToArray(): Array<T>--><!--Device-ArrayList-convertToArray(): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](arkts-arkts-collections-array-c.md)<T> | 返回数组类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The convertToArray method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: Array<number> = arrayList.convertToArray();
console.info('result = ', result); // result =  2,4,5,4

```

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, arrlist?: ArrayList<T>) => void, thisArg?: Object): void
```

在遍历ArrayList实例对象的过程中，对每个元素执行回调函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-forEach(callbackFn: (value: T, index?: number, arrlist?: ArrayList<T>) => void, thisArg?: Object): void--><!--Device-ArrayList-forEach(callbackFn: (value: T, index?: number, arrlist?: ArrayList<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, arrlist?: ArrayList<T>) => void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
// 遍历ArrayList中的每个元素，打印元素值和下标
arrayList.forEach((value: number, index?: number) => {
  console.info('value:' + value, 'index:' + index);
});
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3

```

## getCapacity

```TypeScript
getCapacity(): number
```

获取当前实例的容量大小。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-getCapacity(): int--><!--Device-ArrayList-getCapacity(): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取当前实例的容量大小。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The getCapacity method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: number = arrayList.getCapacity();
console.info('result = ', result); // result = 10

```

## getIndexOf

```TypeScript
getIndexOf(element: T): number
```

返回指定元素第一次出现的下标，查找失败返回-1。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-getIndexOf(element: T): int--><!--Device-ArrayList-getIndexOf(element: T): int-End-->

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
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(2);
arrayList.add(1);
arrayList.add(2);
arrayList.add(4);
let result: number = arrayList.getIndexOf(2);
console.info("result = ", result); // result = 0

```

## getLastIndexOf

```TypeScript
getLastIndexOf(element: T): number
```

返回指定元素最后一次出现的下标，查找失败返回-1。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-getLastIndexOf(element: T): int--><!--Device-ArrayList-getLastIndexOf(element: T): int-End-->

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
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(2);
arrayList.add(1);
arrayList.add(2);
arrayList.add(4);
let result: number = arrayList.getLastIndexOf(2);
console.info('result = ', result); // result = 5

```

## has

```TypeScript
has(element: T): boolean
```

判断此ArrayList中是否包含该指定元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-has(element: T): boolean--><!--Device-ArrayList-has(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示包含指定元素，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<string>();
arrayList.add('squirrel');
let result: boolean = arrayList.has('squirrel');
console.info('result:', result);  // result: true

```

## increaseCapacityTo

```TypeScript
increaseCapacityTo(newCapacity: number): void
```

如果传入的新容量大于或等于ArrayList中的元素个数，将容量变更为新容量。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-increaseCapacityTo(newCapacity: int): void--><!--Device-ArrayList-increaseCapacityTo(newCapacity: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newCapacity | number | 是 | 新容量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The increaseCapacityTo method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.increaseCapacityTo(2);
arrayList.increaseCapacityTo(8);
console.info('result = ', arrayList.length); // result = 4

```

## insert

```TypeScript
insert(element: T, index: number): void
```

在长度范围内指定位置index插入元素element。如果index超出范围，则插入失败。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-insert(element: T, index: int): void--><!--Device-ArrayList-insert(element: T, index: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 被插入的元素。 |
| index | number | 是 | 被插入的位置索引。需要小于等于int32_max即2147483647。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of index is out of range. |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The insert method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number | string | boolean>();
// 在位置0插入字符串'A'
arrayList.insert('A', 0);
// 在位置1插入数字0
arrayList.insert(0, 1);
// 在位置2插入布尔值true
arrayList.insert(true, 2);
console.info('length:', arrayList.length);  // length: 3

```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断该ArrayList是否为空。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-isEmpty(): boolean--><!--Device-ArrayList-isEmpty(): boolean-End-->

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
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: boolean = arrayList.isEmpty();
console.info('result = ', result); // result =  false

```

## remove

```TypeScript
remove(element: T): boolean
```

删除查找到的第一个指定元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-remove(element: T): boolean--><!--Device-ArrayList-remove(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 删除成功返回true，失败返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: boolean = arrayList.remove(2);
console.info('result = ', result); // result =  true

```

## removeByIndex

```TypeScript
removeByIndex(index: number): T
```

根据元素的下标值查找元素，返回元素后将其删除。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-removeByIndex(index: int): T--><!--Device-ArrayList-removeByIndex(index: int): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定元素的下标值。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of "index" is out of range. |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeByIndex method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(2);
arrayList.add(4);
let result: number = arrayList.removeByIndex(2);
console.info('result = ', result); // result = 5

```

## removeByRange

```TypeScript
removeByRange(fromIndex: number, toIndex: number): void
```

删除指定范围内的元素，区间包含fromIndex，但不包含toIndex，即左闭右开区间[fromIndex, toIndex)。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-removeByRange(fromIndex: int, toIndex: int): void--><!--Device-ArrayList-removeByRange(fromIndex: int, toIndex: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromIndex | number | 是 | 起始下标。 |
| toIndex | number | 是 | 终止下标。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of fromIndex or toIndex is out of range. |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The removeByRange method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
// 删除下标2到4之间的元素（左闭右开区间，即删除下标为2和3的元素）
arrayList.removeByRange(2, 4);

```

## replaceAllElements

```TypeScript
replaceAllElements(callbackFn: (value: T, index?: number, arrlist?: ArrayList<T>) => T, thisArg?: Object): void
```

用户操作ArrayList中的元素，用操作后的元素替换原元素并返回操作后的元素。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-replaceAllElements(callbackFn: (value: T, index?: number, arrlist?: ArrayList<T>) => T, thisArg?: Object): void--><!--Device-ArrayList-replaceAllElements(callbackFn: (value: T, index?: number, arrlist?: ArrayList<T>) => T, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, arrlist?: ArrayList<T>) => T | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The replaceAllElements method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.replaceAllElements((value: number): number => {
  // 用户操作逻辑根据实际场景进行添加。
  return value;
});

```

## sort

```TypeScript
sort(comparator?: ArrayListComparatorFn<T>): void
```

根据指定比较器所定义的顺序，对ArrayList中的元素进行排序。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-sort(comparator?: ArrayListComparatorFn<T>): void--><!--Device-ArrayList-sort(comparator?: ArrayListComparatorFn<T>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| comparator | [ArrayListComparatorFn](arkts-arkts-arraylistcomparatorfn-t.md)<T> | 否 | 回调函数，默认为升序排序的回调函数。<br> API version 23开始发生兼容性变更，在API version 22及之前的版本其类型为：`(firstValue: T, secondValue: T) =&gt; number`。<br>**起始版本：** 23 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The sort method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
// 升序排序
arrayList.sort((firstValue: number, secondValue: number) => firstValue - secondValue);
// 降序排序
arrayList.sort((firstValue: number, secondValue: number) => secondValue - firstValue);
// 默认排序（升序）
arrayList.sort();

```

## subArrayList

```TypeScript
subArrayList(fromIndex: number, toIndex: number): ArrayList<T>
```

根据下标截取ArrayList中的一段元素，并返回这一段ArrayList实例，区间包含fromIndex，但不包含toIndex，即左闭右开区间[fromIndex, toIndex)。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-subArrayList(fromIndex: int, toIndex: int): ArrayList<T>--><!--Device-ArrayList-subArrayList(fromIndex: int, toIndex: int): ArrayList<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromIndex | number | 是 | 起始下标。 |
| toIndex | number | 是 | 终止下标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArrayList](arkts-arkts-util-arraylist-arraylist-c.md)<T> | 返回ArrayList对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of fromIndex or toIndex is out of range. |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The subArrayList method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: ArrayList<number> = arrayList.subArrayList(2, 4);
console.info('result = ', result.length); // result = 2

```

## trimToCurrentLength

```TypeScript
trimToCurrentLength(): void
```

释放ArrayList中预留的空间，把容量调整为当前的元素个数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-trimToCurrentLength(): void--><!--Device-ArrayList-trimToCurrentLength(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The trimToCurrentLength method cannot be bound. |

**示例：**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.trimToCurrentLength();
console.info('result = ', arrayList.length); // result = 4

```

## index

```TypeScript
[index: number]: T
```

获取指定索引值对应位置的元素。

**类型：** T

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-[index: int]: T--><!--Device-ArrayList-[index: int]: T-End-->

**系统能力：** SystemCapability.Utils.Lang

## length

```TypeScript
length: number
```

ArrayList的元素个数。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ArrayList-length: number--><!--Device-ArrayList-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

