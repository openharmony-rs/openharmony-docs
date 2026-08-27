# Map

一种基于键值对存储的非线性数据结构，能够高效地通过唯一键来存取对应的值。

> **说明：**
> 
> - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。
> 本节使用以下标识符来表示泛型的使用：
- K：Key，键。
- V：Value，值。
K和V类型都需为 [Sendable支持的数据类型](../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。 **装饰器类型**：\@Sendable

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[K, V]>
```

返回一个迭代器，迭代器的每一项都是一个JavaScript对象。 说明： 本接口不支持在.ets文件中使用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator & lt;[K, V] & gt; | 返回一个迭代器对象，该对象包含键值对。 |

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entries | readonly (readonly [K, V])[] \| null | 否 | 键值对数组或其它可迭代对象。 默认值为**null**，创建一个空Map对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The ArkTS Map's constructor cannot be directly invoked. |

## constructor

```TypeScript
constructor(iterable: Iterable<readonly [K, V]>)
```

构造函数，用于通过可迭代对象创建ArkTS Map对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iterable | Iterable & lt;readonly [K, V] & gt; | 是 | 用于构造ArkTS Map的可迭代对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-构造函数调用异常) | The ArkTS Map's constructor cannot be directly invoked. |

## containsValue

```TypeScript
containsValue(value: V): boolean
```

判断该Map中是否存在一个或多个键映射到指定值。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | V | 是 | 指定值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果存在指定值，则返回**true**；否则返回 **false**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The containsValue method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification exception |

## delete

```TypeScript
delete(key: K): boolean
```

删除该Map中指定键对应的元素。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 待删除元素的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作结果。如果元素存在并已被删除，则返回**true**； 否则该元素不存在，返回**false**。 |

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator & lt;[K, V] & gt; | Map迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The entries method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## forEach

```TypeScript
forEach(callbackFn: (value: V, key: K, map: Map<K, V>) => void): void
```

按插入顺序对该Map中的每个键值对执行一次回调函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: V, key: K, map: Map & lt;K, V & gt;) = & gt; void | 是 | 对每个键值对运行的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The forEach method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## get

```TypeScript
get(key: K): V | undefined
```

返回该Map中指定键对应的元素。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要获取值的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V \| undefined | 与指定键相关联的元素，如果键在Map对象中找不到，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The get method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## has

```TypeScript
has(key: K): boolean
```

判断该Map中是否存在指定键。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 待查找元素的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判断结果。如果存在指定元素，则返回**true**，否则返回 **false**。 |

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator & lt;K & gt; | Map迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The keys method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## put

```TypeScript
put(key: K, value: V): V | undefined
```

向该Map添加或更新一个指定的键值对，并返回该键之前关联的值。

> **NOTE：**
> 
> - 返回**undefined**时无法直接区分是键不存在还是键存在但值为**undefined**，可在使用本接口前先使用
> **has**接口判断键是否存在，进而区分返回的**undefined**所属情况。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 添加或更新指定元素的键。 |
| value | V | 是 | 添加或更新指定元素的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V \| undefined | 该键之前关联的值。如果键在Map对象中找不到，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The put method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification exception |

## putAll

```TypeScript
putAll(from: Map<K, V>): void
```

使用指定ArkTS Map中的键值对更新该Map。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | Map & lt;K, V & gt; | 是 | 提供键值对的ArkTS Map。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The putAll method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification exception |

## putAll

```TypeScript
putAll(from: BuiltinMap<K, V>): void
```

使用指定内建Map中的键值对更新该Map。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | [BuiltinMap](arkts-arkts-builtinmap-t.md)&lt;K, V&gt; | 是 | 提供键值对的内建Map。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The putAll method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification exception |

## remove

```TypeScript
remove(key: K): V | undefined
```

删除该Map中的指定键及其对应值。

> **NOTE：**
> 
> - 返回**undefined**时无法直接区分是键不存在还是键存在但值为**undefined**，可在使用本接口前先使用
> **has**接口判断键是否存在，进而区分返回的**undefined**所属情况。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 指定键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V \| undefined | 被删除的值。如果键在Map对象中找不到，则返回**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The remove method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification exception |

## set

```TypeScript
set(key: K, value: V): Map<K, V>
```

向该Map添加或更新一个指定的键值对。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | 要添加或更新的键。 |
| value | V | 是 | 要添加或更新的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Map & lt;K, V & gt; | 添加或更新键值对操作后的Map对象本身。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | The set method cannot be bound with non-sendable. |
| [10200201](../errorcode-utils.md#10200201-concurrent修改错误) | Concurrent modification error. |

## values

```TypeScript
values(): IterableIterator<V>
```

返回一个Map迭代器对象，该对象包含了此Map中每个元素的值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator & lt;V & gt; | Map迭代器对象。 |

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
