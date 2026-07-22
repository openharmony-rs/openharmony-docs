# Vector

Vector是基于数组实现的线性数据结构。当Vector的内存用完时，会自动分配一块更大的连续内存区域，并将所有元素复制到新内存区域，回收当前内存区域。Vector可用于高效访问元素。Vector和[ArrayList](arkts-util-arraylist.md)都是基于数组实现，但Vector提供了更多的数组操作接口。两者都可以动态调整容量，Vector每次扩容为原来的两倍，ArrayList每次扩容为原来的1.5倍。**推荐使用场景：** 当数据量较大时，推荐使用Vector。文档中使用了泛型，涉及以下泛型标记符：

- T：Type，类
> **说明**  
>  
> - 此模块提供的接口从API version 9开始废弃。建议使用  
> [@ohos.util.ArrayList](arkts-util-arraylist.md)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** ArrayList

<!--Device-unnamed-declare class Vector<T>--><!--Device-unnamed-declare class Vector<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { Vector } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个ES6迭代器，迭代器的每一项都是一个JavaScript对象。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-[Symbol.iterator](): IterableIterator<T>--><!--Device-Vector-[Symbol.iterator](): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | @syscap SystemCapability.Utils.Lang |

**示例：**

```TypeScript
// 创建Vector实例并添加元素
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// 使用方法一：通过convertToArray将Vector转为数组后使用for-of遍历
let nums: Array<number> =  vector.convertToArray()
for (let item of nums) {
  console.info("value:" + item);
}

// 使用方法二：通过Symbol.iterator获取迭代器，使用next()逐个访问元素
let iter = vector[Symbol.iterator]();
let temp: IteratorResult<number> = iter.next().value;
while(temp != undefined) {
  console.info("value:" + temp);
  temp = iter.next().value;
}

```

## add

```TypeScript
add(element: T): boolean
```

在Vector尾部添加元素。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-add(element: T): boolean--><!--Device-Vector-add(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 添加的成员数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功添加元素返回true，否则返回false。 |

**示例：**

```TypeScript
// 定义自定义类PersonInfo
class PersonInfo {
  name: string = ""
  age: string = ""
}
// 创建Vector实例
let vector : Vector<string | number | PersonInfo | Array<number>> = new Vector();
// 添加字符串元素
let result = vector.add("a");
// 添加数字元素
let result1 = vector.add(1);
let numArray = [1, 2, 3];
// 添加数组元素
let result2 = vector.add(numArray);
let personInfo: PersonInfo = {name : "Jack", age : "13"};
// 添加自定义类实例
let result3 = vector.add(personInfo);

```

## clear

```TypeScript
clear(): void
```

清除Vector中的所有元素，并将length置为0。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-clear(): void--><!--Device-Vector-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.clear();

```

## clone

```TypeScript
clone(): Vector<T>
```

克隆一个实例，并返回克隆后的实例。修改克隆后的实例并不会影响原实例。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-clone(): Vector<T>--><!--Device-Vector-clone(): Vector<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Vector](arkts-arkts-util-vector-vector-c.md)&lt;T&gt; | 返回新的Vector实例。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.clone();

```

## constructor

```TypeScript
constructor()
```

Vector的构造函数。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-constructor()--><!--Device-Vector-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let vector : Vector<string | number | Array<number>> = new Vector();

```

## convertToArray

```TypeScript
convertToArray(): Array<T>
```

将Vector实例转换为数组。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-convertToArray(): Array<T>--><!--Device-Vector-convertToArray(): Array<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 返回数组。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.convertToArray();

```

## copyToArray

```TypeScript
copyToArray(array: Array<T>): void
```

将Vector中的元素复制到指定数组中，覆盖数组中相同下标的元素。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-copyToArray(array: Array<T>): void--><!--Device-Vector-copyToArray(array: Array<T>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| array | Array&lt;T&gt; | 是 | 接收Vector中复制元素的数组。 |

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, vector?: Vector<T>) => void, thisArg?: Object): void
```

通过回调函数来遍历Vector实例对象上的元素以及元素对应的下标。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-forEach(callbackFn: (value: T, index?: number, vector?: Vector<T>) => void, thisArg?: Object): void--><!--Device-Vector-forEach(callbackFn: (value: T, index?: number, vector?: Vector<T>) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, vector?: Vector&lt;T&gt;) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**示例：**

```TypeScript
// 创建Vector实例并添加元素
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// 遍历Vector中的每个元素，打印元素值和下标
vector.forEach((value : number, index?: number) : void => {
  console.info("value:" + value, "index:" + index);
});

```

## get

```TypeScript
get(index: number): T
```

获取指定下标对应的元素。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-get(index: number): T--><!--Device-Vector-get(index: number): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 查找的下标位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回指定下标对应的元素。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.get(2);

```

