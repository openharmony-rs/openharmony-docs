# Map

一种基于键值对存储的非线性数据结构。

> **说明**
>
> - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。
> 本节使用以下标识符来表示泛型的使用：

- K：键。
- V：值。
K和V类型都需为
[Sendable支持的数据类型](../../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。
**装饰器类型**：\@Sendable

**起始版本：** 12

**装饰器类型：** @Sendable

**系统能力：** SystemCapability.Utils.Lang

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[K, V]>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。
说明：
本接口不支持在.ets文件中使用。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | 返回一个迭代器对象，该对象包含键值对。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The Symbol.iterator method cannot be bound. |

## clear

```TypeScript
clear(): void
```

删除该Map中的所有元素。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The clear method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## constructor

```TypeScript
constructor(entries?: readonly (readonly [K, V])[] | null)
```

构造函数，用于创建ArkTS Map对象。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entries | readonly (readonly [K, V])[] \| null | 否 | 键值对数组或其它可迭代对象。默认值为**null**，创建一个空Map对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The ArkTS Map's constructor cannot be directly invoked. |

## constructor

```TypeScript
constructor(iterable: Iterable<readonly [K, V]>)
```

创建ArkTS Map对象的构造函数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iterable | Iterable&lt;readonly [K, V]&gt; | 是 | 用于构造ArkTS Map的对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The ArkTS Map's constructor cannot be directly invoked. |

## delete

```TypeScript
delete(key: K): boolean
```

删除该Map中指定元素。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 待删除元素的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作结果。如果元素存在并已被删除，则返回**true**；否则该元素不存在，返回**false**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The delete method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

返回一个Map迭代器对象，该对象包含了此Map中的每个元素的[key, value]对。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | Map迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## forEach

```TypeScript
forEach(callbackFn: (value: V, key: K, map: Map<K, V>) => void): void
```

按插入顺序对该Map中的每个键/值对执行一次回调函数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: V, key: K, map: Map&lt;K, V&gt;) =&gt; void | 是 | 对每个键值对运行的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## get

```TypeScript
get(key: K): V | undefined
```

返回该Map中的指定元素。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | 与指定键相关联的元素，如果键在Map对象中找不到，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The get method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## has

```TypeScript
has(key: K): boolean
```

判断该Map中是否存在指定元素。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 待查找元素的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判断结果。如果存在指定元素，则返回**true**，否则返回**false**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The has method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## keys

```TypeScript
keys(): IterableIterator<K>
```

返回一个Map迭代器对象，该对象包含了此Map中每个元素的键。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;K&gt; | Map迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The keys method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## set

```TypeScript
set(key: K, value: V): Map<K, V>
```

向该Map添加或更新一个指定的键值对。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 添加或更新指定元素的键。 |
| value | V | 是 | 添加或更新指定元素的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Map&lt;K, V&gt; | 新的Map对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The set method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## values

```TypeScript
values(): IterableIterator<V>
```

返回一个Map迭代器对象，该对象包含此Map中每个元素的值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;V&gt; | Map迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The values method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## size

```TypeScript
readonly size: number
```

Map的元素个数。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

