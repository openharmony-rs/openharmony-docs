# Uint16Array

一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md)实现。

> **说明**  
>  
> - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  
> **装饰器类型**：\@Sendable

**起始版本：** 12

**装饰器类型：** @Sendable

<!--Device-collections-class Uint16Array--><!--Device-collections-class Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { collections } from '@kit.ArkTS';
```

<a id="[symbol.iterator]"></a>
## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<number>
```

返回一个迭代器，迭代器的每一项都是一个数字。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-[Symbol.iterator](): IterableIterator<number>--><!--Device-Uint16Array-[Symbol.iterator](): IterableIterator<number>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;number&gt; | 迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

<a id="at"></a>
## at

```TypeScript
at(index: number): number | undefined
```

返回指定下标的元素，如果不存在，则返回**undefined**。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-at(index: number): number | undefined--><!--Device-Uint16Array-at(index: number): number | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 要返回的Array元素的索引（从零开始），取值为整数。<br/>如果`index < 0`，则会访问`index + Uint16Array.length`位置的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 指定下标的元素；如果不存在，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The at method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

构造函数，用于创建一个空ArkTS Uint16Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-constructor()--><!--Device-Uint16Array-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Uint16Array's constructor cannot be directly invoked. |

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(length: number)
```

构造函数，用于创建一个指定长度的ArkTS Uint16Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-constructor(length: number)--><!--Device-Uint16Array-constructor(length: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 用于指定ArkTS Uint16Array的长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Uint16Array's constructor cannot be directly invoked. |

<a id="constructor-2"></a>
## constructor

```TypeScript
constructor(elements: Iterable<number>)
```

构造函数，以Iterable创建一个ArkTS Uint16Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-constructor(elements: Iterable<number>)--><!--Device-Uint16Array-constructor(elements: Iterable<number>)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elements | Iterable&lt;number&gt; | 是 | 可迭代数字集合，用于构造ArkTS Uint16Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Uint16Array's constructor cannot be directly invoked. |

<a id="constructor-3"></a>
## constructor

```TypeScript
constructor(array: ArrayLike<number> | ArrayBuffer)
```

构造函数，以ArrayLike或ArkTS ArrayBuffer创建一个ArkTS Uint16Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-constructor(array: ArrayLike<number> | ArrayBuffer)--><!--Device-Uint16Array-constructor(array: ArrayLike<number> | ArrayBuffer)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| array | ArrayLike&lt;number&gt; \| ArrayBuffer | 是 | 用于构造ArkTS Uint16Array的对象。当参数类型是ArrayBuffer时buffer所占的字节数须是4的整数倍。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Uint16Array's constructor cannot be directly invoked. |

<a id="constructor-4"></a>
## constructor

```TypeScript
constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)
```

构造函数，以ArrayBuffer创建一个ArkTS Uint16Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)--><!--Device-Uint16Array-constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 用于构造ArkTS Uint16Array的ArrayBuffer对象。buffer所占的字节数须是4的整数倍。 |
| byteOffset | number | 否 | 指定buffer的字节偏移，从0开始。默认值为**0**。 |
| length | number | 否 | 指定ArkTS Uint16Array的长度。默认值为**0**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Uint16Array's constructor cannot be directly invoked. |

<a id="copywithin"></a>
## copyWithin

```TypeScript
copyWithin(target: number, start: number, end?: number): Uint16Array
```

从ArkTS Uint16Array指定范围内的元素依次拷贝到目标位置。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-copyWithin(target: number, start: number, end?: number): Uint16Array--><!--Device-Uint16Array-copyWithin(target: number, start: number, end?: number): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | number | 是 | 目标起始位置的下标，如果`target < 0`，则会从`target + array.length`位置开始。 |
| start | number | 是 | 源起始位置下标，如果`start < 0`，则会从`start + Uint16Array.length`位置开始。 |
| end | number | 否 | 源终止位置下标（不包含end位置的元素），如果`end < 0`，则会从`end +Uint16Array.length`位置终止。默认为ArkTS Uint16Array的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 修改后的ArkTS Uint16Array。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The copyWithin method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="entries"></a>
## entries

```TypeScript
entries(): IterableIterator<[number, number]>
```

返回一个新的迭代器对象，该对象包含ArkTS Uint16Array中每个元素的键值对。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-entries(): IterableIterator<[number, number]>--><!--Device-Uint16Array-entries(): IterableIterator<[number, number]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[number, number]&gt; | 新的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="every"></a>
## every

```TypeScript
every(predicate: TypedArrayPredicateFn<number, Uint16Array>): boolean
```

测试ArkTS Uint16Array中的所有元素是否满足指定条件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-every(predicate: TypedArrayPredicateFn<number, Uint16Array>): boolean--><!--Device-Uint16Array-every(predicate: TypedArrayPredicateFn<number, Uint16Array>): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)&lt;number, Uint16Array&gt; | 是 | 用于测试的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果所有元素都满足指定条件则返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The every method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="fill"></a>
## fill

```TypeScript
fill(value: number, start?: number, end?: number): Uint16Array
```

使用特定值填充ArkTS Uint16Array指定范围的全部元素。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-fill(value: number, start?: number, end?: number): Uint16Array--><!--Device-Uint16Array-fill(value: number, start?: number, end?: number): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 待填充的值。 |
| start | number | 否 | 开始填充的索引，如果`start < 0`，则会从`start +Uint16Array.length`位置开始。默认值为**0**。 |
| end | number | 否 | 结束填充的索引（不包括该元素），如果`end < 0`，则会到`end +Uint16Array.length`位置结束。默认为ArkTS Uint16Array的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 填充后的ArkTS Uint16Array。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The fill method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="filter"></a>
## filter

```TypeScript
filter(predicate: TypedArrayPredicateFn<number, Uint16Array>): Uint16Array
```

返回一个新ArkTS Uint16Array，其包含满足指定条件的所有元素。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-filter(predicate: TypedArrayPredicateFn<number, Uint16Array>): Uint16Array--><!--Device-Uint16Array-filter(predicate: TypedArrayPredicateFn<number, Uint16Array>): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)&lt;number, Uint16Array&gt; | 是 | 用于元素过滤的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 过滤后的ArkTS Uint16Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The filter method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="find"></a>
## find

```TypeScript
find(predicate: TypedArrayPredicateFn<number, Uint16Array>): number | undefined
```

返回ArkTS Uint16Array中第一个满足指定条件的元素的值，如果所有元素都不满足，则返回**undefined**。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-find(predicate: TypedArrayPredicateFn<number, Uint16Array>): number | undefined--><!--Device-Uint16Array-find(predicate: TypedArrayPredicateFn<number, Uint16Array>): number | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)&lt;number, Uint16Array&gt; | 是 | 用于元素查找的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 第一个满足条件的元素的值；如果所有元素都不满足条件，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The find method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="findindex"></a>
## findIndex

```TypeScript
findIndex(predicate: TypedArrayPredicateFn<number, Uint16Array>): number
```

返回ArkTS Uint16Array中第一个满足指定条件的元素索引，如果所有元素都不满足，则返回**-1**。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-findIndex(predicate: TypedArrayPredicateFn<number, Uint16Array>): number--><!--Device-Uint16Array-findIndex(predicate: TypedArrayPredicateFn<number, Uint16Array>): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)&lt;number, Uint16Array&gt; | 是 | 用于元素查找的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 第一个满足条件的元素索引；如果所有元素都不满足条件，则返回**-1**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The findIndex method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="foreach"></a>
## forEach

```TypeScript
forEach(callbackFn: TypedArrayForEachCallback<number, Uint16Array>): void
```

对ArkTS Uint16Array中的每个元素执行提供的回调函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-forEach(callbackFn: TypedArrayForEachCallback<number, Uint16Array>): void--><!--Device-Uint16Array-forEach(callbackFn: TypedArrayForEachCallback<number, Uint16Array>): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayForEachCallback](arkts-arkts-collections-typedarrayforeachcallback-t.md)&lt;number, Uint16Array&gt; | 是 | 用于对每个元素执行的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="from"></a>
## from

```TypeScript
static from(arrayLike: ArrayLike<number>): Uint16Array
```

从一个ArrayLike或者可迭代对象中创建一个ArkTS Uint16Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-static from(arrayLike: ArrayLike<number>): Uint16Array--><!--Device-Uint16Array-static from(arrayLike: ArrayLike<number>): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;number&gt; | 是 | 用于构造ArkTS Uint16Array的ArrayLike对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 新创建的ArkTS Uint16Array对象。 |

<a id="from-1"></a>
## from

```TypeScript
static from<T>(arrayLike: ArrayLike<T>, mapFn: TypedArrayFromMapFn<T, number>): Uint16Array
```

从一个ArrayLike中创建一个ArkTS Uint16Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-static from<T>(arrayLike: ArrayLike<T>, mapFn: TypedArrayFromMapFn<T, number>): Uint16Array--><!--Device-Uint16Array-static from<T>(arrayLike: ArrayLike<T>, mapFn: TypedArrayFromMapFn<T, number>): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; | 是 | 用于构造ArrayLike对象。 |
| mapFn | [TypedArrayFromMapFn](arkts-arkts-collections-typedarrayfrommapfn-t.md)&lt;T, number&gt; | 是 | 映射函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 新创建的ArkTS Uint16Array对象。 |

<a id="from-2"></a>
## from

```TypeScript
static from(arrayLike: Iterable<number>, mapFn?: TypedArrayFromMapFn<number, number>): Uint16Array
```

从一个可迭代对象中创建一个ArkTS Uint16Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-static from(arrayLike: Iterable<number>, mapFn?: TypedArrayFromMapFn<number, number>): Uint16Array--><!--Device-Uint16Array-static from(arrayLike: Iterable<number>, mapFn?: TypedArrayFromMapFn<number, number>): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLike | Iterable&lt;number&gt; | 是 | 用于构造的可迭代对象。 |
| mapFn | [TypedArrayFromMapFn](arkts-arkts-collections-typedarrayfrommapfn-t.md)&lt;number, number&gt; | 否 | 映射函数。如果省略，则不对元素进行加工处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 新创建的ArkTS Uint16Array对象。 |

<a id="includes"></a>
## includes

```TypeScript
includes(searchElement: number, fromIndex?: number): boolean
```

判断ArkTS Uint16Array是否包含特定元素。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-includes(searchElement: number, fromIndex?: number): boolean--><!--Device-Uint16Array-includes(searchElement: number, fromIndex?: number): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchElement | number | 是 | 待搜索的元素。 |
| fromIndex | number | 否 | 开始搜索的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果ArkTS Uint16Array包含指定的元素，则返回true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The includes method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="indexof"></a>
## indexOf

```TypeScript
indexOf(searchElement: number, fromIndex?: number): number
```

返回在ArkTS Uint16Array中给定元素的第一个索引，如果不存在，则返回**-1**。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-indexOf(searchElement: number, fromIndex?: number): number--><!--Device-Uint16Array-indexOf(searchElement: number, fromIndex?: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchElement | number | 是 | 待索引的值。 |
| fromIndex | number | 否 | 搜索的起始下标。默认值为**0**。如果下标大于等于ArkTS Uint16Array的长度，则返回**-1**。如果提供的下标值是负数，则被当做距离数组尾部的偏移，从前到后搜索。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 数组中元素的第一个索引；没有找到，则返回**-1**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The indexOf method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="join"></a>
## join

```TypeScript
join(separator?: string): string
```

将ArkTS Uint16Array的所有元素拼接成一个字符串，元素之间使用指定的分隔符分隔。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-join(separator?: string): string--><!--Device-Uint16Array-join(separator?: string): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| separator | string | 否 | 分隔字符串。如果省略，则使用逗号（,）分隔。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 包含所有元素拼接成的字符串。如果ArkTS Uint16Array为空，则返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The join method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="keys"></a>
## keys

```TypeScript
keys(): IterableIterator<number>
```

返回一个新的迭代器对象，该对象包含ArkTS Uint16Array中每个元素的键（下标）。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-keys(): IterableIterator<number>--><!--Device-Uint16Array-keys(): IterableIterator<number>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;number&gt; | 新的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The keys method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="lastindexof"></a>
## lastIndexOf

```TypeScript
lastIndexOf(searchElement: number, fromIndex?: number): number
```

返回ArkTS Uint16Array实例中最后一次出现searchElement的索引，如果对象不包含，则为-1。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-lastIndexOf(searchElement: number, fromIndex?: number): number--><!--Device-Uint16Array-lastIndexOf(searchElement: number, fromIndex?: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchElement | number | 是 | 待索引的值。 |
| fromIndex | number | 否 | 搜索的起始下标。默认值为**0**。如果下标大于等于ArkTS Uint16Array的长度，则返回**-1**。如果提供的下标值是负数，则被当做距离数组尾部的偏移，从后到前搜索。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 数组中给定元素的最后一个索引；没有找到，则返回**-1**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The lastIndexOf method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="map"></a>
## map

```TypeScript
map(callbackFn: TypedArrayMapCallback<number, Uint16Array>): Uint16Array
```

对ArkTS Uint16Array中的每个元素应用指定的回调函数，并使用结果创建一个新的ArkTS Uint16Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-map(callbackFn: TypedArrayMapCallback<number, Uint16Array>): Uint16Array--><!--Device-Uint16Array-map(callbackFn: TypedArrayMapCallback<number, Uint16Array>): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayMapCallback](arkts-arkts-collections-typedarraymapcallback-t.md)&lt;number, Uint16Array&gt; | 是 | 回调函数。map方法会对数组中的每个元素调用一次callbackFn函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 新ArkTS Uint16Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The map method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="of"></a>
## of

```TypeScript
static of(...items: number[]): Uint16Array
```

通过可变数量的参数创建一个新的ArkTS Uint16Array对象，参数个数可以是0个、1个或者多个。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-static of(...items: number[]): Uint16Array--><!--Device-Uint16Array-static of(...items: number[]): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | number[] | 是 | 用于创建数组的元素，参数个数可以是0个、1个或者多个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 新的ArkTS Uint16Array实例。可能的异常原因：1.必填参数未指定；<br>2.参数类型不正确；3.参数校验失败。 |

<a id="reduce"></a>
## reduce

```TypeScript
reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint16Array>): number
```

对ArkTS Uint16Array中的每个元素执行归约函数，并返回最终的归约结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint16Array>): number--><!--Device-Uint16Array-reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint16Array>): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)&lt;number, number, Uint16Array&gt; | 是 | 归约函数。reduce方法会对数组中的每个元素调用一次callbackFn函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 由最后一次调用归约函数返回的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="reduce-1"></a>
## reduce

```TypeScript
reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint16Array>, initialValue: number): number
```

对ArkTS Uint16Array中的每个元素执行归约函数，且接收一个初始值作为归约函数首次调用的参数，并返回最终的归约结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint16Array>, initialValue: number): number--><!--Device-Uint16Array-reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint16Array>, initialValue: number): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)&lt;number, number, Uint16Array&gt; | 是 | 归约函数。reduce方法会对数组中的每个元素调用一次callbackFn函数。 |
| initialValue | number | 是 | 如果指定了initialValue，则将其作为初始值开始累加。首次调用callbackFn函数时会将该值作为参数传入，而不是使用数组元素值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 由最后一次调用归约函数返回的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="reduce-2"></a>
## reduce

```TypeScript
reduce<U>(callbackFn: TypedArrayReduceCallback<U, number, Uint16Array>, initialValue: U): U
```

对ArkTS Uint16Array中的每个元素执行归约函数，且接收一个初始值作为归约函数首次调用的参数，并返回最终的归约结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-reduce<U>(callbackFn: TypedArrayReduceCallback<U, number, Uint16Array>, initialValue: U): U--><!--Device-Uint16Array-reduce<U>(callbackFn: TypedArrayReduceCallback<U, number, Uint16Array>, initialValue: U): U-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)&lt;U, number, Uint16Array&gt; | 是 | 归约函数。 |
| initialValue | U | 是 | 初始值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| U | 由最后一次调用归约函数返回的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="reduceright"></a>
## reduceRight

```TypeScript
reduceRight<U = number>(callbackFn: TypedArrayReduceCallback<U, number, Uint16Array>, initialValue: U): U
```

反向遍历ArkTS Uint16Array，对ArkTS Uint16Array中的每个元素执行归约函数，且接收一个初始值作为归约函数首次调用的参数，并返回最终的归约结果。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-reduceRight<U = number>(callbackFn: TypedArrayReduceCallback<U, number, Uint16Array>, initialValue: U): U--><!--Device-Uint16Array-reduceRight<U = number>(callbackFn: TypedArrayReduceCallback<U, number, Uint16Array>, initialValue: U): U-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)&lt;U, number, Uint16Array&gt; | 是 | 对Uint16Array中每个元素调用的函数。 |
| initialValue | U | 是 | 作为首次调用callbackFn函数第一个参数的值。<br>若未提供初始值，则会使用Uint16Array的最后一个元素作为初始值，<br>并从倒数第二个元素开始调用callback。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| U | 由最后一次调用归约函数返回的结果。可能的异常原因：1.必填参数未指定。2.参数类型不正确。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduceRight method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="reduceright-1"></a>
## reduceRight

```TypeScript
reduceRight(callbackFn: TypedArrayReduceCallback<number, number, Uint16Array>): number
```

反向遍历ArkTS Uint16Array，对ArkTS Uint16Array中的每个元素执行归约函数，并返回最终的归约结果。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-reduceRight(callbackFn: TypedArrayReduceCallback<number, number, Uint16Array>): number--><!--Device-Uint16Array-reduceRight(callbackFn: TypedArrayReduceCallback<number, number, Uint16Array>): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)&lt;number, number, Uint16Array&gt; | 是 | 对Uint16Array中每个元素调用的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 由最后一次调用归约函数返回的结果。可能的异常原因：1.必填参数未指定。2.参数类型不正确。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduceRight method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="reverse"></a>
## reverse

```TypeScript
reverse(): Uint16Array
```

反转ArkTS Uint16Array。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-reverse(): Uint16Array--><!--Device-Uint16Array-reverse(): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 反转后的ArkTS Uint16Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reverse method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="set"></a>
## set

```TypeScript
set(array: ArrayLike<number>, offset?: number): void
```

将传入的ArrayLike元素依次写入到指定的起始位置。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-set(array: ArrayLike<number>, offset?: number): void--><!--Device-Uint16Array-set(array: ArrayLike<number>, offset?: number): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| array | ArrayLike&lt;number&gt; | 是 | 用于设置的ArrayLike对象。 |
| offset | number | 否 | 写入的起始位置。默认为0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The set method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="slice"></a>
## slice

```TypeScript
slice(start?: number, end?: number): Uint16Array
```

返回一个新的ArkTS Uint16Array对象，其包含原ArkTS Uint16Array指定范围的内容。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-slice(start?: number, end?: number): Uint16Array--><!--Device-Uint16Array-slice(start?: number, end?: number): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 否 | 开始索引，如果`start < 0`，则会从`start +Uint16Array.length`位置开始。默认值为**0**。 |
| end | number | 否 | 结束索引（不包括该元素），如果`end < 0`，则会到`end +Uint16Array.length`位置结束。默认为ArkTS Uint16Array的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 新的ArkTS Uint16Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The slice method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="some"></a>
## some

```TypeScript
some(predicate: TypedArrayPredicateFn<number, Uint16Array>): boolean
```

测试ArkTS Uint16Array中的是否存在元素满足指定条件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-some(predicate: TypedArrayPredicateFn<number, Uint16Array>): boolean--><!--Device-Uint16Array-some(predicate: TypedArrayPredicateFn<number, Uint16Array>): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)&lt;number, Uint16Array&gt; | 是 | 用于测试的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果存在元素满足指定条件返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The some method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="sort"></a>
## sort

```TypeScript
sort(compareFn?: TypedArrayCompareFn<number>): Uint16Array
```

对ArkTS Uint16Array进行排序，并返回排序后的ArkTS Uint16Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-sort(compareFn?: TypedArrayCompareFn<number>): Uint16Array--><!--Device-Uint16Array-sort(compareFn?: TypedArrayCompareFn<number>): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| compareFn | [TypedArrayCompareFn](arkts-arkts-collections-typedarraycomparefn-t.md)&lt;number&gt; | 否 | 用于确定元素顺序的函数。默认使用升序排序。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 排序后的ArkTS Uint16Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The sort method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="subarray"></a>
## subarray

```TypeScript
subarray(begin?: number, end?: number): Uint16Array
```

从指定的位置截取数组，返回一个新的、基于相同ArkTS ArrayBuffer的ArkTS Uint16Array对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-subarray(begin?: number, end?: number): Uint16Array--><!--Device-Uint16Array-subarray(begin?: number, end?: number): Uint16Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | number | 否 | 开始索引，如果`begin < 0`，则会从`begin +Uint16Array.length`位置开始。默认值为**0**。 |
| end | number | 否 | 结束索引（不包括该元素），如果`end < 0`，则会到`end +Uint16Array.length`位置结束。默认为ArkTS Uint16Array的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint16Array | 新的ArkTS Uint16Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The subarray method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

<a id="tolocalestring"></a>
## toLocaleString

```TypeScript
toLocaleString(): string
```

根据当前应用的系统地区获取符合当前文化习惯的数字表示形式，让每个元素调用自己的toLocaleString方法把数字转换为字符串，然后使用逗号将每个元素的结果字符串按照顺序拼接成字符串。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-toLocaleString(): string--><!--Device-Uint16Array-toLocaleString(): string-End-->

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

<a id="tostring"></a>
## toString

```TypeScript
toString(): string
```

ArkTS Uint16Array转换为字符串。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-toString(): string--><!--Device-Uint16Array-toString(): string-End-->

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

<a id="values"></a>
## values

```TypeScript
values(): IterableIterator<number>
```

返回一个新的迭代器对象，该对象包含ArkTS Uint16Array中每个元素的值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-values(): IterableIterator<number>--><!--Device-Uint16Array-values(): IterableIterator<number>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;number&gt; | 新的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## BYTES_PER_ELEMENT

```TypeScript
static readonly BYTES_PER_ELEMENT: number
```

ArkTS Uint16Array中每个元素所占用的字节数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-static readonly BYTES_PER_ELEMENT: number--><!--Device-Uint16Array-static readonly BYTES_PER_ELEMENT: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## buffer

```TypeScript
readonly buffer: ArrayBuffer
```

ArkTS Uint16Array底层使用的buffer。

**类型：** ArrayBuffer

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-readonly buffer: ArrayBuffer--><!--Device-Uint16Array-readonly buffer: ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

## byteLength

```TypeScript
readonly byteLength: number
```

ArkTS Uint16Array的所占的字节数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-readonly byteLength: number--><!--Device-Uint16Array-readonly byteLength: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## byteOffset

```TypeScript
readonly byteOffset: number
```

ArkTS Uint16Array距离其ArrayBuffer起始位置的偏移。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-readonly byteOffset: number--><!--Device-Uint16Array-readonly byteOffset: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## index

```TypeScript
[index: number]: number
```

返回Uint16Array指定索引位置的元素。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-[index: number]: number--><!--Device-Uint16Array-[index: number]: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## length

```TypeScript
readonly length: number
```

ArkTS Uint16Array元素个数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Uint16Array-readonly length: number--><!--Device-Uint16Array-readonly length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

