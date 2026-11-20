# Class (SendableLruCache)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=b2f3b26f12a87ac1d194c003c5395a708b430ee0 translatedAt=2026-11-06T09:06:36.433Z pushedAt=2026-11-13T03:36:52.467Z nl=1 -->

When the cache space is insufficient, SendableLruCache replaces the least recently used data with new data. This design is based on resource access considerations: data accessed recently may be accessed again in the near future, so the least accessed data has the least value and should be evicted from the cache first. SendableLruCache supports the Sendable feature (which allows safe cross-thread sharing) and can store Sendable objects, ensuring safe cross-thread access.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The initial APIs of SendableLruCache are supported since API version 18.
>
> This module can be imported and used only in ArkTS files (with the .ets file name extension).
> 

**Decorator**: \@Sendable

## Modules to Import

```ts
import { ArkTSUtils } from '@kit.ArkTS';
```

## Properties

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

| Name  | Type  | Read-Only| Optional| Description                  |
| ------ | ------ | ---- | ---- | ---------------------- |
| length<sup>18+</sup> | number | Yes   | No   | Total number of values in the current cache. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
lruCache.put(1, 8);
let result = lruCache.length;
console.info(`result = ${result}`);
// Expected output: result = 2
```

## constructor<sup>18+</sup>

constructor(capacity?: number)

A constructor used to create a **SendableLruCache** instance. The default capacity of the cache is 64.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type  | Mandatory| Description                        |
| -------- | ------ | ---- | ---------------------------- |
| capacity | number | No | Indicates the custom capacity of the cache. If not passed, the default value is 64, and the maximum value cannot exceed 2147483647. An exception is thrown when the value is less than or equal to 0. It is recommended that you set an appropriate capacity value based on the actual amount of service data to balance the cache hit rate and memory usage. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
```

## updateCapacity<sup>18+</sup>

updateCapacity(newCapacity: number): void

Sets the cache capacity to the specified value. If the total number of values in the cache exceeds the specified capacity, the least recently used key-value pairs will be evicted.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name     | Type  | Mandatory| Description                        |
| ----------- | ------ | ---- | ---------------------------- |
| newCapacity | number | Yes | Indicates the capacity to customize for the cache. The maximum value cannot exceed 2147483647. An exception is thrown when the value is less than or equal to 0. It is recommended to set an appropriate capacity value based on the actual business data volume to balance the cache hit rate and memory usage. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.updateCapacity(100);
```

## toString<sup>18+</sup>

toString(): string

Returns the string representation of the object, including information such as the maximum cache capacity, the number of successful query matches, the number of failed query matches, and the match rate.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description                      |
| ------ | -------------------------- |
| string | Returns the string representation of the object. The returned string format is: SendableLruCache[ maxSize = (maxSize), hits = (hitCount), misses = (missCount), hitRate = (hitRate) ]. (maxSize) indicates the maximum cache size, (hitCount) indicates the number of times a query value matched successfully, (missCount) indicates the number of times a query value failed to match, and (hitRate) indicates the query value match rate.|

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
lruCache.get(2);
lruCache.get(3);
console.info(lruCache.toString());
// Expected output: SendableLruCache[ maxSize = 64, hits = 1, misses = 1, hitRate = 50% ]
// maxSize: maximum cache size hits: number of successful query matches misses: number of failed query matches hitRate: query match rate
```

## getCapacity<sup>18+</sup>

getCapacity(): number

Obtains the current cache capacity.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description                  |
| ------ | ---------------------- |
| number | Returns the current cache capacity. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
let result = lruCache.getCapacity();
console.info(`result = ${result}`);
// Expected output: result = 64
```

## clear<sup>18+</sup>

clear(): void

Clears all key-value pairs from the current cache.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
let result = lruCache.length;
lruCache.clear();
let res = lruCache.length;
console.info(`result = ${result}`);
console.info(`res = ${res}`);
// Expected output: result = 1
// Expected output: res = 0
```

## getCreateCount<sup>18+</sup>

getCreateCount(): number

Obtains the number of times objects are created by calling the createDefault method.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description               |
| ------ | -------------------|
| number | Return the number of times objects are created using the createDefault method. |

**Example**

```ts
@Sendable
class ChildLRUCache extends ArkTSUtils.SendableLruCache<number, number> {
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
console.info(`res = ${res}`);
// Expected output: res = 2
// When the get operation is performed, if the key does not exist, call the createDefault API to check whether the return value is undefined.
// If the return value is not undefined, add the key and return value to the cache as a new entry and increase the creation count by one.
```

## getMissCount<sup>18+</sup>

getMissCount(): number

Obtains the number of times that the queried values are mismatched.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| number | Number of times that the queried values are mismatched.|

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
lruCache.get(2);
let result = lruCache.getMissCount();
console.info(`result = ${result}`);
// Expected output: result = 0
```

## getRemoveCount<sup>18+</sup>

getRemoveCount(): number

Obtains the number of evictions of cache key-value pairs. When the number of cached items exceeds the capacity limit, the least recently used key-value pairs will be evicted.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description                      |
| ------ | -------------------------- |
| number | Returns the number of times cache key-value pairs have been evicted. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
lruCache.updateCapacity(2);
lruCache.put(50, 22);
let result = lruCache.getRemoveCount();
console.info(`result = ${result}`);
// Expected output: result = 0
```

## getMatchCount<sup>18+</sup>

getMatchCount(): number

