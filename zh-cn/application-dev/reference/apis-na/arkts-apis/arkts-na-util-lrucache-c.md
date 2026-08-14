# LRUCache

Provides APIs to discard the least recently used data to make rooms for new elements when the cache is full. This class uses the Least Recently Used (LRU) algorithm, which believes that the recently used data may be accessed again in the near future and the least accessed data is the least valuable data and should be removed from the cache.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-util-class LRUCache--><!--Device-util-class LRUCache-End-->

**系统能力：** SystemCapability.Utils.Lang

## $_iterator

```TypeScript
$_iterator(): IterableIterator<[K, V]>
```

Specifies the default iterator for an object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-$_iterator(): IterableIterator<[K, V]>--><!--Device-LRUCache-$_iterator(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | Returns a two - dimensional array in the form of key - value pairs. |

## afterRemoval

```TypeScript
afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void
```

Executes subsequent operations after a value is deleted.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void--><!--Device-LRUCache-afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEvict | boolean | 是 | The parameter value is true if this method is called due to insufficient capacity, and the parameter value is false in other cases. |
| key | K | 是 | Indicates the deleted key. |
| value | V | 是 | Indicates the deleted value. |
| newValue | V | 是 | The parameter value is the new value associated if the put(java.lang.Object,java.lang.Object) method is called and the key to add already exists. The parameter value is null in other cases. |

## clear

```TypeScript
clear(): void
```

Clears key-value pairs from the current buffer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-clear(): void--><!--Device-LRUCache-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(capacity?: int)
```

Default constructor used to create a new LruBuffer instance with the default capacity of 64.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-constructor(capacity?: int)--><!--Device-LRUCache-constructor(capacity?: int)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capacity | int | 否 | Indicates the capacity to customize for the buffer. |

## contains

```TypeScript
contains(key: K): boolean
```

Checks whether the current buffer contains a specified key.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-contains(key: K): boolean--><!--Device-LRUCache-contains(key: K): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | Indicates the key to check. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the buffer contains the specified key. |

## createDefault

```TypeScript
createDefault(key: K): V | undefined
```

Executes subsequent operations if miss to compute a value for the specific key.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-createDefault(key: K): V | undefined--><!--Device-LRUCache-createDefault(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | Indicates the missed key. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | Returns the value associated with the key. |

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

Returns an array of key-value pairs of enumeratable properties of a given object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-entries(): IterableIterator<[K, V]>--><!--Device-LRUCache-entries(): IterableIterator<[K, V]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, V]&gt; | Returns an array of key-value pairs for the enumeratable properties of the given object itself. |

## get

```TypeScript
get(key: K): V | undefined
```

Obtains the value associated with a specified key.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-get(key: K): V | undefined--><!--Device-LRUCache-get(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | Indicates the key to query. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | Returns the value associated with the key if the specified key is present in the buffer; returns null otherwise. |

## getCapacity

```TypeScript
getCapacity(): int
```

Obtains the capacity of the current buffer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-getCapacity(): int--><!--Device-LRUCache-getCapacity(): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Returns the capacity of the current buffer. |

## getCreateCount

```TypeScript
getCreateCount(): long
```

Obtains the number of times createDefault(Object) returned a value.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-getCreateCount(): long--><!--Device-LRUCache-getCreateCount(): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | Returns the number of times createDefault(java.lang.Object) returned a value. |

## getMatchCount

```TypeScript
getMatchCount(): long
```

Obtains the number of times that the queried values are successfully matched.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-getMatchCount(): long--><!--Device-LRUCache-getMatchCount(): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | Returns the number of times that the queried values are successfully matched. |

## getMissCount

```TypeScript
getMissCount(): long
```

Obtains the number of times that the queried values are not matched.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-getMissCount(): long--><!--Device-LRUCache-getMissCount(): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | Returns the number of times that the queried values are not matched. |

## getPutCount

```TypeScript
getPutCount(): long
```

Obtains the number of times that values are added to the buffer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-getPutCount(): long--><!--Device-LRUCache-getPutCount(): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | Returns the number of times that values are added to the buffer. |

## getRemovalCount

```TypeScript
getRemovalCount(): long
```

Obtains the number of times that values are evicted from the buffer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-getRemovalCount(): long--><!--Device-LRUCache-getRemovalCount(): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | Returns the number of times that values are evicted from the buffer. |

## isEmpty

```TypeScript
isEmpty(): boolean
```

Checks whether the current buffer is empty.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-isEmpty(): boolean--><!--Device-LRUCache-isEmpty(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the current buffer contains no value. |

## keys

```TypeScript
keys(): Array<K>
```

Obtains a list of keys for the values in the current buffer. since 9

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-keys(): Array<K>--><!--Device-LRUCache-keys(): Array<K>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;K&gt; | Returns a list of keys ordered by access time, from the most recently accessed to the least recently accessed. |

## put

```TypeScript
put(key: K, value: V): V | undefined
```

Adds a key-value pair to the buffer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-put(key: K, value: V): V | undefined--><!--Device-LRUCache-put(key: K, value: V): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | Indicates the key to add. |
| value | V | 是 | Indicates the value associated with the key to add. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | Returns the value associated with the added key; returns the original value if the key to add already exists, returns null otherwise. |

## remove

```TypeScript
remove(key: K): V | undefined
```

Deletes a specified key and its associated value from the current buffer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-remove(key: K): V | undefined--><!--Device-LRUCache-remove(key: K): V | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | K | 是 | Indicates the key to delete. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | Returns an Optional object containing the deleted key-value pair; returns an empty Optional object if the key does not exist. |

## toString

```TypeScript
toString(): string
```

Returns a string representation of the object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-toString(): string--><!--Device-LRUCache-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the string representation of the object and outputs the string representation of the object. |

## updateCapacity

```TypeScript
updateCapacity(newCapacity: int): void
```

Updates the buffer capacity to a specified capacity.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-updateCapacity(newCapacity: int): void--><!--Device-LRUCache-updateCapacity(newCapacity: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newCapacity | int | 是 | Indicates the new capacity to set. |

## values

```TypeScript
values(): Array<V>
```

Obtains a list of all values in the current buffer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-LRUCache-values(): Array<V>--><!--Device-LRUCache-values(): Array<V>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;V&gt; | Returns the list of all values in the current buffer, ordered from the most recently accessed to the least recently accessed. |

