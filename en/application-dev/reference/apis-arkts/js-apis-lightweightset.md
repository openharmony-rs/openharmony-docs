# @ohos.util.LightWeightSet (Nonlinear Container LightWeightSet)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=d1445e627393d0b704d7fd66f2f8322beeeda048 translatedAt=2026-11-06T09:31:50.737Z pushedAt=2026-11-13T06:45:51.386Z nl=1 -->

LightWeightSet can be used to store a series of values, and the value of each stored element is unique.

LightWeightSet is defined based on generics and adopts a lightweight structure. Its initial default capacity is 8, and each expansion doubles the original capacity.

The lookup of values in the set relies on the hash algorithm. Hash values are stored in an array, and then the corresponding storage location is mapped based on the hash value to obtain the value.

Both LightWeightSet and [HashSet](js-apis-hashset.md) are collection types used to store elements, but LightWeightSet occupies less memory.

**Recommended Use Scenarios:** When you need to store a group of unique elements, deduplicate data, or quickly look up elements based on hash, LightWeightSet is recommended. Compared with HashSet, LightWeightSet occupies less memory and is suitable for small-scale data storage and lookup in memory-sensitive scenarios.

This topic uses the following to identify the use of generics:

T: Type, which represents the type of elements stored in LightWeightSet.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - Container classes, implemented in static languages, have restrictions on storage locations and properties, and do not support custom properties or methods.

## Specifications

When the value stored in LightWeightSet is of the number type and is greater than INT32_MAX (2147483647) or less than INT32_MIN (-2147483648), the result of operations on LightWeightSet may be inconsistent with expectations.

This is because the storage structure changes in such cases.

For example, in the following example, for the calculation of value, 1758783600000 is greater than INT32_MAX, so it is stored through TaggedDouble; 1758783600 is within the INT32 range, so it is stored through TaggedInt. Due to the difference in the storage methods above, different hash values are calculated when the hash algorithm is applied, resulting in different mapping results and producing a phenomenon inconsistent with expectations.

```ts
let lightWeightSet = new LightWeightSet<number>();
let value = 1758783600000 / 1000;  // 1758783600000 > INT32_MAX
lightWeightSet.add(value);
console.info("result:", lightWeightSet.has(1758783600));  // result: false 
console.info("result:", lightWeightSet.has(value));  // result: true
```

## Modules to Import

```ts
import { LightWeightSet } from '@kit.ArkTS';
```

## LightWeightSet

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Number of elements in a LightWeightSet.|


### constructor

constructor()

A constructor used to create a **LightWeightSet** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200012 | The LightWeightSet's constructor cannot be directly invoked. |

**Example**

```ts
// Create a LightWeightSet instance.
let lightWeightSet = new LightWeightSet<number | string>();
```

### isEmpty

isEmpty(): boolean

Checks whether this LightWeightSet is empty (contains no element).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the LightWeightSet is empty; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**Example**

```ts
// Determine whether the container is empty.
const lightWeightSet = new LightWeightSet<number>();
let result = lightWeightSet.isEmpty();
console.info("result:", result);  // result: true
```

### add

add(obj: T): boolean

Adds data to the container. If the element to be added already exists in the container, it will not be added repeatedly, and false is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| obj | T | Yes | Member data to add. If the value to add already exists in the container, it will not be added again. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true if the element is added successfully, and returns false if the element to add already exists. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The add method cannot be bound. |

**Example**

```ts
// Add an element to the container.
let lightWeightSet = new LightWeightSet<string>();
let result = lightWeightSet.add("squirrel");
console.info("result:", result);  // result: true
```


### addAll

addAll(set: LightWeightSet&lt;T&gt;): boolean

