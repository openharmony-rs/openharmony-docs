# @ohos.util.HashSet (Nonlinear Container HashSet)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=e6c4038e0bf1c51873d9b3148ebe6dd87b09de1c translatedAt=2026-11-16T05:32:04.226Z pushedAt=2026-11-16T06:31:14.198Z nl=1 -->

HashSet is a non-linear container used to store a collection of non-duplicate elements, supporting efficient element addition, removal, and existence checking. HashSet is implemented based on [HashMap](js-apis-hashmap.md) and operates only on the value objects of elements, without involving the concept of keys.

Compared with [TreeSet](js-apis-treeset.md), the data in HashSet is distributed and stored by hash value, so the insertion order of elements may be inconsistent with the traversal order, whereas TreeSet stores elements in an ordered manner according to their natural ordering or a custom comparator. Elements in both collections are not allowed to be duplicated. HashSet allows inserting null values, while TreeSet does not recommend inserting null values, as this affects the sorting result.

**Recommended use cases:** When you need to ensure that elements in a collection are not duplicated, or need to remove duplicate elements from an existing collection, HashSet is recommended. You can also leverage the hash-based O(1) lookup feature of HashSet for efficient element existence checking.

This topic uses the following to identify the use of generics:
- T: Type

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - Container classes, implemented in static languages, have restrictions on storage locations and properties, and do not support custom properties or methods.


## Modules to Import

```ts
import { HashSet } from '@kit.ArkTS';
```

## HashSet

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Number of elements in a HashSet.|

**Example**

```ts
// Create a HashSet instance and add elements.
let hashSet = new HashSet<number>();
hashSet.add(1);
hashSet.add(2);
hashSet.add(3);
hashSet.add(4);
hashSet.add(5);
let result = hashSet.length;
console.info("length:", result);  // length: 5
```

### constructor

constructor()

The constructor of HashSet, used to create an empty HashSet instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200012 | The HashSet's constructor cannot be directly invoked. |

**Example**

```ts
let hashSet = new HashSet<number>();
```


### isEmpty

isEmpty(): boolean

Checks whether this HashSet is empty (contains no element).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true when empty, and returns false when not empty. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**Example**

```ts
// Create a HashSet instance and determine whether it is empty.
const hashSet = new HashSet<number>();
let result = hashSet.isEmpty();
console.info("result:", result);  // result: true
```


### has

has(value: T): boolean

Checks whether the HashSet contains the specified element. The lookup is based on the hash value and has O(1) time complexity.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes | Specifies the element to find. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true if the specified element is contained; returns false otherwise. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The has method cannot be bound. |

**Example**

```ts
// Create a HashSet instance and add elements.
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
let result = hashSet.has("squirrel");
console.info("result:", result);  // result: true
```


### add

add(value: T): boolean

Adds an element to the HashSet. After a successful addition, the length of the HashSet increases by 1. If the element to be added already exists, it will not be added again, false is returned, and the length remains unchanged.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes | Element to add. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true if the element is added successfully, and returns false if the element already exists. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The add method cannot be bound. |

**Example**

```ts
// Create a HashSet instance.
let hashSet = new HashSet<string>();
// Add elements to the HashSet.
let result = hashSet.add("squirrel");
console.info("result:", result);  // result: true
```


### remove

remove(value: T): boolean

Removes the specified element from the HashSet. After a successful removal, the length of the HashSet decreases by 1. If the specified element does not exist, the collection remains unchanged and false is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes | Specifies the element to delete. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true if the specified element is deleted successfully, and returns false if the specified element does not exist. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The remove method cannot be bound. |

**Example**

```ts
// Create a HashSet instance and add elements.
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");
let result = hashSet.remove("sparrow");
console.info("result:", result);  // result: true
```


### clear

clear(): void

Clears this HashSet and sets its length to **0**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The clear method cannot be bound. |

**Example**

```ts
// Create a HashSet instance and add elements.
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");
hashSet.clear();
let result = hashSet.isEmpty();
console.info("result:", result);  // result: true
```


### values

values(): IterableIterator&lt;T&gt;

Returns a new iterator object that contains all the values in this HashSet.

