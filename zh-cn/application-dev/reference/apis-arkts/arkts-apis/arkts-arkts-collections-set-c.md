# Set

一种非线性数据结构。

> **说明**  
>  
> - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  
> 本节使用以下标识来表示泛型的使用：

- T：Type，支持[Sendable支持的数据类型](../../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。**装饰器类型：** \@Sendable

**起始版本：** 12

**装饰器类型：** @Sendable

<!--Device-collections-class Set<T>--><!--Device-collections-class Set<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { collections } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。说明：本接口不支持在.ets文件中使用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-[Symbol.iterator](): IterableIterator<T>--><!--Device-Set-[Symbol.iterator](): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<T> | 迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

## add

```TypeScript
add(value: T): Set<T>
```

检查此Set中是否存在指定值，如果不存在，则将该值添加到Set中。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-add(value: T): Set<T>--><!--Device-Set-add(value: T): Set<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 目标值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Set](arkts-arkts-collections-set-c.md)<T> | Set对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The add method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## clear

```TypeScript
clear(): void
```

删除此Set中的所有元素。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-clear(): void--><!--Device-Set-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## constructor

```TypeScript
constructor(values?: readonly T[] | null)
```

构造函数，用于创建ArkTS Set对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-constructor(values?: readonly T[] | null)--><!--Device-Set-constructor(values?: readonly T[] | null)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | readonly T[] \| null | 否 | 数组或其它可迭代对象。默认值为**null**，表示创建一个空Set对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The ArkTS Set's constructor cannot be directly invoked. |

## constructor

```TypeScript
constructor(iterable: Iterable<T>)
```

创建ArkTS Set对象的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-constructor(iterable: Iterable<T>)--><!--Device-Set-constructor(iterable: Iterable<T>)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iterable | Iterable<T> | 是 | 用于构造ArkTS Set的对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The ArkTS Set's constructor cannot be directly invoked. |

## delete

```TypeScript
delete(value: T): boolean
```

删除此Set中的指定元素。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-delete(value: T): boolean--><!--Device-Set-delete(value: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 目标值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作结果。成功删除返回**true**，否则返回**false**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The delete method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## entries

```TypeScript
entries(): IterableIterator<[T, T]>
```

返回一个Set迭代器对象，该对象包含了此Set中每个元素的键值对。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-entries(): IterableIterator<[T, T]>--><!--Device-Set-entries(): IterableIterator<[T, T]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<[T, T]> | 返回一个Set迭代器对象，该对象包含了此Set中每个元素的键值对。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## forEach

```TypeScript
forEach(callbackFn: (value: T, value2: T, set: Set<T>) => void): void
```

对此Set中的每个键值对执行一次回调函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-forEach(callbackFn: (value: T, value2: T, set: Set<T>) => void): void--><!--Device-Set-forEach(callbackFn: (value: T, value2: T, set: Set<T>) => void): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: T, value2: T, set: Set<T>) => void | 是 | 对每个键值对运行的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## has

```TypeScript
has(value: T): boolean
```

判断此Set中是否存在指定值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-has(value: T): boolean--><!--Device-Set-has(value: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 目标键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果存在指定元素，则返回**true**，否则返回**false**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## keys

```TypeScript
keys(): IterableIterator<T>
```

返回一个Set迭代器对象，该对象包含了此Set中每个元素的键。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-keys(): IterableIterator<T>--><!--Device-Set-keys(): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<T> | 返回一个Set迭代器对象，该对象包含了此Set中每个元素的键。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The keys method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## values

```TypeScript
values(): IterableIterator<T>
```

返回一个Set迭代器对象，该对象包含了此Set中每个元素的值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-values(): IterableIterator<T>--><!--Device-Set-values(): IterableIterator<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator<T> | 返回一个Set迭代器对象，该对象包含了此Set中每个元素的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## size

```TypeScript
readonly size: number
```

Set的元素个数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Set-readonly size: number--><!--Device-Set-readonly size: number-End-->

**系统能力：** SystemCapability.Utils.Lang

