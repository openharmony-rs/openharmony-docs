# Uint32Array

一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md)实现。

> **说明**  
>  
> - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  
> **装饰器**：\@Sendable

**起始版本：** 12

**装饰器类型：** @Sendable

<!--Device-collections-class Uint32Array--><!--Device-collections-class Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { collections } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<number>
```

返回一个迭代器，迭代器的每一项都是一个数字。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-[Symbol.iterator](): IterableIterator<number>--><!--Device-Uint32Array-[Symbol.iterator](): IterableIterator<number>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<number> | 产出数字的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

## at

```TypeScript
at(index: number): number | undefined
```

返回指定下标的元素，如果不存在，则返回**undefined**。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-at(index: number): number | undefined--><!--Device-Uint32Array-at(index: number): number | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 所需代码单元的从零开始的索引。<br/>如果传入负数，则从最后一个元素开始反向计数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 指定下标的元素；如果不存在，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The at method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## constructor

```TypeScript
constructor()
```

构造函数，用于创建一个空的ArkTS Uint32Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-constructor()--><!--Device-Uint32Array-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Uint32Array's constructor cannot be directly invoked. |

## constructor

```TypeScript
constructor(length: number)
```

构造函数，用于创建一个指定长度的ArkTS Uint32Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-constructor(length: number)--><!--Device-Uint32Array-constructor(length: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 用于指定ArkTS Uint32Array的长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Uint32Array's constructor cannot be directly invoked. |

## constructor

```TypeScript
constructor(elements: Iterable<number>)
```

构造函数，以Iterable创建一个ArkTS Uint32Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-constructor(elements: Iterable<number>)--><!--Device-Uint32Array-constructor(elements: Iterable<number>)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elements | Iterable<number> | 是 | 可迭代数字集合，用于构造ArkTS Uint32Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Uint32Array's constructor cannot be directly invoked. |

## constructor

```TypeScript
constructor(array: ArrayLike<number> | ArrayBuffer)
```

构造函数，以ArrayLike或ArkTS ArrayBuffer创建一个ArkTS Uint32Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-constructor(array: ArrayLike<number> | ArrayBuffer)--><!--Device-Uint32Array-constructor(array: ArrayLike<number> | ArrayBuffer)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| array | ArrayLike<number> \| ArrayBuffer | 是 | 用于构造ArkTS Uint32Array的对象。当参数类型是ArrayBuffer时，buffer所占的字节数须是4的整数倍。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Uint32Array's constructor cannot be directly invoked. |

## constructor

```TypeScript
constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)
```

构造函数，以ArrayBuffer创建一个ArkTS Uint32Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)--><!--Device-Uint32Array-constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | [ArrayBuffer](arkts-arkts-collections-arraybuffer-c.md) | 是 | 用于构造ArkTS Uint32Array的ArrayBuffer对象。buffer所占的字节数须是4的整数倍。 |
| byteOffset | number | 否 | 指定buffer的字节偏移，从0开始。默认值为**0**。 |
| length | number | 否 | 指定ArkTS Uint32Array的长度。默认值为**0**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Uint32Array's constructor cannot be directly invoked. |

## copyWithin

```TypeScript
copyWithin(target: number, start: number, end?: number): Uint32Array
```

从ArkTS Uint32Array指定范围内的元素依次拷贝到目标位置。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-copyWithin(target: number, start: number, end?: number): Uint32Array--><!--Device-Uint32Array-copyWithin(target: number, start: number, end?: number): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | number | 是 | 目标起始位置的下标。如果传入负数，则指代`target + array.length`位置的下标。 |
| start | number | 是 | 源起始位置的下标。如果传入负数，则指代`start + Uint32Array.length`位置的下标。 |
| end | number | 否 | 源终止位置的下标（不包含end位置的元素）。如果传入负数，则指代`end + Uint32Array.length`位置的下标。默认值为ArkTS Uint32Array的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 修改后的ArkTS Uint32Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The copyWithin method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## entries

```TypeScript
entries(): IterableIterator<[number, number]>
```

返回一个新的迭代器对象，该对象包含ArkTS Uint32Array中每个元素的键值对。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-entries(): IterableIterator<[number, number]>--><!--Device-Uint32Array-entries(): IterableIterator<[number, number]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<[number, number]> | 迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## every

```TypeScript
every(predicate: TypedArrayPredicateFn<number, Uint32Array>): boolean
```

测试ArkTS Uint32Array中的所有元素是否满足指定条件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-every(predicate: TypedArrayPredicateFn<number, Uint32Array>): boolean--><!--Device-Uint32Array-every(predicate: TypedArrayPredicateFn<number, Uint32Array>): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)<number, Uint32Array> | 是 | 用于测试的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果所有元素都满足指定条件则返回**true**；否则返回**false**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The every method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## fill

```TypeScript
fill(value: number, start?: number, end?: number): Uint32Array
```

使用特定值填充ArkTS Uint32Array指定范围的全部元素。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-fill(value: number, start?: number, end?: number): Uint32Array--><!--Device-Uint32Array-fill(value: number, start?: number, end?: number): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 待填充的值。 |
| start | number | 否 | 开始填充的索引。如果传入负数，则指代`start + Uint32Array.length`位置。默认值为**0**。 |
| end | number | 否 | 结束填充的索引（不包括该元素）。如果传入负数，则指代`end + Uint32Array.length`位置。默认值为ArkTS Uint32Array的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 填充后的ArkTS Uint32Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The fill method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## filter

```TypeScript
filter(predicate: TypedArrayPredicateFn<number, Uint32Array>): Uint32Array
```

返回一个新的ArkTS Uint32Array对象，其包含满足指定条件的所有元素。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-filter(predicate: TypedArrayPredicateFn<number, Uint32Array>): Uint32Array--><!--Device-Uint32Array-filter(predicate: TypedArrayPredicateFn<number, Uint32Array>): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)<number, Uint32Array> | 是 | 用于元素过滤的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 过滤后的ArkTS Uint32Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The filter method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## find

```TypeScript
find(predicate: TypedArrayPredicateFn<number, Uint32Array>): number | undefined
```

返回ArkTS Uint32Array中第一个满足指定条件的元素的值，如果所有元素都不满足，则返回**undefined**。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-find(predicate: TypedArrayPredicateFn<number, Uint32Array>): number | undefined--><!--Device-Uint32Array-find(predicate: TypedArrayPredicateFn<number, Uint32Array>): number | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)<number, Uint32Array> | 是 | 用于元素查找的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 第一个满足条件的元素的值；如果所有元素都不满足条件，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The find method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## findIndex

```TypeScript
findIndex(predicate: TypedArrayPredicateFn<number, Uint32Array>): number
```

返回ArkTS Uint32Array中第一个满足指定条件的元素索引，如果所有元素都不满足，则返回**-1**。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-findIndex(predicate: TypedArrayPredicateFn<number, Uint32Array>): number--><!--Device-Uint32Array-findIndex(predicate: TypedArrayPredicateFn<number, Uint32Array>): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)<number, Uint32Array> | 是 | 用于元素查找的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 第一个满足条件的元素索引；如果所有元素都不满足条件，则返回**-1**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The findIndex method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## forEach

```TypeScript
forEach(callbackFn: TypedArrayForEachCallback<number, Uint32Array>): void
```

对ArkTS Uint32Array中的每个元素执行提供的回调函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-forEach(callbackFn: TypedArrayForEachCallback<number, Uint32Array>): void--><!--Device-Uint32Array-forEach(callbackFn: TypedArrayForEachCallback<number, Uint32Array>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayForEachCallback](arkts-arkts-collections-typedarrayforeachcallback-t.md)<number, Uint32Array> | 是 | 用于对每个元素执行的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## from

```TypeScript
static from(arrayLike: ArrayLike<number>): Uint32Array
```

从一个ArrayLike或者可迭代对象中创建一个ArkTS Uint32Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-static from(arrayLike: ArrayLike<number>): Uint32Array--><!--Device-Uint32Array-static from(arrayLike: ArrayLike<number>): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLike | ArrayLike<number> | 是 | 用于构造ArkTS Uint32Array的ArrayLike对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 新创建的ArkTS Uint32Array对象。 |

## from

```TypeScript
static from<T>(arrayLike: ArrayLike<T>, mapFn: TypedArrayFromMapFn<T, number>): Uint32Array
```

从一个ArrayLike中创建一个ArkTS Uint32Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-static from<T>(arrayLike: ArrayLike<T>, mapFn: TypedArrayFromMapFn<T, number>): Uint32Array--><!--Device-Uint32Array-static from<T>(arrayLike: ArrayLike<T>, mapFn: TypedArrayFromMapFn<T, number>): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLike | ArrayLike<T> | 是 | 用于构造ArrayLike对象。 |
| mapFn | [TypedArrayFromMapFn](arkts-arkts-collections-typedarrayfrommapfn-t.md)<T, number> | 是 | 映射函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 新创建的ArkTS Uint32Array对象。 |

## from

```TypeScript
static from(arrayLike: Iterable<number>, mapFn?: TypedArrayFromMapFn<number, number>): Uint32Array
```

从一个可迭代对象中创建一个ArkTS Uint32Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-static from(arrayLike: Iterable<number>, mapFn?: TypedArrayFromMapFn<number, number>): Uint32Array--><!--Device-Uint32Array-static from(arrayLike: Iterable<number>, mapFn?: TypedArrayFromMapFn<number, number>): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLike | Iterable<number> | 是 | 用于构造的可迭代对象。 |
| mapFn | [TypedArrayFromMapFn](arkts-arkts-collections-typedarrayfrommapfn-t.md)<number, number> | 否 | 映射函数，用于对每个元素进行加工处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 新创建的ArkTS Uint32Array对象。 |

## includes

```TypeScript
includes(searchElement: number, fromIndex?: number): boolean
```

判断ArkTS Uint32Array是否包含特定元素。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-includes(searchElement: number, fromIndex?: number): boolean--><!--Device-Uint32Array-includes(searchElement: number, fromIndex?: number): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchElement | number | 是 | 待搜索的元素。 |
| fromIndex | number | 否 | 开始搜索的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果ArkTS Uint32Array包含指定的元素，则返回**true**；否则返回**false**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The includes method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## indexOf

```TypeScript
indexOf(searchElement: number, fromIndex?: number): number
```

返回在ArkTS Uint32Array中给定元素的第一个索引，如果不存在，则返回**-1**。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-indexOf(searchElement: number, fromIndex?: number): number--><!--Device-Uint32Array-indexOf(searchElement: number, fromIndex?: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchElement | number | 是 | 待索引的值。 |
| fromIndex | number | 否 | 搜索的起始下标。默认值为**0**。如果下标大于等于ArkTS Uint32Array的长度，则返回**-1**。如果传入负数，则从ArkTS Uint32Array的末尾开始向前搜索。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 数组中给定元素的第一个索引；如果不存在，则返回**-1**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The indexOf method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## join

```TypeScript
join(separator?: string): string
```

将ArkTS Uint32Array的所有元素拼接成一个字符串，元素之间使用指定的分隔符分隔。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-join(separator?: string): string--><!--Device-Uint32Array-join(separator?: string): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| separator | string | 否 | 分隔字符串。如果省略，则使用逗号（,）作为分隔符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 拼接后的字符串。如果ArkTS Uint32Array为空，则返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The join method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## keys

```TypeScript
keys(): IterableIterator<number>
```

返回一个新的迭代器对象，该对象包含ArkTS Uint32Array中每个元素的键（下标）。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-keys(): IterableIterator<number>--><!--Device-Uint32Array-keys(): IterableIterator<number>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<number> | 迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The keys method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## lastIndexOf

```TypeScript
lastIndexOf(searchElement: number, fromIndex?: number): number
```

返回ArkTS Uint32Array实例中最后一次出现给定元素的索引，如果不存在，则返回**-1**。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-lastIndexOf(searchElement: number, fromIndex?: number): number--><!--Device-Uint32Array-lastIndexOf(searchElement: number, fromIndex?: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchElement | number | 是 | 待索引的值。 |
| fromIndex | number | 否 | 搜索的起始下标。默认值为**0**。如果下标大于等于ArkTS Uint32Array的长度，则返回**-1**。如果传入负数，则从ArkTS Uint32Array的末尾开始向前搜索。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 数组中给定元素的最后一个索引；如果不存在，则返回**-1**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The lastIndexOf method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## map

```TypeScript
map(callbackFn: TypedArrayMapCallback<number, Uint32Array>): Uint32Array
```

对ArkTS Uint32Array中的每个元素应用指定的回调函数，并使用结果创建一个新的ArkTS Uint32Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-map(callbackFn: TypedArrayMapCallback<number, Uint32Array>): Uint32Array--><!--Device-Uint32Array-map(callbackFn: TypedArrayMapCallback<number, Uint32Array>): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayMapCallback](arkts-arkts-collections-typedarraymapcallback-t.md)<number, Uint32Array> | 是 | 一个最多接受三个参数的函数。map方法对数组中的每个元素调用一次callbackfn函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 新的ArkTS Uint32Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The map method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## of

```TypeScript
static of(...items: number[]): Uint32Array
```

通过可变数量的参数创建一个新的ArkTS Uint32Array对象。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-static of(...items: number[]): Uint32Array--><!--Device-Uint32Array-static of(...items: number[]): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | number[] | 是 | 用于创建数组的元素，参数个数可以是0个、1个或者多个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 新的ArkTS Uint32Array实例。可能的原因：1.必填参数未指定；<br>2.参数类型不正确；3.参数校验失败。 |

## reduce

```TypeScript
reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint32Array>): number
```

对ArkTS Uint32Array中的每个元素执行归约函数，并返回最终的归约结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint32Array>): number--><!--Device-Uint32Array-reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint32Array>): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)<number, number, Uint32Array> | 是 | 一个最多接受四个参数的函数。reduce方法对数组中的每个元素调用一次callbackfn函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 由归约函数最后一次调用返回的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## reduce

```TypeScript
reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint32Array>, initialValue: number): number
```

对ArkTS Uint32Array中的每个元素执行归约函数，且接收一个初始值作为归约函数首次调用的参数，并返回最终的归约结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint32Array>, initialValue: number): number--><!--Device-Uint32Array-reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint32Array>, initialValue: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)<number, number, Uint32Array> | 是 | 一个最多接受四个参数的函数。reduce方法对数组中的每个元素调用一次callbackfn函数。 |
| initialValue | number | 是 | 如果指定了initialValue，则将其作为开始累加的初始值。首次调用callbackfn函数时将提供此值作为参数，而不是数组元素值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 由归约函数最后一次调用返回的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## reduce

```TypeScript
reduce<U>(callbackFn: TypedArrayReduceCallback<U, number, Uint32Array>, initialValue: U): U
```

对ArkTS Uint32Array中的每个元素执行归约函数，且接收一个初始值作为归约函数首次调用的参数，并返回最终的归约结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-reduce<U>(callbackFn: TypedArrayReduceCallback<U, number, Uint32Array>, initialValue: U): U--><!--Device-Uint32Array-reduce<U>(callbackFn: TypedArrayReduceCallback<U, number, Uint32Array>, initialValue: U): U-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)<U, number, Uint32Array> | 是 | 归约函数。 |
| initialValue | U | 是 | 初始值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| U | 由归约函数最后一次调用返回的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## reduceRight

```TypeScript
reduceRight<U = number>(callbackFn: TypedArrayReduceCallback<U, number, Uint32Array>, initialValue: U): U
```

反向遍历ArkTS Uint32Array，对ArkTS Uint32Array中的每个元素执行归约函数，且接收一个初始值作为归约函数首次调用的参数，并返回最终的归约结果。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-reduceRight<U = number>(callbackFn: TypedArrayReduceCallback<U, number, Uint32Array>, initialValue: U): U--><!--Device-Uint32Array-reduceRight<U = number>(callbackFn: TypedArrayReduceCallback<U, number, Uint32Array>, initialValue: U): U-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)<U, number, Uint32Array> | 是 | 对Uint32Array中的每个元素调用的函数。 |
| initialValue | U | 是 | 作为回调函数首次调用时第一个参数使用的值。<br>若未提供初始值，则使用Uint32Array的最后一个元素作为初始值，<br>且回调函数将从倒数第二个元素开始调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| U | 由归约函数最后一次调用返回的结果。可能的原因：1.必填参数未指定。2.参数类型不正确。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduceRight method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## reduceRight

```TypeScript
reduceRight(callbackFn: TypedArrayReduceCallback<number, number, Uint32Array>): number
```

反向遍历ArkTS Uint32Array，对ArkTS Uint32Array中的每个元素执行归约函数，并返回最终的归约结果。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-reduceRight(callbackFn: TypedArrayReduceCallback<number, number, Uint32Array>): number--><!--Device-Uint32Array-reduceRight(callbackFn: TypedArrayReduceCallback<number, number, Uint32Array>): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)<number, number, Uint32Array> | 是 | 对Uint32Array中的每个元素调用的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 由归约函数最后一次调用返回的结果。可能的原因：1.必填参数未指定。2.参数类型不正确。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduceRight method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## reverse

```TypeScript
reverse(): Uint32Array
```

反转ArkTS Uint32Array。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-reverse(): Uint32Array--><!--Device-Uint32Array-reverse(): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 反转后的ArkTS Uint32Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reverse method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## set

```TypeScript
set(array: ArrayLike<number>, offset?: number): void
```

将传入的ArrayLike元素依次写入到指定的起始位置。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-set(array: ArrayLike<number>, offset?: number): void--><!--Device-Uint32Array-set(array: ArrayLike<number>, offset?: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| array | ArrayLike<number> | 是 | 用于设置的ArrayLike对象。 |
| offset | number | 否 | 写入的起始位置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The set method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## slice

```TypeScript
slice(start?: number, end?: number): Uint32Array
```

返回一个新的ArkTS Uint32Array对象，其包含原ArkTS Uint32Array指定范围的内容。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-slice(start?: number, end?: number): Uint32Array--><!--Device-Uint32Array-slice(start?: number, end?: number): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 否 | 开始索引。如果传入负数，则指代`start + Uint32Array.length`位置。默认值为**0**。 |
| end | number | 否 | 结束索引（不包括该元素）。如果传入负数，则指代`end + Uint32Array.length`位置。默认值为ArkTS Uint32Array的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 新的ArkTS Uint32Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The slice method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## some

```TypeScript
some(predicate: TypedArrayPredicateFn<number, Uint32Array>): boolean
```

测试ArkTS Uint32Array中是否存在元素满足指定条件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-some(predicate: TypedArrayPredicateFn<number, Uint32Array>): boolean--><!--Device-Uint32Array-some(predicate: TypedArrayPredicateFn<number, Uint32Array>): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)<number, Uint32Array> | 是 | 用于测试的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果存在元素满足指定条件则返回**true**；否则返回**false**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The some method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## sort

```TypeScript
sort(compareFn?: TypedArrayCompareFn<number>): Uint32Array
```

对ArkTS Uint32Array进行排序，并返回排序后的ArkTS Uint32Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-sort(compareFn?: TypedArrayCompareFn<number>): Uint32Array--><!--Device-Uint32Array-sort(compareFn?: TypedArrayCompareFn<number>): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| compareFn | [TypedArrayCompareFn](arkts-arkts-collections-typedarraycomparefn-t.md)<number> | 否 | 用于确定元素顺序的函数。默认使用升序排序。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 排序后的ArkTS Uint32Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The sort method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## subarray

```TypeScript
subarray(begin?: number, end?: number): Uint32Array
```

从指定的位置截取数组，返回一个新的、基于相同ArkTS ArrayBuffer的ArkTS Uint32Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-subarray(begin?: number, end?: number): Uint32Array--><!--Device-Uint32Array-subarray(begin?: number, end?: number): Uint32Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | number | 否 | 开始索引。如果传入负数，则指代`begin + Uint32Array.length`位置。默认值为**0**。 |
| end | number | 否 | 结束索引（不包括该元素）。如果传入负数，则指代`end + Uint32Array.length`位置。默认值为ArkTS Uint32Array的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 新的ArkTS Uint32Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The subarray method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## toLocaleString

```TypeScript
toLocaleString(): string
```

根据当前应用的系统地区获取符合当前文化习惯的数字表示形式，让每个元素调用自己的**toLocaleString**方法把数字转换为字符串，然后使用逗号（,）将每个元素的结果字符串按照顺序拼接成字符串。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-toLocaleString(): string--><!--Device-Uint32Array-toLocaleString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 一个包含数组所有元素的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The toLocaleString method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## toString

```TypeScript
toString(): string
```

ArkTS Uint32Array转换为字符串。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-toString(): string--><!--Device-Uint32Array-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 一个包含数组所有元素的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The toString method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## values

```TypeScript
values(): IterableIterator<number>
```

返回一个新的迭代器对象，该对象包含ArkTS Uint32Array中每个元素的值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-values(): IterableIterator<number>--><!--Device-Uint32Array-values(): IterableIterator<number>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<number> | 迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## BYTES_PER_ELEMENT

```TypeScript
static readonly BYTES_PER_ELEMENT: number
```

ArkTS Uint32Array中每个元素所占用的字节数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-static readonly BYTES_PER_ELEMENT: number--><!--Device-Uint32Array-static readonly BYTES_PER_ELEMENT: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## buffer

```TypeScript
readonly buffer: ArrayBuffer
```

ArkTS Uint32Array底层使用的buffer。

**类型：** ArrayBuffer

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-readonly buffer: ArrayBuffer--><!--Device-Uint32Array-readonly buffer: ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

## byteLength

```TypeScript
readonly byteLength: number
```

ArkTS Uint32Array所占的字节数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-readonly byteLength: number--><!--Device-Uint32Array-readonly byteLength: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## byteOffset

```TypeScript
readonly byteOffset: number
```

ArkTS Uint32Array距离其ArrayBuffer起始位置的偏移。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-readonly byteOffset: number--><!--Device-Uint32Array-readonly byteOffset: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## index

```TypeScript
[index: number]: number
```

返回Uint32Array指定索引位置的元素。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-[index: number]: number--><!--Device-Uint32Array-[index: number]: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## length

```TypeScript
readonly length: number
```

ArkTS Uint32Array元素个数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint32Array-readonly length: number--><!--Device-Uint32Array-readonly length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

