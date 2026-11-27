# @ohos.util.TreeMap (Nonlinear Container TreeMap)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=a211d88dec3940df73a753a1732c7250fbff3179 translatedAt=2026-11-16T05:55:16.093Z pushedAt=2026-11-16T06:54:09.639Z nl=1 -->

TreeMap stores key-value (KV) pairs. Each key must be unique and have only one value.

TreeMap is implemented based on a red-black tree. It uses the binary tree characteristics to search for key-value pairs, and the time complexity of search, insertion, and deletion operations is O(log n). Keys are stored in sorted order, which enables efficient in-order traversal.

Compared with [HashMap](js-apis-hashmap.md), HashMap accesses data based on the hashCode of keys, which is faster but does not guarantee the order of keys. TreeMap, in contrast, accesses data in sorted order based on a red-black tree, which is less efficient but supports ordered operations such as in-order traversal, range query, and lookup of the first/last key and adjacent keys.

**Recommended use cases:** Scenarios that require ordered storage and access of key-value pairs, such as range query, in-order traversal, and adjacent key lookup.

This topic uses the following to identify the use of generics:

- K: Key

- V: Value

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Container classes, implemented in static languages, have restrictions on storage locations and properties, and do not support custom properties or methods.


## Modules to Import

```ts
import { TreeMap } from '@kit.ArkTS';
```

## TreeMap

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Number of elements in a TreeMap.|


### constructor

constructor(comparator?:(firstValue: K, secondValue: K) => boolean)

Constructor of TreeMap, which supports sorting elements by custom rules through a comparison function. When the key is a custom type, a comparison function must be provided; otherwise, keys of the custom type cannot be sorted and compared properly.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| comparator | function | No | User-defined Comparison Function that sorts Elements based on the comparison relationship. The default value is null, indicating that no Comparison Function is provided. When the key is a custom type, a Comparison Function must be provided; otherwise, insertion or lookup exceptions may occur. |

comparator parameters

| Name| Type| Mandatory| Description|
| ------| ---- | ----- | -- |
| firstValue | K | Yes | The first element involved in the comparison, serving as the first object for sorting judgment. |
| secondValue | K | Yes | The second element involved in the comparison, serving as the second object for sorting judgment. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200012 | The TreeMap's constructor cannot be directly invoked. |

**Example**

```ts
// Default constructor.
let treeMap = new TreeMap<number, number>();
```

```ts
// Use the comparator firstValue < secondValue if the elements are expected to be sorted in ascending order. Use firstValue > secondValue if the elements are expected to be sorted in descending order.
let treeMap: TreeMap<string, string> = new TreeMap<string, string>((firstValue: string, secondValue: string): boolean => {
  return firstValue > secondValue;
});
treeMap.set('aa', '3');
treeMap.set('dd', '1');
treeMap.set('cc', '2');
treeMap.set('bb', '4');
for (let item of treeMap) {
  console.info('key: ' + item[0], 'value: ' + item[1]);
};
// Output:
// key: dd value: 1
// key: cc value: 2
// key: bb value: 4
// key: aa value: 3
```

```ts
// When inserting a custom type, a comparison function must be provided.
class TestEntry {
  public id: number = 0;
}

let testEntryMap: TreeMap<TestEntry, string> = new TreeMap<TestEntry, string>((t1: TestEntry, t2: TestEntry): boolean => {
  return t1.id < t2.id;
});
let entry1: TestEntry = {
  id: 0
};
let entry2: TestEntry = {
  id: 1
}
testEntryMap.set(entry1, '0');
testEntryMap.set(entry2, '1');
console.info('length:', testEntryMap.length); // length: 2
```


### isEmpty

isEmpty(): boolean

Checks whether this TreeMap is empty (contains no element).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns **true** if the TreeMap is empty; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<number, number>();
// Check whether the container is empty.
let result = treeMap.isEmpty();
console.info('result:', result);  // result: true
```


### hasKey

hasKey(key: K): boolean

Checks whether this TreeMap has the specified key.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes | Key to check whether it exists in the container. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns **true** if the specified key is contained; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The hasKey method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
// Add data to the container.
treeMap.set('squirrel', 123);
// Determine whether the container contains the specified key.
let result = treeMap.hasKey('squirrel');
console.info('result:', result);  // result: true
```


### hasValue

hasValue(value: V): boolean

