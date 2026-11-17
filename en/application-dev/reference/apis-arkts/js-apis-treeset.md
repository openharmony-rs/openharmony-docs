# @ohos.util.TreeSet (Nonlinear Container TreeSet)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=fff9bf5149feb6115df0d71aed30fc3b080f14ff translatedAt=2026-11-06T09:41:45.468Z pushedAt=2026-11-13T07:02:05.228Z nl=1 -->

TreeSet is implemented based on [TreeMap](js-apis-treemap.md). In TreeSet, only the value of an element is processed, and the key is not processed separately. Each element in TreeSet is stored as both the key and the value in the underlying TreeMap, so the values of elements are unique and ordered. For details about the implementation mechanism of TreeMap, see [TreeMap](js-apis-treemap.md).

Neither TreeSet nor [HashSet](js-apis-hashset.md) allows duplicate elements. Data in HashSet is stored in an unordered manner, while data in TreeSet is stored in an ordered manner. HashSet allows inserting null values, but TreeSet does not recommend inserting null values, as they may affect the sorting result.

**Recommended use cases:** TreeSet is suitable for scenarios that require ordered storage and traversal of a set, such as ordered data display, ranking and sorting systems, scenarios that require obtaining adjacent elements in sorted order, or automatic sorted insertion.

This topic uses the following to identify the use of generics:

- T: Type, which indicates the type of elements in TreeSet.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Container classes, implemented in static languages, have restrictions on storage locations and properties, and do not support custom properties or methods.


## Modules to Import

```ts
import { TreeSet } from '@kit.ArkTS';
```

## TreeSet

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Number of elements in a TreeSet.|


### constructor

constructor(comparator?: (firstValue: T, secondValue: T) => boolean)

Constructor of TreeSet, which supports sorting elements in ascending or descending order through a comparator. When inserting a custom type, a comparator must be provided.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| comparator | function | No | User-defined comparator function that can sort elements by comparison relationship. The default value is null, indicating that no comparator function is provided. Value principle: the return value of the comparator function determines the sort direction. Returning firstValue < secondValue means ascending order, and returning firstValue > secondValue means descending order. |

comparator parameters

| Name| Type| Mandatory| Description|
| ------| ---- | ----- | -- |
| firstValue | T | Yes | The first element to be compared in the comparator, which determines the sort order together with secondValue. |
| secondValue | T | Yes | The second element to be compared in the comparator, which determines the sort order together with firstValue. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200012 | The TreeSet's constructor cannot be directly invoked. |

**Example**

```ts
// Default constructor
let treeSet = new TreeSet<string | number | boolean | Object>();
```

```ts
// Use comparator firstValue < secondValue to indicate that the expected result is in ascending order. Conversely, firstValue > secondValue indicates descending order.
let treeSet: TreeSet<string> = new TreeSet<string>((firstValue: string, secondValue: string): boolean => {
  return firstValue < secondValue;
});
treeSet.add('a');
treeSet.add('c');
treeSet.add('d');
treeSet.add('b');
for (let value of treeSet) {
  console.info('value:', value);
};
// value: a
// value: b
// value: c
// value: d
```

```ts
// When inserting a custom type, provide a comparator.
class TestEntry {
  public id: number = 0;
}
let testEntrySet: TreeSet<TestEntry> = new TreeSet<TestEntry>((t1: TestEntry, t2: TestEntry): boolean => { return t1.id > t2.id; });
let firstEntry: TestEntry = {
  id: 0
};
let secondEntry: TestEntry = {
  id: 1
}
testEntrySet.add(firstEntry);
testEntrySet.add(secondEntry);
console.info('treeSet: ', testEntrySet.length);
```


### isEmpty

isEmpty(): boolean

Checks whether this TreeSet is empty (contains no element).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns **true** if the TreeSet is empty; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
// Check whether the container is empty.
let result = treeSet.isEmpty();
console.info('result:', result);  // result: true
```


### has

has(value: T): boolean

Checks whether this TreeSet has the specified value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes | Target element to check whether it exists in the container. |

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
let treeSet = new TreeSet<number>();
treeSet.add(123);
// Determine whether the container contains the specified element.
let result = treeSet.has(123);
console.info('result:', result); // result: true
```

### getFirstValue

getFirstValue(): T

Obtains the first element in the container in sorted order. Returns undefined if the container is empty.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Value obtained. If nothing is obtained, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getFirstValue method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.getFirstValue();
console.info('result:', result); // result: sparrow
```


### getLastValue

getLastValue(): T

Obtains the value of the last element in this TreeSet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Value obtained. If nothing is obtained, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getLastValue method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.getLastValue();
console.info('result:', result); // result: squirrel
```


### add

add(value: T): boolean

Adds a specified element to the container. Inserting null values is not recommended, as they may affect the sorting result. When adding elements of a custom type, ensure that a comparator has been provided when TreeSet is constructed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes | Value element to add to the TreeSet. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true if the new element is successfully added to the container, and false if the element already exists. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The add method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
let result = treeSet.add('squirrel');
console.info('result:', result); // result: true
```


### remove

remove(value: T): boolean

Removes the element with the specified key from this TreeSet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes | Target element to remove from the container. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true if the element is successfully deleted, and returns false if the specified element does not exist. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The remove method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.remove('sparrow');
console.info('result:', result); // result: true
```


### getLowerValue

getLowerValue(key: T): T