Obtains the number of times that the queried values are matched.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description                      |
| ------ | -------------------------- |
| number | Number of times that the queried values are matched.|

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
lruCache.get(2);
let result = lruCache.getMatchCount();
console.info(`result = ${result}`);
// Expected output: result = 1
```

## getPutCount<sup>18+</sup>

getPutCount(): number

Obtains the number of times values have been added to the cache.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type  | Description                        |
| ------ | ---------------------------- |
| number | Return the number of times a value is added to the cache. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
let result = lruCache.getPutCount();
console.info(`result = ${result}`);
// Expected output: result = 1
```

## isEmpty<sup>18+</sup>

isEmpty(): boolean

Checks whether the current cache is empty.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type   | Description                                    |
| ------- | ---------------------------------------- |
| boolean | Returns true if the current cache is empty and contains no key-value pairs; returns false if the current cache is not empty. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
let result = lruCache.isEmpty();
console.info('result = ' + result);
// Expected output: result = false
```

## get<sup>18+</sup>

get(key: K): V | undefined

Returns the value corresponding to the key. If the specified key does not exist in the cache, the createDefault method is called; if createDefault returns a non-undefined value, the key-value pair is added to the cache and the value is returned; if createDefault returns undefined, undefined is returned.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description        |
| ------ | ---- | ---- | ------------ |
| key    | K    | Yes  | Key based on which the value is queried.|

**Return value**

| Type                    | Description                                                        |
| ------------------------ | ------------------------------------------------------------ |
| V \| undefined | If the specified key exists in the cache, returns the value associated with the key; otherwise, calls the createDefault method to create a value. If createDefault returns a non-undefined value, adds the key-value pair to the cache and returns that value; if createDefault returns undefined, ultimately returns undefined. When the number of values in the cache exceeds the capacity due to adding a new entry, the least recently used key-value pair is evicted. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
let result  = lruCache.get(2);
console.info(`result = ${result}`);
// Expected output: result = 10
```

## put<sup>18+</sup>

put(key: K, value: V): V

Adds a key-value pair to the cache and returns the value associated with the added key. When the number of values in the cache exceeds the capacity, the least recently used key-value pair is evicted.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description                      |
| ------ | ---- | ---- | -------------------------- |
| key    | K    | Yes  | Key of the key-value pair to add.            |
| value  | V    | Yes  | Value of the key-value pair to add.|

**Return value**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| V    | Value of the key-value pair added.|

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
let result = lruCache.put(2, 10);
console.info(`result = ${result}`);
// Expected output: result = 10
```

## values<sup>18+</sup>

values(): V[]

Obtains a list of all values in the current cache, arranged in order from most recently accessed to least recently accessed.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type     | Description                                                        |
| --------- | ------------------------------------------------------------ |
| V&nbsp;[] | Returns a list of all values in the current cache, arranged in order from most recently accessed to least recently accessed. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number|string,number|string>();
lruCache.put(2, 10);
lruCache.put(2, "anhu");
lruCache.put("afaf", "grfb");
let result = lruCache.values();
console.info(`result = ${result}`);
// Expected output: result = anhu,grfb
```

## keys<sup>18+</sup>

keys(): K[]

Obtains all keys in the current cache, arranged in order from most recently accessed to least recently accessed.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type     | Description                                                        |
| --------- | ------------------------------------------------------------ |
| K&nbsp;[] | Returns a list of all keys in the current cache, ordered from most recently accessed to least recently accessed. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
lruCache.put(3, 1);
let result = lruCache.keys();
console.info(`result = ${result}`);
// Expected output: result = 2,3
```

## remove<sup>18+</sup>

remove(key: K): V | undefined

Removes the specified key and its associated value from the current cache, and returns the value associated with the key. If the key does not exist, undefined is returned.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description          |
| ------ | ---- | ---- | -------------- |
| key    | K    | Yes   | Key to delete. |

**Return value**

| Type                    | Description                                                        |
| ------------------------ | ------------------------------------------------------------ |
| V&nbsp;\|&nbsp;undefined | Return the value associated with the key; if the key does not exist, return undefined. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
let result = lruCache.remove(20);
console.info(`result = ${result}`);
// Expected output: result = undefined
```

## contains<sup>18+</sup>

contains(key: K): boolean

Checks whether the current cache contains the specified key. If it exists, true is returned; otherwise, false is returned.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| key    | K      | Yes  | Key to check.|

**Return value**

| Type   | Description                                      |
| ------- | ------------------------------------------ |
| boolean | true: the cache contains the specified key; false: the cache does not contain the specified key. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
let result = lruCache.contains(2);
console.info(`result = ${result}`);
// Expected output: result = true
```

## entries<sup>18+</sup>

entries(): IterableIterator&lt;[K,V]&gt;

Allows iteration over all key-value pairs contained in this object, arranged in order from most recently accessed to least recently accessed.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type       | Description                |
| ----------- | -------------------- |
| IterableIterator<[K,&nbsp;V]> | Return an iterator of key-value pairs. |

**Example**

```ts
let lruCache = new ArkTSUtils.SendableLruCache<number, number>();
lruCache.put(2, 10);
lruCache.put(3, 15);
let pair:Iterable<[number, number]> = lruCache.entries();
let arrayValue = Array.from(pair);
for (let value of arrayValue) {
  console.info(`${value[0]}, ${value[1]}`);
  // Expected output:
  // 2, 10
  // 3, 15
}
```