Checks whether the container contains the specified value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | V | Yes | Value to check whether it exists in the container. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true if the specified value is contained; otherwise returns false. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The hasValue method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
// Determine whether the container contains the specified value.
let result = treeMap.hasValue(123);
console.info('result:', result);  // result: true
```


### get

get(key: K): V

Obtains the value corresponding to the specified key. If the specified key does not exist, undefined is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes | Specify the key whose corresponding value is required. |

**Return value**

| Type| Description|
| -------- | -------- |
| V | Returns the value mapped by the key, and returns undefined when the specified key does not exist. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The get method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// Obtain the value corresponding to the specified key.
let result = treeMap.get('sparrow');
console.info('result:', result); // result: 356
```


### getFirstKey

getFirstKey(): K

Obtains the first key in the container in sorted order. If the container is empty, undefined is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| K | Return the first key in sorted order, or undefined if the container is empty. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getFirstKey method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// Obtain the first key after sorting the container.
let result = treeMap.getFirstKey();
console.info('result:', result); // result: sparrow
```


### getLastKey

getLastKey(): K

Obtains the last key in the container in sorted order. If the container is empty, undefined is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| K | Returns the last key in sorted order, or undefined when the container is empty. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getLastKey method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// Obtain the last key in the container by sorting.
let result = treeMap.getLastKey();
console.info('result:', result); // result: squirrel
```


### setAll

setAll(map: TreeMap<K, V>): void

Adds all elements in one TreeMap to another TreeMap.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| map | TreeMap<K, V> | Yes | Adds all elements in the parameter map to the TreeMap object that calls the setAll method. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The setAll method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
let map: TreeMap<string, number> = new TreeMap();
map.set('demo', 12);
map.setAll(treeMap); // Add all elements in the treeMap to the map.
map.forEach((value?: number, key?: string) : void => {
  console.info('value: ' + value, 'key: ' + key); 
});
// Output:
// value: 12 key: demo
// value: 356 key: sparrow
// value: 123 key: squirrel
```


### set

set(key: K, value: V): Object

Adds a key-value pair to the container. If the key already exists, the corresponding value is updated; if the key does not exist, a new key-value pair is added.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes| Key of the target element.|
| value | V | Yes| Value of the target element.|

**Return value**

| Type| Description|
| -------- | -------- |
| Object | TreeMap that contains the new element.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The set method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
console.info('squirrel:', treeMap.get('squirrel')); // squirrel: 123
```


### remove

remove(key: K): V

Deletes the element corresponding to the specified key and returns its value. If the specified key does not exist, undefined is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes | Specifies the key corresponding to the element to be removed. |

**Return value**

| Type| Description|
| -------- | -------- |
| V | Value of the element removed.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The remove method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
let result = treeMap.remove('sparrow'); // Remove the data.
console.info('result = ' + result); // result = 356
```


### getLowerKey

getLowerKey(key: K): K

Obtains the largest key in the container that is smaller than the comparison key. If no key smaller than the comparison key exists, undefined is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes| Input key.|

**Return value**

| Type| Description|
| -------- | -------- |
| K | Returns the largest key smaller than the specified key, or undefined when not existing. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getLowerKey method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<number, string>();
treeMap.set(1, 'one');
treeMap.set(2, 'two');
treeMap.set(3, 'three');
treeMap.set(4, 'four');
// Obtain the largest key less than the key value 3 in the less-than comparison.
let result = treeMap.getLowerKey(3);
console.info('result:', result); // result: 2
```


### getHigherKey

getHigherKey(key: K): K

Obtains the smallest key in the container that is greater than the specified key. If no key greater than the specified key exists, undefined is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes| Input key.|

**Return value**

| Type| Description|
| -------- | -------- |
| K | Returns the key that is one position after the specified key in the sorted order. Returns undefined when not existing. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getHigherKey method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<number, string>();
treeMap.set(1, 'one');
treeMap.set(2, 'two');
treeMap.set(3, 'three');
treeMap.set(4, 'four');
// Obtain the minimum key greater than the comparison key value 3.
let result = treeMap.getHigherKey(3);
console.info('result:', result); // result: 4
```

### replace

replace(key: K, newValue: V): boolean

Replaces the value corresponding to the specified key in the container. If the key exists, the replacement succeeds and true is returned. If the key does not exist, no modification is made and false is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | K | Yes | Specify the key corresponding to the value to be replaced. |
| newValue | V | Yes | New value to replace, which overwrites the original value corresponding to the specified key. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns **true** if the element is replaced successfully; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The replace method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('sparrow', 123);
// Replace the value corresponding to the specified key.
treeMap.replace('sparrow', 357);
console.info('sparrow:', treeMap.get('sparrow')); // sparrow: 357
```


