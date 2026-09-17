# SendableLruCache

Object used for store least recently used sendable Object.

**Since:** 18

**Decorator:** @Sendable

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## clear

```TypeScript
clear(): void
```

Clear all key-value pairs from the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(capacity?: number)
```

Default constructor.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capacity | number | No | The capacity of the SendableLruCache. |

## contains

```TypeScript
contains(key: K): boolean
```

Check whether the given key exists in the SendableLruCache. If exists, returns true; otherwise, returns false.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | The key to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The result of the checked. |

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

Returns an iterable of key-value pairs for each element in the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[K, V]&gt; | A new iterable iterator object. |

## get

```TypeScript
get(key: K): V | undefined
```

Get the value associated with a specified key in the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | The key to query. |

**Return value:**

| Type | Description |
| --- | --- |
| V &#124; undefined | The value associated with the key if the specified key is present; returns undefined otherwise. |

## getCapacity

```TypeScript
getCapacity(): number
```

Get the Capacity of the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | The Capacity of the SendableLruCache. |

## getCreateCount

```TypeScript
getCreateCount(): number
```

Get the number of times createDefault in the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | The number of times createDefault. |

## getMatchCount

```TypeScript
getMatchCount(): number
```

Get the number of times that the queried values are matched in the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | The number of times that the queried values are matched. |

## getMissCount

```TypeScript
getMissCount(): number
```

Get the number of times that the queried values are not matched in the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | The number of times that the queried values are unmatched. |

## getPutCount

```TypeScript
getPutCount(): number
```

Get the number of times that values are added to SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | The number of times that values are added. |

## getRemoveCount

```TypeScript
getRemoveCount(): number
```

Get the number of times that values are removed from the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | The number of times that values are removed. |

## isEmpty

```TypeScript
isEmpty(): boolean
```

Checks whether the SendableLruCache is empty.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true if the SendableLruCache is empty, otherwise false. |

## keys

```TypeScript
keys(): K[]
```

Returns a list of all keys in the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| K[] | An array of all keys. |

## put

```TypeScript
put(key: K, value: V): V
```

Adds a key-value pair to the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | The key to add. |
| value | V | Yes | The value associated with the key to add. |

**Return value:**

| Type | Description |
| --- | --- |
| V | The value associated with the added key or the original value if the key to add already exists. |

## remove

```TypeScript
remove(key: K): V | undefined
```

Remove a specified key and its associated value from the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | The key to delete. |

**Return value:**

| Type | Description |
| --- | --- |
| V &#124; undefined | The deleted value or undefined. |

## toString

```TypeScript
toString(): string
```

Return the string representation of the object. The returned string format is: SendableLruCache[ maxSize = (maxSize), hits = (hitCount), misses = (missCount), hitRate = (hitRate) ]. (maxSize) represents the maximum size of the cache, (hitCount) indicates the number of successful query matches, (missCount) denotes the number of failed query matches, (hitRate) signifies the query match rate.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | A new string contains all elements. |

## updateCapacity

```TypeScript
updateCapacity(newCapacity: number): void
```

Update the capacity of the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newCapacity | number | Yes | The new capacity of the SendableLruCache. |

## values

```TypeScript
values(): V[]
```

Returns a list of all values in the SendableLruCache.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| V[] | An array of all values. |

## length

```TypeScript
readonly length: number
```

The length of the SendableLruCache.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang
