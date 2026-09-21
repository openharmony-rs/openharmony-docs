# LRUCache

```TypeScript
class LRUCache<K, V>
```

Provides APIs to discard the least recently used data to make rooms for new elements when the cache is full. This class uses the Least Recently Used (LRU) algorithm, which believes that the recently used data may be accessed again in the near future and the least accessed data is the least valuable data and should be removed from the cache.

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[K, V]>
```

Specifies the default iterator for an object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[K, V]&gt; | Returns a two - dimensional array in the form of key - value pairs. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.put(3, 15);

for (let value of pro) {
  console.info(value[0]+ ', '+ value[1]);
}
// Output:
// 2, 10
// 3, 15
```

## afterRemoval

```TypeScript
afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void
```

Performs subsequent operations after a value is removed. The subsequent operations must be implemented by developers. This API is called during deletion operations, such as [get&lt;sup&gt;9+&lt;/sup&gt;](#get), [put&lt;sup&gt;9+&lt;/sup&gt;](#put), [remove&lt;sup&gt;9+&lt;/sup&gt;](#remove), [clear&lt;sup&gt;9+&lt;/sup&gt;](#clear), and [updateCapacity&lt;sup&gt;9+&lt;/sup&gt;](#updatecapacity).

> **NOTE:** 
> 
> If the callback method is executed after [clear&lt;sup&gt;9+&lt;/sup&gt;](#clear) and
> [updateCapacity&lt;sup&gt;9+&lt;/sup&gt;](#updatecapacity) are called and the input **key** and
> **value** parameters are of the MapIterator type, perform subsequent operations by referring to example 2.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEvict | boolean | Yes | Whether the capacity is insufficient. If the value is **true**, this API is called due to insufficient capacity. |
| key | K | Yes | Key removed. |
| value | V | Yes | Value removed. |
| newValue | V | Yes | New value for the key if the **put()** method is called and the key to be added already exists. In other cases, this parameter is left blank. |

## clear

```TypeScript
clear(): void
```

Clears key-value pairs from this cache.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result = pro.length;
pro.clear();
let res = pro.length;
console.info('result = ' + result);
console.info('res = ' + res);
// Output: result = 1
// Output: res = 0
```

## constructor

```TypeScript
constructor(capacity?: number)
```

A constructor used to create a **LRUCache** instance. The default capacity of the cache is 64.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capacity | number | No | Capacity of the cache to create. The default value is **64**, and the maximum value is **2147483647**.<br>**Since:** 12 |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
```

## contains

```TypeScript
contains(key: K): boolean
```

Checks whether this cache contains the specified key.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the cache contains the specified key; otherwise, **false** is returned. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result = pro.contains(2);
console.info('result = ' + result);
// Output: result = true
```

## createDefault

```TypeScript
createDefault(key: K): V
```

Performs subsequent operations if no key is matched in the cache and returns the value (**undefined** by default) associated with the key.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key. |

**Return value:**

| Type | Description |
| --- | --- |
| V | Value of the key. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
let result = pro.createDefault(50);
console.info('result = ' + result);
// Output: result = undefined
```

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

Returns an iterator object that traverses all key-value pairs ([key, value]) in this object in the insertion order.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[K, V]&gt; | Iterable array. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.put(3, 15);
let pair = pro.entries();
for (let value of pair) {
  console.info(value[0]+ ', '+ value[1]);
}
// Output:
// 2, 10
// 3, 15
```

## get

```TypeScript
get(key: K): V | undefined
```

Obtains the value of a key. If the key is not in the cache, [createDefault&lt;sup&gt;9+&lt;/sup&gt;](#createdefault) is called to create the key. If the value specified in **createDefault** is not **undefined**, [afterRemoval&lt;sup&gt;9+&lt;/sup&gt;](#afterremoval) is called to return the value specified in **createDefault**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key based on which the value is queried. |

**Return value:**

| Type | Description |
| --- | --- |
| V &#124; undefined | Value of the key. If no match is found, the value specified in **createDefault** is returned. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result  = pro.get(2);
console.info('result = ' + result);
// Output: result = 10
```

## getCapacity

```TypeScript
getCapacity(): number
```

Obtains the capacity of this cache.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Capacity of the cache. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
let result = pro.getCapacity();
console.info('result = ' + result);
// Output: result = 64
```

## getCreateCount

```TypeScript
getCreateCount(): number
```

Obtains the number of times that an object is created.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of times that objects are created. |

**Examples**

```TypeScript
// Create the ChildLRUCache class that inherits LRUCache, and override createDefault() to return a non-undefined value.
class ChildLRUCache extends util.LRUCache<number, number> {
  constructor() {
    super();
  }

  createDefault(key: number): number {
    return key;
  }
}
let lru = new ChildLRUCache();
lru.put(2, 10);
lru.get(3);
lru.get(5);
let res = lru.getCreateCount();
console.info('res = ' + res);
// Output: res = 2
```

## getMatchCount

```TypeScript
getMatchCount(): number
```

Obtains the number of times that the queried values are matched.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of times that the queried values are matched. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.get(2);
let result = pro.getMatchCount();
console.info('result = ' + result);
// Output: result = 1
```

## getMissCount

```TypeScript
getMissCount(): number
```

Obtains the number of times that the queried values are mismatched.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of times that the queried values are mismatched. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.get(2);
let result = pro.getMissCount();
console.info('result = ' + result);
// Output: result = 0
```

## getPutCount

```TypeScript
getPutCount(): number
```

Obtains the number of additions to this cache.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of additions to the cache. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result = pro.getPutCount();
console.info('result = ' + result);
// Output: result = 1
```

## getRemovalCount

```TypeScript
getRemovalCount(): number
```

Obtains the number of times that key-value pairs in the cache are recycled.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of times that key-value pairs in the cache are recycled. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.updateCapacity(2);
pro.put(50, 22);
let result = pro.getRemovalCount();
console.info('result = ' + result);
// Output: result = 0
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

Checks whether this cache is empty.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the cache does not contain any value. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result = pro.isEmpty();
console.info('result = ' + result);
// Output: result = false
```

## keys

```TypeScript
keys(): K[]
```

Obtains all keys in this cache, listed from the least to the most recently accessed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| K[] | The list of all keys in this cache, listed from the least to the most recently accessed. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, string>();
pro.put(1, 'A');
pro.put(2, "B");
pro.put(3, 'C');
pro.put(4, 'D')
pro.put(5, 'E')
pro.put(6, 'F')
let result = pro.keys();
console.info('result = ' + result);
// Output: result = 1,2,3,4,5,6
pro.get(5);
pro.get(3);
result = pro.keys();
console.info('result = ' + result);
// Output: result = 1,2,4,6,5,3
```

## put

```TypeScript
put(key: K, value: V): V
```

Adds a key-value pair to this cache and returns the value associated with the key. If the total number of values in the cache is greater than the specified capacity, the deletion operation is performed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key of the key-value pair to add. |
| value | V | Yes | Value of the key-value pair to add. |

**Return value:**

| Type | Description |
| --- | --- |
| V | Value of the key-value pair added. If the key or value is empty, an exception is thrown. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
let result = pro.put(2, 10);
console.info('result = ' + result);
// Output: result = 10
```

## remove

```TypeScript
remove(key: K): V | undefined
```

Removes a key and its associated value from this cache and returns the value associated with the key. If the key does not exist, **undefined** is returned.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key to remove. |

**Return value:**

| Type | Description |
| --- | --- |
| V &#124; undefined | Returns an **Optional** object containing the removed key-value pair if the key exists in the cache; returns **undefined** if the key does not exist; throws an error if **null** is passed in for **key**. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
let result = pro.remove(20);
console.info('result = ' + result);
// Output: result = undefined
```

## toString

```TypeScript
toString(): string
```

Obtains the string representation of this cache.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | String representation of this cache. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.put(2, 10);
pro.get(2);
pro.get(3);
console.info(pro.toString());
// Output: LRUCache[ maxSize = 64, hits = 1, misses = 1, hitRate = 50% ]
// maxSize: maximum size of the cache. hits: number of matched queries. misses: number of mismatched queries. hitRate: matching rate.
```

## updateCapacity

```TypeScript
updateCapacity(newCapacity: number): void
```

Changes the cache capacity. If the new capacity is less than or equal to **0**, an exception will be thrown. If the total number of values in the cache is greater than the specified capacity, the deletion operation is performed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newCapacity | number | Yes | New capacity of the cache. The maximum value is **2147483647**. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, number>();
pro.updateCapacity(100);
```

## values

```TypeScript
values(): V[]
```

Obtains all values in this cache, listed from the least to the most recently accessed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| V[] | The list of all values in this cache, listed from the least to the most recently accessed. |

**Examples**

```TypeScript
let pro = new util.LRUCache<number, string>();
pro.put(1, 'A');
pro.put(2, "B");
pro.put(3, 'C');
pro.put(4, 'D')
pro.put(5, 'E')
pro.put(6, 'F')
let result = pro.values();
console.info('result = ' + result);
// Output: result = A,B,C,D,E,F
pro.get(1);
pro.get(2);
result = pro.values();
console.info('result = ' + result);
// Output: result = C,D,E,F,A,B
```

## length

```TypeScript
length: number
```

Total number of values in this cache.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
