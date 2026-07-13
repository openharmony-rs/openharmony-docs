# Array

一种线性数据结构，底层基于数组实现，可以在ArkTS上并发实例间传递。
推荐使用引用传递以提升传递性能。

> **说明**
>
> - 本模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。
> 本节使用以下标识来表示泛型的使用：

- T：Type，支持
[Sendable支持的数据类型](../../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。
**装饰器**：\@Sendable

**继承/实现关系：** Array implements [ConcatArray<T>](ConcatArray<T>)

**起始版本：** 12

**装饰器类型：** @Sendable

**系统能力：** SystemCapability.Utils.Lang

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

获取一个迭代器，迭代器的每一项都是一个 JavaScript 对象。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

## at

```TypeScript
at(index: number): T | undefined
```

返回ArkTS Array中指定索引位置的元素。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 要返回的Array元素的索引（从零开始），取值为整数。负数索引从Array末尾开始计数，如果传入负数，则指代**index + array.length**位置的下标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回指定索引处的元素；如果索引超出范围或无效，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The at method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## concat

```TypeScript
concat(...items: ConcatArray<T>[]): Array<T>
```

将ArkTS Array与一个或多个数组拼接。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | ConcatArray&lt;T&gt;[] | 是 | 用于拼接ArkTS Array的一个或多个数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 拼接后生成的新Array。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The concat method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## constructor

```TypeScript
constructor()
```

创建一个空的ArkTS Array的构造函数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Array's constructor cannot be directly invoked. |

## constructor

```TypeScript
constructor(first: T, ...left: T[])
```

ArkTS Array的构造函数，通过开发者提供的元素进行初始化。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| first | T | 是 | 初始化ArkTS Array的第一个元素。 |
| left | T[] | 是 | 初始化ArkTS Array的剩余元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Array's constructor cannot be directly invoked. |

## constructor

```TypeScript
constructor(...items: T[])
```

ArkTS Array的构造函数，通过开发者提供的元素进行初始化。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | T[] | 是 | 初始化ArkTS Array的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The Array's constructor cannot be directly invoked. |

## copyWithin

```TypeScript
copyWithin(target: number, start: number, end?: number): Array<T>
```

从ArkTS Array指定范围内的元素依次拷贝到目标位置。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | number | 是 | 目标起始位置的下标。如果传入负数，则指代`target + array.length`位置的下标。 |
| start | number | 是 | 源起始位置下标。如果传入负数，则指代**start + array.length**位置的下标。 |
| end | number | 否 | 源终止位置下标。如果传入负数，则指代 `end+ array.length`位置的下标。默认值为ArkTS Array的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 修改后的ArkTS Array。可能的原因：1. 必填参数未指定。2. 参数类型不正确。3. 参数校验失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The copyWithin method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## create

```TypeScript
static create<T>(arrayLength: number, initialValue: T): Array<T>
```

生成一个固定长度的ArkTS Array，其中每个元素的初始值为给定的初始值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLength | number | 是 | ArkTS Array的长度。 |
| initialValue | T | 是 | ArkTS Array中每个元素的初始值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 新创建的ArkTS Array实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The create method cannot be bound.<br>**适用版本：** 12 - 17 |

## entries

```TypeScript
entries(): IterableIterator<[number, T]>
```

返回一个迭代器对象，该对象包含ArkTS Array中每个元素的键值对。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[number, T]&gt; | 包含Array中每个元素的键值对的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## every

```TypeScript
every(predicate: ArrayPredicateFn<T, Array<T>>): boolean
```

测试ArkTS Array中的所有元素是否满足指定条件。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | ArrayPredicateFn&lt;T, Array&lt;T&gt;&gt; | 是 | 用于测试的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果所有元素都满足指定条件，则返回**true**；否则返回**false**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The every method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## extendTo

```TypeScript
extendTo(arrayLength: number, initialValue: T): void
```

使用指定初始值填充新增元素，使Array扩展到指定长度。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLength | number | 是 | Array的新长度。如果传入的值小于或等于当前Array的长度，Array不发生变化。 |
| initialValue | T | 是 | 新增元素的初始值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The extendTo method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## fill

```TypeScript
fill(value: T, start?: number, end?: number): Array<T>
```

使用指定的值填充ArkTS Array中指定范围的所有元素。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 要填充的值。 |
| start | number | 否 | 开始填充的索引。默认值为**0**。 |
| end | number | 否 | 结束填充的索引（不包括该元素）。如果未传入，则指代数组的最后一个元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 填充后的Array。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The fill method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## filter

```TypeScript
filter(predicate: (value: T, index: number, array: Array<T>) => boolean): Array<T>
```

返回一个新Array，其中包含通过指定回调函数测试的所有元素。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | (value: T, index: number, array: Array&lt;T&gt;) =&gt; boolean | 是 | 一个接受三个参数的函数，用于筛选元素。返回值为**true**表示当前元素通过测试，应保留在新数组中；返回值为**false**表示当前元素未通过测试，应被排除在新数组外。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 包含通过测试的元素的新Array。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The filter method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## find

```TypeScript
find(predicate: (value: T, index: number, obj: Array<T>) => boolean): T | undefined
```

返回通过回调函数测试的第一个元素的值。如果所有元素都不满足，则返回**undefined**。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | (value: T, index: number, obj: Array&lt;T&gt;) =&gt; boolean | 是 | 一个接受三个参数的函数，用于筛选元素。返回值为**true**表示当前元素满足条件，会立即停止遍历，并将该元素作为结果返回；返回值为**false**表示当前元素不满足条件，会继续检查下一个元素，直到找到符合条件的元素或遍历完整个数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 第一个满足条件的元素的值；如果所有元素都不满足条件，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The find method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## findIndex

```TypeScript
findIndex(predicate: (value: T, index: number, obj: Array<T>) => boolean): number
```

返回通过回调函数测试的第一个元素的索引，如果所有元素都不满足，则返回**-1**。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | (value: T, index: number, obj: Array&lt;T&gt;) =&gt; boolean | 是 | 一个接受三个参数的函数，用于筛选元素。返回值为**true**表示当前元素满足条件，会立即停止遍历，并返回该元素的索引；返回值为**false**表示当前元素不满足条件，会继续检查下一个元素，直到找到符合条件的元素或遍历完整个数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 第一个满足条件的元素的索引；如果所有元素都不满足条件，则返回**-1**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The findIndex method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## forEach

```TypeScript
forEach(callbackFn: (value: T, index: number, array: Array<T>) => void): void
```

对ArkTS Array中的每个元素执行提供的回调函数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index: number, array: Array&lt;T&gt;) =&gt; void | 是 | 用于对每个元素执行的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## from

```TypeScript
static from<T>(arrayLike: ArrayLike<T>): Array<T>
```

从一个实现了ArrayLike接口的对象创建一个新的ArkTS Array。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; | 是 | 用于构造ArkTS Array的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 新创建的ArkTS Array实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The from method cannot be bound.<br>**适用版本：** 12 - 17 |

## from

```TypeScript
static from<T>(iterable: Iterable<T>): Array<T>
```

从一个实现了Iterable接口的对象创建一个新的ArkTS Array。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iterable | Iterable&lt;T&gt; | 是 | 用于构造ArkTS Array的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 新创建的ArkTS Array实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The from method cannot be bound.<br>**适用版本：** 12 - 17 |

## from

```TypeScript
static from<T>(arrayLike: ArrayLike<T> | Iterable<T>, mapFn: ArrayFromMapFn<T, T>): Array<T>
```

从一个实现了ArrayLike接口的对象创建一个新的ArkTS Array，并使用自定义函数处理每个数组元素。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; \| Iterable&lt;T&gt; | 是 | 用于构造ArkTS Array的对象。 |
| mapFn | ArrayFromMapFn&lt;T, T&gt; | 是 | 用于处理数组元素的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 新创建的ArkTS Array实例。 |

## from

```TypeScript
static from<U, T>(arrayLike: ArrayLike<U> | Iterable<U>, mapFn: ArrayFromMapFn<U, T>): Array<T>
```

从一个实现了ArrayLike接口的对象创建一个新的ArkTS Array，并使用自定义函数处理每个数组元素。
ArrayLike接口对象的元素类型可以和数组元素的类型不一样。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;U&gt; \| Iterable&lt;U&gt; | 是 | 用于构造ArkTS Array的对象。 |
| mapFn | ArrayFromMapFn&lt;U, T&gt; | 是 | 用于处理数组元素的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 新创建的ArkTS Array实例。 |

## includes

```TypeScript
includes(searchElement: T, fromIndex?: number): boolean
```

判断ArkTS Array是否包含指定的元素，并返回一个布尔值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchElement | T | 是 | 要搜索的元素。 |
| fromIndex | number | 否 | 开始搜索的索引。默认值为**0**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果Array包含指定的元素，则返回**true**；否则返回**false**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The includes method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## indexOf

```TypeScript
indexOf(searchElement: T, fromIndex?: number): number
```

返回在ArkTS Array中搜索元素首次出现的索引，如果不存在则返回**-1**。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchElement | T | 是 | 要搜索的值。 |
| fromIndex | number | 否 | 开始搜索的索引，从0开始。默认值为**0**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 搜索元素首次出现的索引；如果不存在，则返回**-1**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The indexOf method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## isArray