### clear

clear(): void

Clears this TreeMap and sets its length to **0**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The clear method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// Clear all elements in the container.
treeMap.clear();
let result = treeMap.isEmpty();
console.info('result:', result); // result: true
```


### keys

keys(): IterableIterator&lt;K&gt;

Returns an iterator that contains all the keys in this TreeMap.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;K&gt; | Returns an iterator object containing all keys in this map. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The keys method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// Obtain the iterator of all keys.
let keys = treeMap.keys();
for (let key of keys) {
  console.info('key:', key);
}
// Output:
// key: sparrow
// key: squirrel
```


### values

values(): IterableIterator&lt;V&gt;

Returns a new iterator object containing all values in this map.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;V&gt; | Returns an iterator object containing all values in this map. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The values method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// Obtain the iterator of all values.
let values = treeMap.values();
for (let value of values) {
  console.info('value:', value);
}
// value: 356
// value: 123
```


### forEach

forEach(callbackFn: (value?: V, key?: K, map?: TreeMap<K, V>) => void, thisArg?: Object): void

Traverses the elements and their keys on the instance object through a callback function.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function used to traverse each key-value pair in the instance object and perform custom operations in the callback. |
| thisArg | Object | No | Value used as this when callbackFn is called. The default value is undefined. |

callbackFn
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | V | No | Value of the element that is currently traversed. |
| key | K | No | Key of the element that is currently traversed. |
| map | TreeMap<K, V> | No | Instance that invokes the **forEach** method. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('sparrow', 123);
treeMap.set('gull', 357);
// Traverse all elements in the TreeMap through a callback function.
treeMap.forEach((value: number, key: string): void => {
  console.info('value: ' + value, 'key: ' + key);
});
// Output:
// value: 357 key: gull
// value: 123 key: sparrow
```

```ts
 // You are not advised to use the set or remove APIs in forEach because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
 let treeMap = new TreeMap<string, number>();
 for (let i = 0; i < 10; i++) {
   treeMap.set('sparrow' + i, 123);
 }
 for (let i = 0; i < 10; i++) {
   treeMap.remove('sparrow' + i);
 }
```

### entries

entries(): IterableIterator<[K, V]>

Returns an iterator that contains all the elements in this TreeMap.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator<[K, V]> | Returns an iterator object containing all key-value pairs in this map. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The entries method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);
// Obtain the key-value pair iterator.
let entriesIterator = treeMap.entries();
// Traverse all key-value pairs through the iterator.
let nextResult: IteratorResult<Object[]> = entriesIterator.next();
while (!nextResult.done) {
  console.info('TreeMap:', nextResult.value);
  nextResult = entriesIterator.next();
}
// Output:
// TreeMap: sparrow,356
// TreeMap: squirrel,123
```

```ts
 // You are not advised to use the set or remove APIs in entries because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
 let treeMap = new TreeMap<string, number>();
 for (let i = 0; i < 10; i++) {
   treeMap.set('sparrow' + i, 123);
 }
 for (let i = 0;i < 10; i++) {
   treeMap.remove('sparrow' + i);
 }
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;[K, V]&gt;

Returns an iterator, where each item of the iterator is a [K, V] array containing a key and a value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**
| Type| Description|
| -------- | -------- |
| IterableIterator<[K, V]> | Iterator obtained.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
let treeMap = new TreeMap<string, number>();
treeMap.set('squirrel', 123);
treeMap.set('sparrow', 356);

// Method 1:
for (let item of treeMap) {
  console.info('TreeMap:', item[0], item[1]);
}
// Output:
// TreeMap: sparrow,356
// TreeMap: squirrel,123

// Method 2:
let iter = treeMap[Symbol.iterator]();
let nextResult: IteratorResult<Object[]> = iter.next();
while (!nextResult.done) {
  console.info('key:', nextResult.value[0]);
  console.info('value:', nextResult.value[1]);
  nextResult = iter.next();
}
// Output:
// key: sparrow
// value: 356
// key: squirrel
// value: 123
```

```ts
 // You are not advised to use the set or remove APIs in Symbol.iterator because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
 let treeMap = new TreeMap<string, number>();
 for (let i = 0; i < 10; i++) {
   treeMap.set('sparrow' + i, 123);
 }
 for (let i = 0;i < 10; i++) {
   treeMap.remove('sparrow' + i);
 }
```