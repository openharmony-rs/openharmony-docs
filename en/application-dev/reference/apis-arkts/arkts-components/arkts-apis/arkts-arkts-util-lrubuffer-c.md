# LruBuffer

The LruBuffer algorithm replaces the least used data with new data when the buffer space is insufficient.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [LRUCache](arkts-arkts-util-lrucache-c.md)

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

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [Symbol.iterator]

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[K, V]&gt; | Returns a two - dimensional array in the form of key - value pairs. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro[Symbol.iterator]();
```

## afterRemoval

```TypeScript
afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void
```

Performs subsequent operations after a value is removed.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [afterRemoval](arkts-arkts-util-lrucache-c.md#afterremoval)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEvict | boolean | Yes | Whether the capacity is insufficient. If the value is **true**, this API is called due to insufficient capacity. |
| key | K | Yes | Key removed. |
| value | V | Yes | Value removed. |
| newValue | V | Yes | New value for the key if the **put()** method is called and the key to be added already exists. In other cases, this parameter is left blank. |

**Examples**

```TypeScript
class ChildLruBuffer<K, V> extends util.LruBuffer<K, V> {
  constructor(capacity?: number) {
    super(capacity);
  }

  afterRemoval(isEvict: boolean, key: K, value: V, newValue: V): void {
    if (isEvict === true) {
      console.info('key: ' + key);
      // Output: key: 11
      console.info('value: ' + value);
      // Output: value: 1
      console.info('newValue: ' + newValue);
      // Output: newValue: null
    }
  }
}
let lru: ChildLruBuffer<number, number> = new ChildLruBuffer(2);
lru.put(11, 1);
lru.put(22, 2);
lru.put(33, 3);
```

## clear

```TypeScript
clear(): void
```

Clears key-value pairs from this cache. The **afterRemoval()** API will be called to perform subsequent operations.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [clear](arkts-arkts-util-lrucache-c.md#clear)

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.length;
pro.clear();
```

## constructor

```TypeScript
constructor(capacity?: number)
```

A constructor used to create a **LruBuffer** instance. The default capacity of the cache is 64.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** constructor

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capacity | number | No | Capacity of the cache to create. The default value is **64**. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
```

## contains

```TypeScript
contains(key: K): boolean
```

Checks whether this cache contains the specified key.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [contains](arkts-arkts-util-lrucache-c.md#contains)

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
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.contains(20);
console.info('result = ' + result);
// Output: result = false
```

## createDefault

```TypeScript
createDefault(key: K): V
```

