# Class (Map)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=a9fc2488607fcc42bb5986c0a0089b8eda0278e0 translatedAt=2026-11-16T04:51:49.293Z pushedAt=2026-11-16T06:31:14.141Z nl=2 -->

A non-linear data structure based on key-value pair storage, which can efficiently access the corresponding value through a unique key.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module can be imported only to ArkTS files (with the file name extension .ets).

Generics are used in this document, involving the following generic type parameter:

- K: key.
- V: value.

The K and V types must be any of the [sendable data types](../../arkts-utils/arkts-sendable.md#sendable-data-types).

**Decorator**: \@Sendable

## Modules to Import

```ts
import { collections } from '@kit.ArkTS';
```

## Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type  | Read Only| Optional| Description           |
| ---- | ------ | ---- | ---- | --------------- |
| size | number | Yes  | No  | Number of elements in a map.|


## constructor
constructor(entries?: readonly (readonly [K, V])[] | null)

A constructor used to create an ArkTS map.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                                                        |
| ------- | ------ | ---- | ------------------------------------------------------------ |
| entries | readonly (readonly [K, V])[] \| null | No | An array of key-value pairs or null. The default value is null, which creates an empty Map object. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The ArkTS Map's constructor cannot be directly invoked. |

**Example**

```ts
// Positive example 1:
// Create an empty ArkTS Map object.
const myMap = new collections.Map<number, number>();
```

```ts
// Positive example 2:
// Create an ArkTS Map object with initial elements through an array of key-value pairs.
const myMap = new collections.Map<number, string>([
  [1, "one"],
  [2, "two"],
  [3, "three"]
]);
```

<!--code_no_check-->
```ts
// Negative example:
@Sendable
class SharedClass {
  constructor() {
  }
}
let sObj = new SharedClass();
const myMap1: collections.Map<number, SharedClass> = new collections.Map<number, SharedClass>([[1, sObj]]);
// Type arguments of generic "Sendable" type must be a "Sendable" data type (arkts-sendable-generic-types)
let obj = new Object();
const myMap2: collections.Map<number, Object> = new collections.Map<number, Object>([[1, obj]]);
```

## constructor

constructor(iterable: Iterable\<readonly \[K, V]>)

Constructor used to create an ArkTS Map object from an iterable object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description                             |
| ------ | ---- | ---- | ------------------------------- |
| iterable | Iterable\<readonly \[K, V]> | Yes | Iterable object used to construct the ArkTS Map. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The ArkTS Map's constructor cannot be directly invoked. |

**Example**

```ts
// Create a standard Map object.
const mapper = new Map([
  ["1", "a"],
  ["2", "b"]
]);
// Obtain the Iterator through the entries() method of the standard Map, and construct an ArkTS Map object.
let newMap = new collections.Map<string, string>(mapper.entries());
console.info(newMap.get("1")); // Expected output: a
console.info(newMap.get("2")); // Expected output: b
```


## entries
entries(): IterableIterator<[K, V]>

Returns a map iterator object that contains the key-value pair of each element in this ArkTS map.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type                          | Description                   |
| ------------------------------ | ----------------------- |
| IterableIterator&lt;[K, V]&gt; | Map iterator object.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                             |
| -------- | ----------------------------------------------------- |
| 10200011 | The entries method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
// Example 1:
// Create a Map object.
const myMap = new collections.Map<number, string>([
  [0, "foo"],
  [1, "bar"]
]);
// Call the entries() method to return an iterator of [key, value] pairs for each element in the Map.
const iterator = myMap.entries();
// Expected output: 0, foo
console.info(iterator.next().value);
// Expected output: 1, bar
console.info(iterator.next().value);
```

```ts
// Example 2:
// Create a Map object.
const myMap: collections.Map<number, string> = new collections.Map<number, string>([
  [0, "one"],
  [1, "two"],
  [2, "three"],
  [3, "four"]
]);
// Return a myMap Iterator object, which contains the [number, string] key-value pair of each element in this myMap.
const entriesIter: IterableIterator<[number, string]> = myMap.entries();
// Traverse the entriesIter Iterator object.
for (const entry of entriesIter) {
  if (entry[1].startsWith("t")) {
    myMap.delete(entry[0]);
  }
}
// Expected output: 2
console.info("size:" + myMap.size);
```

## keys
keys(): IterableIterator\<K>

Returns a map iterator object that contains the key of each element in this ArkTS map.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type                     | Description                   |
| ------------------------- | ----------------------- |
| IterableIterator&lt;K&gt; | Map iterator object.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                          |
| -------- | -------------------------------------------------- |
| 10200011 | The keys method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
// Create a Map object.
const myMap = new collections.Map<number, string>([
  [0, "foo"],
  [1, "bar"]
]);
// Call the keys() method to return an iterator containing all keys in the Map.
const iterator = myMap.keys();
// Expected output: 0
console.info(iterator.next().value);
// Expected output: 1
console.info(iterator.next().value);
```

## values
values(): IterableIterator\<V>

Returns a Map iterator object that contains the value of each element in this Map.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type                     | Description                   |
| ------------------------- | ----------------------- |
| IterableIterator&lt;V&gt; | Map iterator object.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                            |
| -------- | ---------------------------------------------------- |
| 10200011 | The values method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
// Create a Map object.
const myMap = new collections.Map<number, string>([
  [0, "foo"],
  [1, "bar"]
]);
// Call the values() method to return an iterator containing all values in the Map.
const iterator = myMap.values();
// Expected output: "foo"
console.info(iterator.next().value);
// Expected output: "bar"
console.info(iterator.next().value);
```

## clear
clear(): void

Removes all elements from this ArkTS map.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                           |
| -------- | --------------------------------------------------- |
| 10200011 | The clear method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error.                  |

**Example**

```ts
// Create a Map object.
const myMap = new collections.Map<number, string>([
  [0, "foo"],
  [1, "bar"]
]);
// Expected output: 2
console.info("size:" + myMap.size);
// Call the clear() method to delete all elements in the Map.
myMap.clear();
// Expected output: 0
console.info("size:" + myMap.size);
```

## delete
delete(key: K): boolean

Deletes the element corresponding to the specified key in this Map.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description            |
| ------ | ---- | ---- | ---------------- |
| key    | K    | Yes  | Key to delete.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Operation result. The value **true** is returned if the key exists and has been deleted; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                            |
| -------- | ---------------------------------------------------- |
| 10200011 | The delete method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error.                   |


**Example**

```ts
// Create a Map object.
const myMap = new collections.Map<string, string>([
  ["hello", "world"]
]);
// Delete the specified key from the Map.
// Expected result: true
console.info("result:" + myMap.delete("hello"));
// Determine whether the key still exists.
// Expected result: false
console.info("result:" + myMap.has("hello"));
// Delete the already-deleted key again.
// Expected result: false
console.info("result:" + myMap.delete("hello"));
```

## forEach
forEach(callbackFn: (value: V, key: K, map: Map<K, V>) => void): void

Executes a callback function once for each key-value pair in this Map in insertion order.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name    | Type                                      | Mandatory| Description      |
| ---------- | ------------------------------------------ | ---- | ---------- |
| callbackFn | (value: V, key: K, map: Map<K, V>) => void | Yes | Callback function. The current Map object should not be modified during callback execution; otherwise, a concurrent modification error is triggered. |

callbackFn parameters
| Name| Type           | Mandatory| Description                        |
| ------ | --------------- | ---- | ---------------------------- |
| value  | V               | No  | Value of the element that is currently traversed.|
| key    | K               | No  | Key of the element that is currently traversed.|
| map    | Map&lt;K, V&gt; | No   | Current Map instance object.            |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                             |
| -------- | ----------------------------------------------------- |
| 10200011 | The forEach method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error.                    |

**Example**

```ts
// Positive example:
// Traverse each element in the Map.
new collections.Map<string, number>([
  ["foo", 0],
  ["bar", 1],
  ["baz", 2],
]).forEach((value, key, map) => {
  console.info(`m[${key}] = ${value}`);
});
```

<!--code_no_check-->
```ts
// Negative example:
new collections.Map<string, number>([
  ["foo", 0],
  ["bar", 1],
  ["baz", 2],
]).forEach((value, key, map) => {
  // Throw exception `Concurrent modification error.`
  map.delete(key);
});
```

## get
get(key: K): V | undefined

Returns the element corresponding to the specified key in this Map.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description     |
| ------ | ---- | ---- | --------- |
| key    | K    | Yes   | Key whose value is to be obtained. |

**Return value**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| V \| undefined    | Value obtained. If the key is not found, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The get method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error.                |

**Example**

```ts
const myMap = new collections.Map<string, string>([
  ["hello", "world"],
]);
// Expected output: "world"
console.info(myMap.get("hello"));
// Expected output: undefined
console.info(myMap.get("hel"));
```

## has
has(key: K): boolean

Determines whether the specified key exists in this Map.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description     |
| ------ | ---- | ---- | --------- |
| key    | K    | Yes   | Target key. |

**Return value**

| Type   | Description                                         |
| ------- | --------------------------------------------- |
| boolean | If the specified key exists in the Map, true is returned; otherwise, false is returned. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The has method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error.                |

**Example**

```ts
// Create a Map object.
const myMap = new collections.Map<string, string>([
  ["hello", "world"],
]);
// Determine whether the specified key exists in the Map.
// Expected output: true
console.info("result:" + myMap.has("hello"));
// Expected output: false
console.info("result:" + myMap.has("world"));
```

## set
set(key: K, value: V): Map<K, V>

Adds or updates a key-value pair to this ArkTS map.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description     |
| ------ | ---- | ---- | --------- |
| key    | K    | Yes   | Key to add or update. |
| value    | V    | Yes   | Value to add or update. |

**Return value**

| Type           | Description   |
| --------------- | ------- |
| Map&lt;K, V&gt; | The Map object itself after the key-value pair is added or updated. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The set method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error.                |

**Example**

```ts
// Positive example:
const myMap = new collections.Map<string, string>();
// Call the set() method to add the key "foo" and its corresponding value "bar" to the Map.
myMap.set("foo", "bar");
```

<!--code_no_check-->
```ts
// Negative example:
let obj = new Object();
const myMap: collections.Map<string, Object> = new collections.Map<string, Object>();
// Type arguments of generic "Sendable" type must be a "Sendable" data type (arkts-sendable-generic-types)
myMap.set("foo", obj);
```

## containsValue

containsValue(value: V): boolean

Determines whether this Map contains one or more keys mapped to the specified value.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description      |
| ------ | ---- | ---- | --------- |
| value    | V    | Yes   | Target value to check. |

**Return value**

| Type    | Description                                          |
| ------- | --------------------------------------------- |
| boolean | Returns true if one or more keys in the Map are mapped to this value; otherwise, returns false. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message                                          |
| -------- | ------------------------------------------------- |
| 10200011 | The containsValue method cannot be bound. |
| 10200201 | Concurrent modification exception                |

**Example**

```ts
let myMap = new collections.Map<string, number>([
  ["one", 1],
  ["two", 2],
  ["TWO", 2],
  ["three", 3]
]);
console.info("myMap.containsValue(1) = " + myMap.containsValue(1)); // true
console.info("myMap.containsValue(2) = " + myMap.containsValue(2)); // true
console.info("myMap.containsValue(4) = " + myMap.containsValue(4)); // false
```

## put

put(key: K, value: V): V | undefined

Associates the specified key with the specified value in the current Map. If the key already exists, the new value overwrites the old value and the old value is returned; if the key does not exist, a new key-value pair is added and undefined is returned.

> **Note:**
>
> When **undefined** is returned, it is impossible to directly distinguish whether the key does not exist or the key exists but its value is **undefined**. You can use [has](#has) to check whether the key exists before calling this API, so as to distinguish the situation to which the returned **undefined** belongs.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description      |
| ------ | ---- | ---- | --------- |
| key    | K    | Yes   | Key to add or update. |
| value    | V    | Yes   | Value to add or update. |

**Return value**

| Type            | Description    |
| --------------- | ------- |
| V \| undefined | Previous value associated with the key. If the key did not exist in the Map before, undefined is returned. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message                                          |
| -------- | ------------------------------------------------- |
| 10200011 | The put method cannot be bound. |
| 10200201 | Concurrent modification exception                |

**Example**

```ts
let myMap = new collections.Map<number, string>([
  [1, "one"],
  [2, "two"],
]);

let old1 = myMap.put(1, "*ONE*");
console.info("old1 = " + old1); // one
console.info("value = " + myMap.get(1)); // *ONE*

myMap.put(3, "three");
console.info('' + (myMap.put(3, "three") === undefined)); // false, key 3 already exists
console.info('' + (myMap.put(4, "four") === undefined)); // true, key 4 did not exist before
```

## putAll

putAll(from: Map\<K, V>): void

Updates the current Map with the key-value pairs from the specified ArkTS Map. If a key in the specified ArkTS Map already exists in the current Map, the corresponding value in the current Map is overwritten; otherwise, a new key-value pair is added.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description      |
| ------ | ---- | ---- | --------- |
| from    | Map\<K, V>    | Yes   | ArkTS Map that provides the key-value pairs. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message                                          |
| -------- | ------------------------------------------------- |
| 10200011 | The putAll method cannot be bound. |
| 10200201 | Concurrent modification exception                |

**Example**

```ts
let myMap = new collections.Map<number, string>([
  [1, "one"],
  [2, "two"],
]);

let putMap = new collections.Map<number, string>([
  [3, "three"],
  [4, "four"],
  [1, "_ONE_"],
]);
myMap.putAll(putMap);
// The content of myMap is: [[1, "_ONE_"], [2, "two"], [3, "three"], [4, "four"]]
for (const entry of myMap.entries()) {
  console.info("key = " + entry[0] + ", value = " + entry[1]);
}
```

## putAll

putAll(from: ReadonlyMap\<K, V>): void

Updates the current Map with the key-value pairs from the specified JavaScript native container Map. If the specified JavaScript native container Map contains a key that is the same as a key in the current Map, the corresponding value in the current Map is overwritten; otherwise, a new key-value pair is added.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description      |
| ------ | ---- | ---- | --------- |
| from    | ReadonlyMap\<K, V>    | Yes   | JavaScript native container Map that provides the key-value pairs. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message                                          |
| -------- | ------------------------------------------------- |
| 10200011 | The putAll method cannot be bound. |
| 10200201 | Concurrent modification exception                |

**Example**

```ts
let myMap = new collections.Map<number, string>([
  [1, "one"],
  [2, "two"],
]);

let builtinMap = new Map<number, string>([
  [3, "_THREE_"],
  [5, "five"],
]);
myMap.putAll(builtinMap);
// The content of myMap is: [[1, "one"], [2, "two"], [3, "_THREE_"], [5, "five"]]
for (const entry of myMap.entries()) {
  console.info("key = " + entry[0] + ", value = " + entry[1]);
}
```

## remove

remove(key: K): V | undefined

Removes the specified key and its corresponding value from this Map, and returns the previous value associated with the key. If the key does not exist, undefined is returned.

> **Note:**
>
> When **undefined** is returned, it is impossible to directly distinguish whether the key does not exist or the key exists but its value is **undefined**. You can use [has](#has) to check whether the key exists before calling this API, so as to distinguish the situation to which the returned **undefined** belongs.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description      |
| ------ | ---- | ---- | --------- |
| key    | K    | Yes   | Key to be removed. |

**Return value**

| Type            | Description    |
| --------------- | ------- |
| V \| undefined | Previous value associated with the key. If the key does not exist in the Map, **undefined** is returned. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message                                          |
| -------- | ------------------------------------------------- |
| 10200011 | The remove method cannot be bound. |
| 10200201 | Concurrent modification exception                |

**Example**

```ts
let myMap = new collections.Map<number, string>([
  [1, "one"],
  [2, "two"]
]);

console.info(myMap.remove(1)); // one
// The content of myMap is: [[2, "two"]]
for (const entry of myMap.entries()) {
  console.info("key = " + entry[0] + ", value = " + entry[1]);
}

let ret = myMap.remove(1);
console.info("myMap.remove(1) == undefined is " + (ret === undefined)); // true, key 1 does not exist
```

## [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;[K, V]&gt;

Returns an iterator that contains the key-value pair of each element in the Map.

> **NOTE**
>
> This API cannot be used in .ets files.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**
| Type| Description|
| -------- | -------- |
| IterableIterator<[K, V]> | An iterator containing the key-value pair of each element in the Map. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
let myMap = new collections.Map<number, string>([
    [0, "one"],
    [1, "two"],
    [2, "three"],
    [3, "four"]
]);
// Obtain the Array of all keys through Array.from and keys().
let keys = Array.from(myMap.keys());
// Traverse each key and obtain the corresponding value through the get() method.
for (let key of keys) {
  console.info("key:" + key);
  console.info("value:" + myMap.get(key));
}
```