Obtains the value that is placed in front of the input key in this TreeSet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | T | Yes | Element value used as the search reference, used to locate the data one position ahead of this element in the sort order. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Returns the data of the element before the input element in the sorting. Returns undefined if it is empty. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getLowerValue method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
treeSet.add('gander');
let result = treeSet.getLowerValue('sparrow');
console.info('result:', result); // result: gander
```


### getHigherValue

getHigherValue(key: T): T

Obtains the value that is placed next to the input key in this TreeSet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| key | T | Yes | Element used as the search reference, used to locate the data that is one position after this element in the sort order. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Value obtained. If nothing is obtained, **undefined** is returned.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getHigherValue method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
treeSet.add('gander');
let result = treeSet.getHigherValue('sparrow');
console.info('result:', result); // result: squirrel
```


### popFirst

popFirst(): T

Removes the first element in this TreeSet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Element removed. If nothing is obtained, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The popFirst method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.popFirst();
console.info('result:', result); // result: sparrow
```


### popLast

popLast(): T

Removes the last element in this TreeSet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Element removed. If nothing is obtained, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The popLast method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let result = treeSet.popLast();
console.info('result:', result); // result: squirrel
```


### clear

clear(): void

Clears this TreeSet and sets its length to **0**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The clear method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
treeSet.clear();
let result = treeSet.isEmpty();
console.info('result:', result); // result: true
```


### values

values(): IterableIterator&lt;T&gt;

Returns a new iterator object containing the element values in this container.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Returns an iterator containing all elements in the TreeSet. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The values method cannot be bound. |

**Example**

```ts
// Avoid using add and remove methods in values, which may cause unpredictable risks such as infinite loops. Use a for loop for insertion and deletion.
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
let values = treeSet.values();
for (let value of values) {
  console.info('value:', value);
}
// value: sparrow
// value: squirrel
```


### forEach

forEach(callbackFn: (value?: T, key?: T, set?: TreeSet&lt;T&gt;) => void, thisArg?: Object): void

Traverses the elements on the instance object through a callback function.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function invoked when traversing each element in the instance object. Developers can perform custom processing on the element and its index in the callback. |
| thisArg | Object | No | Value used as this when callbackFn is invoked. If not passed, the default value is undefined. |

> **NOTE**
>
> The `thisArg` parameter is not recommended. In ArkTS, the `this` of an arrow function is determined by the outer context, and `thisArg` cannot change the `this` in the callback function. In a normal function, `this` is not allowed. Therefore, this parameter does not actually take effect. If you need to access an external object in the callback function, it is recommended to reference it directly in the arrow function.

callbackFn
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | No | Currently traversed value element. This parameter is always passed when forEach invokes the callback. |
| key | T | No | Currently traversed element (in TreeSet, key and value are the same, both being the element itself). |
| set | TreeSet&lt;T&gt; | No | Instance object that currently invokes the forEach method. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
treeSet.add('sparrow');
treeSet.add('gull');
// Traverse the elements in TreeSet through forEach.
treeSet.forEach((value: string, key: string): void => {
  console.info('value:' + value);
});
// value:gull
// value:sparrow
```
```ts
// It is not recommended to use add and remove in forEach, which may cause unpredictable risks such as infinite loops. Use a for loop for insertion and deletion.
let treeSet = new TreeSet<string>();
for (let i = 0; i < 10; i++) {
  treeSet.add('sparrow' + i);
}
for (let i = 0; i < 10; i++) {
  treeSet.remove('sparrow' + i);
}
```

### entries

entries(): IterableIterator<[T, T]>

Returns a new iterator object containing the elements in this container, with each element returned in the form of [value, value].

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator<[T, T]> | Returns an iterator object containing all key-value pairs in the TreeSet, where the key and value in each key-value pair are the same, both being the element itself. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The entries method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
// Obtain the entries iterator.
let iterator = treeSet.entries();
// Traverse the iterator to obtain key-value pairs.
let iterResult: IteratorResult<Object[]> = iterator.next();
while (!iterResult.done) {
  console.info('TreeSet: ' + iterResult.value[1]);
  iterResult = iterator.next();
}
// TreeSet: sparrow
// TreeSet: squirrel
```

```ts
// Do not use add or remove in entries, which may cause unpredictable risks such as infinite loops. Use a for loop for insertion and deletion.
let treeSet = new TreeSet<string>();
for(let i = 0; i < 10; i++) {
  treeSet.add('sparrow' + i);
}
for(let i = 0; i < 10; i++) {
  treeSet.remove('sparrow' + i);
}
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

Returns an iterator, where each item is an element value in the container.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Returns an iterator containing all elements in the TreeSet. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
let treeSet = new TreeSet<string>();
treeSet.add('squirrel');
treeSet.add('sparrow');
// Method 1: Use the for...of syntax to traverse the TreeSet.
for (let item of treeSet) {
  console.info('value:' + item);
}
// value:sparrow
// value:squirrel

// Method 2: Obtain an iterator through Symbol.iterator for manual traversal.
let iterator = treeSet[Symbol.iterator]();
let currentValue: IteratorResult<string> = iterator.next().value;
while (currentValue != undefined) {
  console.info('value:' + currentValue);
  currentValue = iterator.next().value;
}
// value:sparrow
// value:squirrel
```

```ts
// Avoid using the add and remove methods in Symbol.iterator, as this may cause unpredictable risks such as infinite loops. Use a for loop for insertion and deletion instead.
let treeSet = new TreeSet<string>();
for (let i = 0; i < 10; i++) {
  treeSet.add('sparrow' + i);
}
for (let i = 0; i < 10; i++) {
  treeSet.remove('sparrow' + i);
}
```