```TypeScript
static isArray(value: Object | undefined | null): boolean
```

检查传入的参数是否是一个ArkTS Array。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object \| undefined \| null | 是 | 需要检查的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果传入的参数是ArkTS Array，则返回**true**；否则返回**false**。可能的原因：1. 必填参数未指定。2. 参数类型不正确。3. 参数校验失败。 |

## join

```TypeScript
join(separator?: string): string
```

将ArkTS Array的所有元素连接成一个字符串，元素之间可以用指定的分隔符分隔。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| separator | string | 否 | 用于分隔Array元素的字符串。如果未传入，则使用逗号（,）作为分隔符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 连接后得到的字符串。如果Array为空，则返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The join method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## keys

```TypeScript
keys(): IterableIterator<number>
```

返回一个迭代器对象，该对象包含ArkTS Array中每个元素的索引。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;number&gt; | 包含Array中每个元素的索引的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The keys method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## lastIndexOf

```TypeScript
lastIndexOf(searchElement: T, fromIndex?: number): number
```

返回ArkTS Array实例中最后一次出现指定值的索引。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchElement | T | 是 | 要搜索的值。 |
| fromIndex | number | 否 | 开始搜索的索引。默认值为**0**。如果索引大于或等于ArkTS Array的长度，则返回**-1**。如果传入负数，则指代**fromIndex + array.length**位置的下标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 元素最后一次出现的索引；如果不存在，则返回**-1**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The lastIndexOf method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## map

```TypeScript
map<U>(callbackFn: (value: T, index: number, array: Array<T>) => U): Array<U>
```

对ArkTS Array中的每个元素执行提供的回调函数，并返回一个新的Array，该Array包含
回调函数的结果。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, index: number, array: Array&lt;T&gt;) =&gt; U | 是 | 用于对每个元素执行的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;U&gt; | 包含回调函数结果的新Array。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The map method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## of

```TypeScript
static of<T>(...items: T[]): Array<T>
```

通过可变数量的参数创建一个新的ArkTS Array。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | T[] | 是 | 用于创建数组的元素集合，参数个数可以是0个、1个或多个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 新创建的ArkTS Array实例。可能的原因：1. 必填参数未指定。2. 参数类型不正确。3. 参数校验失败。 |

## pop

```TypeScript
pop(): T | undefined
```

从ArkTS Array中移除并返回最后一个元素。如果Array为空，则返回**undefined**，
且Array不发生变化。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 从Array中移除的元素；如果Array为空，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The pop method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## push

```TypeScript
push(...items: T[]): number
```

在ArkTS Array的末尾添加元素，并返回新的Array长度。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | T[] | 是 | 要添加到Array末尾的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 新Array的长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The push method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## reduce

```TypeScript
reduce(callbackFn: (previousValue: T, currentValue: T, currentIndex: number, array: Array<T>) => T): T
```

对ArkTS Array中的每个元素执行回调函数，将上一次的返回值作为累加值，
并返回最终的结果。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (previousValue: T, currentValue: T, currentIndex: number, array: Array&lt;T&gt;) =&gt; T | 是 | 一个接受四个参数的函数，用于对每个元素执行操作，并将结果作为累加值传递给下一个元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 回调函数执行后的最终结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## reduce

```TypeScript
reduce<U>(
      callbackFn: (previousValue: U, currentValue: T, currentIndex: number, array: Array<T>) => U,
      initialValue: U
    ): U
```

与前一个API类似，此API接受一个初始值作为第二个参数，用于在Array遍历开始前
初始化累加器。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (previousValue: U, currentValue: T, currentIndex: number, array: Array&lt;T&gt;) =&gt; U | 是 | 一个接受四个参数的函数，用于对每个元素执行操作，并将结果作为累加值传递给下一个元素。 |
| initialValue | U | 是 | 用于初始化累加器的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| U | 回调函数执行后的最终结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## reduceRight

```TypeScript
reduceRight<U = T>(callbackFn: ArrayReduceCallback<U, T, Array<T>>, initialValue: U): U
```