## getCapacity

```TypeScript
getCapacity(): number
```

获取Vector实例的容量大小。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-getCapacity(): number--><!--Device-Vector-getCapacity(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回Vector的容量。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getCapacity();

```

## getFirstElement

```TypeScript
getFirstElement(): T
```

获取Vector实例中的第一个元素。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-getFirstElement(): T--><!--Device-Vector-getFirstElement(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回Vector实例中的第一个元素。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getFirstElement();

```

## getIndexFrom

```TypeScript
getIndexFrom(element: T, index: number): number
```

从指定下标位置向前查找指定元素，并返回该元素的位置下标。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-getIndexFrom(element: T, index: number): number--><!--Device-Vector-getIndexFrom(element: T, index: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |
| index | number | 是 | 开始查找的下标位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定元素的下标值，查找失败返回-1。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getIndexFrom(4, 3);

```

## getIndexOf

```TypeScript
getIndexOf(element: T): number
```

获取指定元素第一次出现的下标值，如果未找到则返回-1。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-getIndexOf(element: T): number--><!--Device-Vector-getIndexOf(element: T): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定元素第一次出现时的下标值，查找失败返回-1。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(2);
vector.add(1);
vector.add(2);
vector.add(4);
let result = vector.getIndexOf(2);

```

## getLastElement

```TypeScript
getLastElement(): T
```

获取Vector实例中的最后一个元素。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-getLastElement(): T--><!--Device-Vector-getLastElement(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回Vector实例中的最后一个元素。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getLastElement();

```

## getLastIndexFrom

```TypeScript
getLastIndexFrom(element: T, index: number): number
```

从指定下标位置向后查找指定元素，并返回该元素的位置下标。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-getLastIndexFrom(element: T, index: number): number--><!--Device-Vector-getLastIndexFrom(element: T, index: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |
| index | number | 是 | 开始查找的下标位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定元素的下标值，查找失败返回-1。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getLastIndexFrom(4,3);

```

## getLastIndexOf

```TypeScript
getLastIndexOf(element: T): number
```

获取指定元素最后一次出现的下标值，如果未找到则返回-1。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-getLastIndexOf(element: T): number--><!--Device-Vector-getLastIndexOf(element: T): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定元素最后一次出现时的下标值，查找失败返回-1。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(2);
vector.add(1);
vector.add(2);
vector.add(4);
let result = vector.getLastIndexOf(2);

```

## has

```TypeScript
has(element: T): boolean
```

判断此Vector中是否包含指定元素。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-has(element: T): boolean--><!--Device-Vector-has(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 指定的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果包含指定元素返回true，否则返回false。 |

**示例：**

```TypeScript
// 创建Vector实例
let vector : Vector<string> = new Vector();
// 在添加元素前判断是否包含"squirrel"，预期返回false
let result = vector.has("squirrel");
// 添加元素"squirrel"
vector.add("squirrel");
// 在添加元素后判断是否包含"squirrel"，预期返回true
let result1 = vector.has("squirrel");

```

## increaseCapacityTo

```TypeScript
increaseCapacityTo(newCapacity: number): void
```

扩容Vector实例。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-increaseCapacityTo(newCapacity: number): void--><!--Device-Vector-increaseCapacityTo(newCapacity: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newCapacity | number | 是 | 新容量。 |

**示例：**

```TypeScript
// 创建Vector实例并添加元素
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// 传入容量2小于元素个数4，不会变更容量
vector.increaseCapacityTo(2);
// 传入容量12大于元素个数4，容量变更为12
vector.increaseCapacityTo(12);

```

## insert

```TypeScript
insert(element: T, index: number): void
```

在长度范围内插入元素，后续元素向后移动。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-insert(element: T, index: number): void--><!--Device-Vector-insert(element: T, index: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 插入的成员数据。 |
| index | number | 是 | 插入数据的位置下标。 |

**示例：**

```TypeScript
// 创建Vector实例
let vector : Vector<string | number | Object | Array<number>> = new Vector();
// 在索引0处插入字符串"A"
vector.insert("A", 0);
// 在索引1处插入数字0
vector.insert(0, 1);
// 在索引2处插入布尔值true
vector.insert(true, 2);

```

## isEmpty

```TypeScript
isEmpty(): boolean
```

判断Vector是否为空。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-isEmpty(): boolean--><!--Device-Vector-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 为空返回true，不为空返回false。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.isEmpty();

```

## remove

```TypeScript
remove(element: T): boolean
```

删除指定元素第一次出现的元素。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-remove(element: T): boolean--><!--Device-Vector-remove(element: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | T | 是 | 待删除的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 成功删除元素返回true，否则返回false。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.remove(2);

```

## removeByIndex

```TypeScript
removeByIndex(index: number): T
```

根据下标删除元素，返回被删除的元素，后续元素前移。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-removeByIndex(index: number): T--><!--Device-Vector-removeByIndex(index: number): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 待删除元素的下标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回删除的元素。如果Vector为空，返回undefined。如果下标越界，抛出异常。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(2);
vector.add(4);
let result = vector.removeByIndex(2);

```

## removeByRange

```TypeScript
removeByRange(fromIndex: number, toIndex: number): void
```

删除Vector实例中指定范围内的元素，包括起始位置但不包括结束位置的元素。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-removeByRange(fromIndex: number, toIndex: number): void--><!--Device-Vector-removeByRange(fromIndex: number, toIndex: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromIndex | number | 是 | 起始位置的下标。 |
| toIndex | number | 是 | 结束位置的下标。 |

**示例：**

```TypeScript
// 创建Vector实例并添加元素
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// 删除索引2到4之间的元素（包含起始索引2，不包含终止索引4）
vector.removeByRange(2,4);

```

## replaceAllElements

```TypeScript
replaceAllElements(callbackFn: (value: T, index?: number, vector?: Vector<T>) => T, thisArg?: Object): void
```

对Vector中的所有元素进行替换，并返回替换后的元素。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-replaceAllElements(callbackFn: (value: T, index?: number, vector?: Vector<T>) => T, thisArg?: Object): void--><!--Device-Vector-replaceAllElements(callbackFn: (value: T, index?: number, vector?: Vector<T>) => T, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, vector?: Vector&lt;T&gt;) =&gt; T | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

**示例：**

```TypeScript
// 创建Vector实例并添加元素
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// 对Vector中的每个元素执行替换操作，回调函数返回替换后的元素
vector.replaceAllElements((value : number) : number => {
  // 用户操作逻辑根据实际场景进行添加。
  return value;
});

```

## set

```TypeScript
set(index: number, element: T): T
```

替换Vector实例中指定下标位置的元素。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-set(index: number, element: T): T--><!--Device-Vector-set(index: number, element: T): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 替换元素的下标位置。 |
| element | T | 是 | 替换的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回替换后的新元素。 |

## setLength

```TypeScript
setLength(newSize: number): void
```

为Vector设置新的长度。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-setLength(newSize: number): void--><!--Device-Vector-setLength(newSize: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newSize | number | 是 | 设置的新长度。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.setLength(8);
vector.setLength(2);

```

## sort

```TypeScript
sort(comparator?: (firstValue: T, secondValue: T) => number): void
```

对Vector中的元素进行排序。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-sort(comparator?: (firstValue: T, secondValue: T) => number): void--><!--Device-Vector-sort(comparator?: (firstValue: T, secondValue: T) => number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| comparator | (firstValue: T, secondValue: T) =&gt; number | 否 | 排序的回调函数。默认值为当前实例对象。 |

**示例：**

```TypeScript
// 创建Vector实例并添加元素
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// 按升序排序
vector.sort((a: number, b: number) => a - b);
// 按降序排序
vector.sort((a: number, b: number) => b - a);
// 使用默认排序规则
vector.sort();

```

## subVector

```TypeScript
subVector(fromIndex: number, toIndex: number): Vector<T>
```

获取Vector实例中指定范围内的元素，包括起始位置但不包括结束位置的元素，作为一个新的Vector实例返回。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-subVector(fromIndex: number, toIndex: number): Vector<T>--><!--Device-Vector-subVector(fromIndex: number, toIndex: number): Vector<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromIndex | number | 是 | 起始位置的下标。 |
| toIndex | number | 是 | 结束位置的下标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Vector](arkts-arkts-util-vector-vector-c.md)&lt;T&gt; | 返回新的Vector实例。 |

**示例：**

```TypeScript
// 创建Vector实例并添加元素
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.add(6);
vector.add(8);
// 截取索引0到4之间的元素（包含起始索引0，不包含终止索引4，且toIndex大于fromIndex）
let result = vector.subVector(0,4);
// 截取索引2到4之间的元素（包含起始索引2，不包含终止索引4）
let result1 = vector.subVector(2,4);


```

## toString

```TypeScript
toString(): string
```

用逗号（,）将Vector实例中的元素拼接成字符串。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-toString(): string--><!--Device-Vector-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回对应字符串。 |

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.toString();

```

## trimToCurrentLength

```TypeScript
trimToCurrentLength(): void
```

把Vector实例的容量调整为当前的元素个数。

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-trimToCurrentLength(): void--><!--Device-Vector-trimToCurrentLength(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.trimToCurrentLength();

```

## length

```TypeScript
length: number
```

Vector的元素个数。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

<!--Device-Vector-length: number--><!--Device-Vector-length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