Creates a value if the value of the specified key is not available.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [createDefault](arkts-arkts-util-lrucache-c.md#createdefault)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key of which the value is missing. |

**Return value:**

| Type | Description |
| --- | --- |
| V | Value of the key. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
let result = pro.createDefault(50);
```

## entries

```TypeScript
entries(): IterableIterator<[K, V]>
```

Obtains a new iterator object that contains all key-value pairs in this object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [entries](arkts-arkts-util-lrucache-c.md#entries)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[K, V]&gt; | Iterable array. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.entries();
```

## get

```TypeScript
get(key: K): V | undefined
```

Obtains the value of the specified key.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [get](arkts-arkts-util-lrucache-c.md#get)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key based on which the value is queried. |

**Return value:**

| Type | Description |
| --- | --- |
| V &#124; undefined | Value of the key. If no match is found, **undefined** is returned. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result  = pro.get(2);
console.info("result = " + result);
// Output: result = 10
```

## getCapacity

```TypeScript
getCapacity(): number
```

Obtains the capacity of this cache.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getCapacity](arkts-arkts-util-lrucache-c.md#getcapacity)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Capacity of the cache. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
let result = pro.getCapacity();
console.info("result = " + result);
// Output: result = 64
```

## getCreateCount

```TypeScript
getCreateCount(): number
```

Obtains the number of return values for **createDefault()**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getCreateCount](arkts-arkts-util-lrucache-c.md#getcreatecount)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of return values for **createDefault()**. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(1,8);
let result = pro.getCreateCount();
console.info("result = " + result);
// Output: result = 0
```

## getMatchCount

```TypeScript
getMatchCount(): number
```

Obtains the number of times that the queried values are matched.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getMatchCount](arkts-arkts-util-lrucache-c.md#getmatchcount)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of times that the queried values are matched. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
pro.get(2);
let result = pro.getMatchCount();
console.info("result = " + result);
// Output: result = 1
```

## getMissCount

```TypeScript
getMissCount(): number
```

Obtains the number of times that the queried values are mismatched.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getMissCount](arkts-arkts-util-lrucache-c.md#getmisscount)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of times that the queried values are mismatched. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
pro.get(2);
let result = pro.getMissCount();
console.info("result = " + result);
// Output: result = 0
```

## getPutCount

```TypeScript
getPutCount(): number
```

Obtains the number of additions to this cache.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getPutCount](arkts-arkts-util-lrucache-c.md#getputcount)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of additions to the cache. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.getPutCount();
console.info("result = " + result);
// Output: result = 1
```

## getRemovalCount

```TypeScript
getRemovalCount(): number
```

Obtains the number of removals from this cache.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRemovalCount](arkts-arkts-util-lrucache-c.md#getremovalcount)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of removals from the cache. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
pro.updateCapacity(2);
pro.put(50,22);
let result = pro.getRemovalCount();
console.info("result = " + result);
// Output: result = 0
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

Checks whether this cache is empty.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isEmpty](arkts-arkts-util-lrucache-c.md#isempty)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the cache does not contain any value. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.isEmpty();
console.info("result = " + result);
// Output: result = false
```

## keys

```TypeScript
keys(): K[]
```

Obtains all keys in this cache, listed from the most to the least recently accessed.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [keys](arkts-arkts-util-lrucache-c.md#keys)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| K[] | All keys in the cache, listed from the most to the least recently accessed. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.keys();
console.info("result = " + result);
// Output: result = 2
```

## put

```TypeScript
put(key: K, value: V): V
```

Adds a key-value pair to this cache.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [put](arkts-arkts-util-lrucache-c.md#put)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key of the key-value pair to add. |
| value | V | Yes | Value of the key-value pair to add. |

**Return value:**

| Type | Description |
| --- | --- |
| V | Value added. If the key already exists, the existing value is returned; if **null** is passed in for **key** or **value**, an error is thrown. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
let result = pro.put(2,10);
console.info("result = " + result);
// Output: result = 10
```

## remove

```TypeScript
remove(key: K): V | undefined
```

Removes the specified key and its value from this cache.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [remove](arkts-arkts-util-lrucache-c.md#remove)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | K | Yes | Key to remove. |

**Return value:**

| Type | Description |
| --- | --- |
| V &#124; undefined | **Optional** object containing the removed key-value pair. If the key does not exist, an empty **Optional** object is returned; if **null** is passed in for **key**, an error is thrown. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
let result = pro.remove(20);
console.info("result = " + result);
// Output: result = undefined
```

## toString

```TypeScript
toString(): string
```

Obtains the string representation of this cache.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [toString](arkts-arkts-util-lrucache-c.md#tostring)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | String representation of this cache. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.put(2,10);
pro.get(2);
pro.remove(20);
let result = pro.toString();
console.info("result = " + result);
// Output: result = Lrubuffer[ maxSize = 64, hits = 1, misses = 0, hitRate = 100% ]
```

## updateCapacity

```TypeScript
updateCapacity(newCapacity: number): void
```

Changes the cache capacity. If the new capacity is less than or equal to **0**, an exception will be thrown.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [updateCapacity](arkts-arkts-util-lrucache-c.md#updatecapacity)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newCapacity | number | Yes | New capacity of the cache. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number,number> = new util.LruBuffer();
pro.updateCapacity(100);
```

## values

```TypeScript
values(): V[]
```

Obtains all values in this cache, listed from the most to the least recently accessed.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [values](arkts-arkts-util-lrucache-c.md#values)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| V[] | All values in the cache, listed from the most to the least recently accessed. |

**Examples**

```TypeScript
let pro : util.LruBuffer<number|string,number|string> = new util.LruBuffer();
pro.put(2,10);
pro.put(2,"anhu");
pro.put("afaf","grfb");
let result = pro.values();
console.info("result = " + result);
// Output: result = anhu,grfb
```

## length

```TypeScript
length: number
```

Total number of values in this cache.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** length

**System capability:** SystemCapability.Utils.Lang