> **NOTE**
>
> It is not recommended to use the add and remove methods during the values iteration process, as this may cause an abnormal state during the iteration process. It is recommended to use a for loop for safe insertion and deletion operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Returns an iterator object that contains all the values in this HashSet. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The values method cannot be bound. |

**Example**

```ts
// Create a HashSet instance and add elements.
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");
let values = hashSet.values();
for (let value of values) {
  console.info("value:", value);
}
// value: squirrel
// value: sparrow
```


### forEach

forEach(callbackFn: (value?: T, key?: T, set?: HashSet&lt;T&gt;) => void, thisArg?: Object): void

Calls the callback function once for each element during the iteration process. It is not recommended to use the add and remove methods to modify the HashSet in the forEach callback, because this may cause an abnormal state during the iteration process.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function, invoked once for each element during the iteration process. The callback parameters include value, key, and set. For details, see the parameter description of callbackFn. |
| thisArg | Object | No | Used as the this value when callbackFn is invoked. Pass this parameter when you need to change the this reference inside the callback function. If not passed, the default value is the current instance object. |

callbackFn parameters
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | No | Value of the element currently being traversed. This parameter is always passed in during forEach traversal. |
| key | T | No | Value of the element currently being traversed (same as value). This parameter is always passed in during forEach traversal. |
| set | [HashSet&lt;T&gt;](#hashset) | No | Instance that invokes the **forEach** method. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**Example**

```ts
// Create a HashSet instance and add elements.
let hashSet = new HashSet<string>();
hashSet.add("sparrow");
hashSet.add("squirrel");
hashSet.forEach((value: string, key: string): void => {
  console.info("value:", value, "key:", key);
});
// value:squirrel key:squirrel
// value:sparrow key:sparrow
```
```ts
// Not recommended to use add and remove methods in forEach, as this may cause abnormal states during iteration. Recommended to use a for loop to perform safe insertion and deletion operations.
let hashSet = new HashSet<string>();
for(let i = 0; i < 10; i++) {
  hashSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  hashSet.remove("sparrow" + i);
}
```

### entries
entries(): IterableIterator&lt;[T, T]&gt;

Returns a new iterator object that contains all the elements in this HashSet, with each element returned in the form of [value, value].

> **NOTE**
>
> It is not recommended to use the add and remove methods during the entries iteration process, because this may cause an abnormal state during the iteration process. It is recommended to use a for loop for safe insertion and deletion operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;[T, T]&gt; | Returns an iterator object that contains all the elements in this HashSet. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The entries method cannot be bound. |

**Example**

```ts
// Create a HashSet instance and add elements.
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");
let entriesIterator = hashSet.entries();
let iterResult: IteratorResult<[string, string]> = entriesIterator.next();
while(!iterResult.done) {
  console.info("key:" + iterResult.value[0]);
  console.info("value:" + iterResult.value[1]);
  iterResult = entriesIterator.next();
}
// key:squirrel
// value:squirrel
// key:sparrow
// value:sparrow
```
```ts
// Not recommended to use add and remove methods in entries, as this may cause abnormal states during iteration. Recommended to use a for loop to perform safe insertion and deletion operations.
let hashSet = new HashSet<string>();
for(let i = 0; i < 10; i++) {
  hashSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  hashSet.remove("sparrow" + i);
}
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

Returns an iterator, each item of which is an element in the HashSet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Returns an iterator object that contains all the elements in this HashSet. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
// Create a HashSet instance and add elements.
let hashSet = new HashSet<string>();
hashSet.add("squirrel");
hashSet.add("sparrow");

// Method 1:
for (let item of hashSet) {
  console.info("value: " + item);
}
// value: squirrel
// value: sparrow

// Method 2:
let symbolIterator = hashSet[Symbol.iterator]();
let iterResult: IteratorResult<string> = symbolIterator.next();
while(!iterResult.done) {
  console.info("value: " + iterResult.value);
  iterResult = symbolIterator.next();
}
// value: squirrel
// value: sparrow
```

```ts
// Not recommended to use add and remove methods in Symbol.iterator, as this may cause abnormal states during iteration. Recommended to use a for loop to perform safe insertion and deletion operations.
let hashSet = new HashSet<string>();
for(let i = 0; i < 10; i++) {
  hashSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  hashSet.remove("sparrow" + i);
}
```