Adds all elements of another container to the current container. If an element in the source container already exists in the current container, that element is skipped and not added repeatedly.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| set | [LightWeightSet&lt;T&gt;](#lightweightset) | Yes | LightWeightSet that provides added elements. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Operation result. The value **true** is returned if the element is added; otherwise, **false** is returned.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The addAll method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
let set = new LightWeightSet<string>();
set.add("gull");
// Add all elements of another container to the current container.
lightWeightSet.addAll(set);
let result = lightWeightSet.has("gull");
console.info("result:", result);  // result: true
```


### hasAll

hasAll(set: LightWeightSet&lt;T&gt;): boolean

Determines whether the container contains all elements in the specified set. When the value stored in the container is of the number type and is greater than INT32_MAX (2147483647) or less than INT32_MIN (-2147483648), the determination result may be inconsistent with expectations. For details, see [Specifications](#specifications).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| set | LightWeightSet&lt;T&gt; | Yes | Used to determine whether the current container contains all elements of the target set. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | true indicates that the container contains all elements in the target set, and false indicates that the container does not contain all elements in the target set. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The hasAll method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
let set = new LightWeightSet<string>();
set.add("sparrow");
// Determine whether the container contains all elements in the specified set.
let result = lightWeightSet.hasAll(set);
console.info("result:", result);  // result: true
```


### has

has(key: T): boolean

Determines whether the container contains the specified element.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | T | Yes | Specifies the element to find, used to determine whether the container contains this element. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | true indicates that the container contains the specified element, and false indicates that the container does not contain the specified element. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The has method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<number>();
lightWeightSet.add(123);
// Determine whether the container contains the specified element.
let result = lightWeightSet.has(123);
console.info("result:", result);  // result: true
```


### increaseCapacityTo

increaseCapacityTo(minimumCapacity: number): void

Increases the capacity of this LightWeightSet. If the passed-in capacity is greater than or equal to the number of elements in this LightWeightSet, the capacity is changed to the new capacity. If the passed-in capacity is less than the number of elements in this LightWeightSet, the capacity is not changed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| minimumCapacity | number | Yes | Number of elements to accommodate. If the passed value is less than the current number of elements, the capacity will not be changed. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of minimumCapacity is out of range. |
| 10200011 | The increaseCapacityTo method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
// Expand the container to the specified capacity.
lightWeightSet.increaseCapacityTo(10);
```


### getIndexOf

getIndexOf(key: T): number

Obtains the index corresponding to the specified element.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key| T | Yes| Key of the target element.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Index of the specified data in LightWeightSet. If the element to be found does not exist in LightWeightSet, a negative value is returned, indicating the position where the target hash value should be inserted. The insertion position is counted from 1, and the negative sign indicates that this is an insertion position rather than an index. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getIndexOf method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// Obtain the index of the specified element.
let result = lightWeightSet.getIndexOf("sparrow");
console.info("result:", result);  // result: 0
```


### remove

remove(key: T): T

Deletes and returns the specified element.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | T | Yes | Specifies the element to delete. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Returns the deleted element. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The remove method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// Delete and return the specified element.
let result = lightWeightSet.remove("sparrow");
console.info("result:", result);  // result: sparrow
```


### removeAt

removeAt(index: number): boolean

Removes the element at the specified position from this LightWeightSet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| index | number | Yes | Specified index, with a value range of [0, length-1], and must be less than or equal to INT32_MAX, that is, 2147483647. Returns false when the index is out of the valid range. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true if the element is successfully deleted, and returns false if the specified index does not exist or is out of range. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The removeAt method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// Delete the element at the specified index.
let result = lightWeightSet.removeAt(1);
console.info("result:", result);  // result: true
```


### getValueAt

getValueAt(index: number): T

Obtains the value of the element at the specified position in this LightWeightSet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| index | number | Yes | Specified index. Must be less than or equal to INT32_MAX, that is, 2147483647. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Returns the element value at the specified index. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getValueAt method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// Obtain the element corresponding to the specified index.
let result = lightWeightSet.getValueAt(1);
console.info("result:", result);  // result: squirrel
```


### clear

clear(): void

Clears this LightWeightSet and sets its length to **0**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The clear method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// Clear all elements in the container.
lightWeightSet.clear();
let result = lightWeightSet.isEmpty();
console.info("result:", result);  // result: true
```


### toString

toString(): String

Obtains a string containing all elements in the container.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| String | Returns a string containing all elements in this container. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// Obtain the string containing all elements in the container.
let result = lightWeightSet.toString();
console.info("result:", result);  // result: sparrow,squirrel
```


### toArray

toArray(): Array&lt;T&gt;

Obtains an array containing all elements in this container.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| Array&lt;T&gt; | Returns containing an array of all elements in this container. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The toArray method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// Obtain the array containing all objects in this container.
let result = lightWeightSet.toArray();
console.info(result.toString());
// sparrow,squirrel
```


### values

values(): IterableIterator&lt;T&gt;

Returns a new iterator object that contains all the values in this set.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Returns containing an iterator object of all values in LightWeightSet. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The values method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
// Obtain the iterator containing all elements.
let values = lightWeightSet.values();
for (let value of values) {
  console.info("value:", value);
}
// value: sparrow
// value: squirrel
```


### forEach

forEach(callbackFn: (value?: T, key?: T, set?: LightWeightSet&lt;T&gt;) => void, thisArg?: Object): void

Traverses the elements in the LightWeightSet instance object through a callback function.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function used to traverse the elements and their indexes on the LightWeightSet instance object. |
| thisArg | Object | No | Value used as this when callbackFn is called. Pass this parameter when the this reference in the callback function needs to be changed; it can be omitted when the this reference does not need to be changed. If not passed, the default value is the current instance object. |

callbackFn parameters
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | No | Value of the element currently being traversed. The default value is the value of the first element. |
| key | T | No | Element currently being traversed (same as value). The default value is the first element. |
| set | [LightWeightSet&lt;T&gt;](#lightweightset) | No | Instance object that currently calls the forEach method. The default value is the current instance object. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("sparrow");
lightWeightSet.add("gull");
// Traverse the elements in LightWeightSet through the callback function.
lightWeightSet.forEach((value: string, key: string) => {
  console.info("value:" + value, "key:" + key);
});
// value:gull key:gull
// value:sparrow key:sparrow
```

```ts
// You are not advised to use the add, remove, or removeAt APIs in forEach because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let lightWeightSet = new LightWeightSet<string>();
for (let i = 0; i < 10; i++) {
  lightWeightSet.add(i + "123");
}
for (let i = 0; i < 10; i++) {
  lightWeightSet.remove(i + "123");
}
```

### entries

entries(): IterableIterator<[T, T]>

Returns a new iterator object that contains all element pairs in this container. Each element pair consists of the same value [value, value].

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator<[T, T]> | Returns an iterator object containing all key-value pairs in LightWeightSet, where each item is an array in the [key, value] structure. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The entries method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
let entryIterator = lightWeightSet.entries();
for (let item of entryIterator) {
  console.info("value:", item[1])
}
// value: sparrow
// value: squirrel
```

```ts
// You are not advised to use the add, remove, or removeAt APIs in entries because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let lightWeightSet = new LightWeightSet<string>();
for(let i = 0; i < 10; i++) {
  lightWeightSet.add(i + "123");
}
for(let i = 0; i < 10; i++) {
  lightWeightSet.remove(i + "123");
}
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

Returns an iterator. Each item of the iterator is a JavaScript object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Returns an iterator object that traverses all elements in LightWeightSet, with each item being the element value in the container. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");

// Method 1:
for (let value of lightWeightSet) {
  console.info("value:", value);
}
// value: sparrow
// value: squirrel

// Method 2:
let symbolIterator = lightWeightSet[Symbol.iterator]();
let iteratorResult: IteratorResult<string> = symbolIterator.next();
while (!iteratorResult.done) {
  console.info("value:", iteratorResult.value);
  iteratorResult = symbolIterator.next();
}
// value: sparrow
// value: squirrel
```

```ts
// You are not advised to use the add, remove, or removeAt APIs in Symbol.iterator because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let lightWeightSet = new LightWeightSet<string>();
for (let i = 0; i < 10; i++) {
  lightWeightSet.add(i + "123");
}
for (let i = 0; i < 10; i++) {
  lightWeightSet.remove(i + "123");
}
```


### equal<sup>(deprecated)</sup>

equal(obj: Object): boolean

Checks whether the elements of this LightWeightSet are the same as those of **obj**.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 12. There is no alternative API.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| obj | Object | Yes | Object used to compare whether the element composition is the same as that of the current container. It can be a LightWeightSet or an array containing only string or number. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true when obj is a LightWeightSet or array containing only string or number, and the internal elements of the object are composed identically; returns false in other cases. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The equal method cannot be bound. |

**Example**

```ts
let lightWeightSet = new LightWeightSet<string>();
lightWeightSet.add("squirrel");
lightWeightSet.add("sparrow");
let comparisonArray = ["sparrow", "squirrel"];
// Determine whether this container has the same constituent elements as obj.
let result = lightWeightSet.equal(comparisonArray);
console.info("result:", result);  // result: true
```