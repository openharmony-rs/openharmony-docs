# Class (Set)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=08d9523ef0226b259d674e299ae60897c53575d4 translatedAt=2026-11-04T10:36:36.476Z pushedAt=2026-11-04T10:42:10.551Z nl=2 -->

A non-linear data structure that stores unique values and efficiently performs element existence detection and deduplication operations.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module can be imported only to ArkTS files (with the file name extension .ets).

Generics are used in this document, involving the following generic type parameter:

- T: type, which can be any of the [sendable data types](../../arkts-utils/arkts-sendable.md#sendable-data-types).

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
| size | number | Yes  | No  | Number of elements in a set.|

## constructor

constructor(values?: readonly T[] | null)

A constructor used to create an ArkTS set.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description                                                     |
| ------ | ---- | ---- | --------------------------------------------------------- |
| values | readonly T[] \| null | No | Array or null. Default value is null, which creates an empty Set object. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The ArkTS Set's constructor cannot be directly invoked. |

**Example**

```ts
// Positive example 1:
// Create an empty Set object.
const mySet = new collections.Set<number>();
```

```ts
// Positive example 2:
// Create a Set using array initial values.
const mySet = new collections.Set<number>([1, 2, 3, 4, 5]);
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
const mySet1: collections.Set<number|SharedClass> = new collections.Set<number|SharedClass>([1, sObj]);
// Type arguments of generic "Sendable" type must be a "Sendable" data type (arkts-sendable-generic-types)
let obj = new Object();
const mySet2: collections.Set<number|SharedClass> = new collections.Set<number|Object>([1, obj]);
```
## constructor

constructor(iterable: Iterable\<T>)

Constructor used to create an ArkTS Set object from an iterable object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description                             |
| ------ | ---- | ---- | ------------------------------- |
| iterable | Iterable\<T> | Yes | Iterable object used to construct the ArkTS Set. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The ArkTS Set's constructor cannot be directly invoked. |

**Example**

```ts
// Create a standard Map object.
const mapper = new Map([
  ["1", "a"],
  ["2", "b"]
]);
// Obtain the iterator through the values() method of the standard Map to construct an ArkTS Set object.
let newSet = new collections.Set<string>(mapper.values());
console.info(`has a: ${newSet.has("a")}`); // Expected output: has a: true
console.info(`has b: ${newSet.has("b")}`); // Expected output: has b: true
```

## entries
entries(): IterableIterator<[T, T]>

Returns a set iterator object that contains the key-value pair of each element in this ArkTS set.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type                          | Description                   |
| ------------------------------ | ----------------------- |
| IterableIterator&lt;[T, T]&gt; | Returns a set iterator object that contains the key-value pair of each element in this ArkTS set.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                             |
| -------- | ----------------------------------------------------- |
| 10200011 | The entries method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
// Create a Set object.
const mySet = new collections.Set<number>([0, 1, 2, 3]);
// Obtain the entries iterator of the Set.
const iterator = mySet.entries();
// Expected output: entry: [0, 0]
console.info(`entry: ${iterator.next().value}`);
// Expected output: entry: [1, 1]
console.info(`entry: ${iterator.next().value}`);
```

## keys
keys(): IterableIterator\<T>

Returns a set iterator object that contains the key of each element in this ArkTS set.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type                     | Description                   |
| ------------------------- | ----------------------- |
| IterableIterator&lt;T&gt; | Returns a set iterator object that contains the key of each element in this ArkTS set.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                          |
| -------- | -------------------------------------------------- |
| 10200011 | The keys method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
// Create a Set object.
const mySet = new collections.Set<number>([0, 1, 2, 3]);
// Obtain the keys iterator of the Set.
const iterator = mySet.keys();
// Expected output: key: 0
console.info(`key: ${iterator.next().value}`);
// Expected output: key: 1
console.info(`key: ${iterator.next().value}`);
```

## values
values(): IterableIterator\<T>

Returns a set iterator object that contains the value of each element in this ArkTS set.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type                     | Description                   |
| ------------------------- | ----------------------- |
| IterableIterator&lt;T&gt; | Returns a set iterator object that contains the value of each element in this ArkTS set.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                            |
| -------- | ---------------------------------------------------- |
| 10200011 | The values method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error. |

**Example**

```ts
// Example 1:
// Create a Set object.
const mySet = new collections.Set<number>([0, 1, 2, 3]);
// Obtain the values iterator.
const iterator = mySet.values();
// Expected output: value: 0
console.info(`value: ${iterator.next().value}`);
// Expected output: value: 1
console.info(`value: ${iterator.next().value}`);
```

```ts
// Example 2:
// Create a Set object.
const mySet = new collections.Set<number>([0, 1, 2, 3]);
// Obtain the values iterator.
const valueIter = mySet.values();
// Traverse the Set and delete even elements.
for (let value of valueIter) {
  if (value % 2 == 0) {
    mySet.delete(value);
  }
}

// Expected output: size: 2
console.info(`size: ${mySet.size}`);
```

## clear
clear(): void

Removes all elements from this ArkTS set.

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
// Create a Set object.
const mySet = new collections.Set<number>([0, 1]);
// Expected output: size: 2
console.info(`size: ${mySet.size}`);
// Clear all elements in the Set.
mySet.clear();
// Expected output: size: 0
console.info(`size: ${mySet.size}`);
```

## delete
delete(value: T): boolean

Deletes an element from this ArkTS set.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description            |
| ------ | ---- | ---- | ---------------- |
| value    | T    | Yes  | Target value.|

**Return value**

| Type   | Description                             |
| ------- | --------------------------------- |
| boolean | Returns true if the deletion is successful, and returns false if the specified element does not exist. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                            |
| -------- | ---------------------------------------------------- |
| 10200011 | The delete method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error.                   |


**Example**

```ts
// Create a Set object.
const mySet = new collections.Set<string>(["hello", "world"]);
// Delete the specified element from the Set.
// Expected result: result: true
console.info(`result: ${mySet.delete("hello")}`);
// Check whether the element still exists.
// Expected result: result: false
console.info(`result: ${mySet.has("hello")}`);
// Delete the already-deleted element again.
// Expected result: result: false
console.info(`result: ${mySet.delete("hello")}`);
```

## forEach
forEach(callbackFn: (value: T, value2: T, set: Set\<T>) => void): void

Executes a callback function once for each key-value pair in this Set in insertion order.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name    | Type                                        | Mandatory| Description      |
| ---------- | -------------------------------------------- | ---- | ---------- |
| callbackFn | (value: T, value2: T, set: Set\<T>) => void  | Yes   | Callback function. The current Set object should not be modified during callback execution; otherwise, a concurrent modification error is triggered.  |

callbackFn parameters
| Name| Type        | Mandatory| Description                        |
| ------ | ------------ | ---- | ---------------------------- |
| value  | T            | No  | Value of the element that is currently traversed.|
| value2 | T            | No  | Key of the element that is currently traversed.|
| set    | Set&lt;T&gt; | No   | Current Set instance object.            |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                             |
| -------- | ----------------------------------------------------- |
| 10200011 | The forEach method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error.                    |

**Example**

```ts
// Positive example:
// Traverse each element in the Set.
new collections.Set<string>(["foo", "bar", "baz"]).forEach((value, value2, set) => {
  console.info(`s[${value}] = ${value2}`);
});
```

<!--code_no_check-->
```ts
// Negative example:
new collections.Set<string>(["foo", "bar", "baz"]).forEach((value, value2, set) => {
  // Throw exception `Concurrent modification error.`
  set.delete(value);
});
```

## has
has(value: T): boolean

Checks whether a value exists in this ArkTS set.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type| Mandatory| Description            |
| ------ | ---- | ---- | ---------------- |
| value  | T    | Yes  | Target key.|

**Return value**

| Type   | Description                                         |
| ------- | --------------------------------------------- |
| boolean | Check result. The value **true** is returned if the value exists; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The has method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error.                |

**Example**

```ts
// Create a Set object.
const mySet = new collections.Set<string>(["hello", "world"]);
// Check whether the Set contains the specified element.
// Expected output: result: true
console.info(`result: ${mySet.has("hello")}`);
// Expected output: result: true
console.info(`result: ${mySet.has("world")}`);
```

## add
add(value: T): Set\<T>

If the element does not exist in the Set, inserts it into the Set.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type| Mandatory| Description            |
| ------ | ---- | ---- | ---------------- |
| value  | T    | Yes  | Target value. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| Set&lt;T&gt; | The Set object itself after the element is inserted. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 10200011 | The add method cannot be bound with non-sendable. |
| 10200201 | Concurrent modification error.                |

**Example**

```ts
// Positive example:
// Create an empty Set object.
const mySet: collections.Set<string> = new collections.Set<string>();
// Add a new element to the Set.
mySet.add("foo");
```

<!--code_no_check-->
```ts
// Negative example:
let obj = new Object();
const mySet: collections.Set<Object> = new collections.Set<Object>();
// Type arguments of generic "Sendable" type must be a "Sendable" data type (arkts-sendable-generic-types)
mySet.add(obj);
```

## [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

Returns an iterator that contains all elements in the Set.

> **NOTE**
>
> This API cannot be used in .ets files.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Iterator containing all elements in the Set. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
// Create a Set object
let mySet = new collections.Set<number>([1, 2, 3, 4, 5]);
// Convert the Set values to an array
let values: Array<number> = Array.from(mySet.values());
// Iterate over and output each element
for (let item of values) {
  console.info(`value: ${item}`);
}
```