此API与
[reduceRight](arkts-arkts-array-c.md#reduceright-2)方法类似，
但它接受一个初始值作为第二个参数，用于在Array从右到左顺序遍历开始前初始化累加器。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | ArrayReduceCallback&lt;U, T, Array&lt;T&gt;&gt; | 是 | 一个接受四个参数的函数，用于对每个元素执行操作，并将结果作为累加值传递给下一个元素。 |
| initialValue | U | 是 | 用于初始化累加器的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| U | 回调函数执行后的最终结果。可能的原因：1.必填参数未指定。2.参数类型不正确。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduceRight method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## reduceRight

```TypeScript
reduceRight(callbackFn: ArrayReduceCallback<T, T, Array<T>>): T
```

对ArkTS Array中的每个元素按照从右到左顺序执行回调函数，将其结果作为累加值，
并返回最终的值。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | ArrayReduceCallback&lt;T, T, Array&lt;T&gt;&gt; | 是 | 一个接受四个参数的函数，用于对每个元素执行操作，并将结果作为累加值传递给下一个元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 回调函数执行后的最终结果。可能的原因：1.必填参数未指定。2.参数类型不正确。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reduceRight method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## reverse

```TypeScript
reverse(): Array<T>
```

反转ArkTS Array数组中的元素，并返回同一数组的引用。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 反转后的ArkTS Array对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The reverse method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## shift

```TypeScript
shift(): T | undefined
```

从ArkTS Array中移除并返回第一个元素。如果Array为空，则返回**undefined**，
且Array不发生变化。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 从Array中移除的元素；如果Array为空，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The shift method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## shrinkTo

```TypeScript
shrinkTo(arrayLength: number): void
```

使ArkTS Array收缩到指定长度。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arrayLength | number | 是 | Array的新长度。如果传入的值大于或等于当前Array的长度，Array不发生变化。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The shrinkTo method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## slice

```TypeScript
slice(start?: number, end?: number): Array<T>
```

选取ArkTS Array中一段范围内的元素创建新数组。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 否 | 开始索引。如果传入负数，则指代start + array.length位置的下标。默认值为0。 |
| end | number | 否 | 结束索引（不包括该元素）。如果传入负数，则指代end + array.length位置的下标。默认值为ArkTS Array的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 包含选取元素的新Array。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The slice method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## some

```TypeScript
some(predicate: ArrayPredicateFn<T, Array<T>>): boolean
```

测试ArkTS Array是否存在满足指定条件的元素。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | ArrayPredicateFn&lt;T, Array&lt;T&gt;&gt; | 是 | 用于测试的断言函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果存在满足指定条件的元素，则返回**true**；否则返回**false**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The some method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## sort

```TypeScript
sort(compareFn?: (a: T, b: T) => number): Array<T>
```

对ArkTS Array进行排序，并返回排序后的Array。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| compareFn | (a: T, b: T) =&gt; number | 否 | 用于确定元素顺序的函数。默认使用升序排序。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 排序后的Array。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The sort method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## splice

```TypeScript
splice(start: number): Array<T>
```

删除Array中指定位置(start)以及之后的所有元素。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 开始索引。如果`-array.length =&lt; start &lt; 0`，则从`start + array.length`开始删除。如果`start &lt; -array.length`，则从0开始删除。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 返回一个新的包含被删除元素的**Array**对象。如果没有元素被删除，返回一个空的**Array**对象。可能的原因：1.必填参数未指定。2.参数类型不正确。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The splice method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## splice

```TypeScript
splice(start: number, deleteCount: number, ...items: T[]): Array<T>
```

删除Array中指定位置的元素，并在同一位置插入新元素。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 开始索引。如果`-array.length =&lt; start &lt; 0`，则从`start + array.length`开始删除。如果`start &lt; -array.length`，则从0开始删除。 |
| deleteCount | number | 是 | 删除元素的个数。 |
| items | T[] | 是 | 从start位置开始插入的新元素。如果未传入，则仅删除Array内的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;T&gt; | 返回一个新的包含被删除元素的**Array**对象。如果没有元素被删除，返回一个空的**Array**对象。可能的原因：1.必填参数未指定。2.参数类型不正确。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The splice method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## toLocaleString

```TypeScript
toLocaleString(): string
```

根据当前应用所在的系统地区获取符合当前文化习惯的字符串表示形式。让每个元素通过自身的
**toLocaleString**方法转换为字符串，然后使用逗号（,）将这些字符串按顺序拼接。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

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

将ArkTS Array转换为字符串。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

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

## unshift

```TypeScript
unshift(...items: T[]): number
```

在ArkTS Array的首端插入元素，并返回新的Array长度。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | T[] | 是 | 要插入到Array首端的元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 新Array的长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The unshift method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## values

```TypeScript
values(): IterableIterator<T>
```

返回一个迭代器对象，该对象包含ArkTS Array中每个元素的值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;T&gt; | 包含Array中每个元素的值的迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## index

```TypeScript
[index: number]: T
```

返回Array中指定索引位置的元素。

**类型：** T

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## length

```TypeScript
readonly length: number
```

ArkTS Array的元素个数。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

