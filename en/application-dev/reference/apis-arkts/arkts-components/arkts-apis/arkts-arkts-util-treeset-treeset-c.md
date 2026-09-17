# TreeSet

TreeSet is implemented based on TreeMap. In TreeSet, only value objects are processed. TreeSet can be used to store values, each of which must be unique.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { TreeSet } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

returns an ES6 iterator.Each item of the iterator is a Javascript Object

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;T&gt; |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The Symbol.iterator method cannot be bound. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
// Method 1:
for (let item of treeSet) {
  console.info("value:" + item);
}
// value:sparrow
// value:squirrel

// Method 2:
let iter = treeSet[Symbol.iterator]();
let temp: IteratorResult<string> = iter.next().value;
while(temp != undefined) {
  console.info("value:" + temp);
  temp = iter.next().value;
}
// value:sparrow
// value:squirrel
```

```TypeScript
// You are not advised to use the set or remove APIs in Symbol.iterator because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let treeSet = new TreeSet<string>();
for(let i = 0; i < 10; i++) {
  treeSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  treeSet.remove("sparrow" + i);
}
```

## add

```TypeScript
add(value: T): boolean
```

If the set does not contain the element, the specified element is added

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes | the element to add to the set |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | whether the element was already present |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The add method cannot be bound. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
let result = treeSet.add("squirrel");
console.info("result:", result); // result: true
```

## clear

```TypeScript
clear(): void
```

Clears all element groups in a set

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The clear method cannot be bound. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
treeSet.clear();
let result = treeSet.isEmpty();
console.info("result:", result); // result: true
```

## constructor

```TypeScript
constructor(comparator?: (firstValue: T, secondValue: T) => boolean)
```

A constructor used to create a TreeSet object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| comparator | (firstValue: T, secondValue: T) =&gt; boolean | No | comparator comparator (Optional) User-defined comparison functions. firstValue (required) previous element. secondValue (required) next element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The TreeSet's constructor cannot be directly invoked. |

**Examples**

```TypeScript
// Default constructor.
let treeSet = new TreeSet<string | number | boolean | Object>();
```

```TypeScript
// Use the comparator firstValue < secondValue if the elements are expected to be sorted in ascending order. Use firstValue > secondValue if the elements are expected to be sorted in descending order.
let treeSet: TreeSet<string> = new TreeSet<string>((firstValue: string, secondValue: string): boolean => {
  return firstValue < secondValue;
});
treeSet.add("a");
treeSet.add("c");
treeSet.add("d");
treeSet.add("b");
for (let value of treeSet) {
  console.info("value:", value);
}
// value: a
// value: b
// value: c
// value: d
```

```TypeScript
// When a custom type is inserted, a comparator must be provided.
class TestEntry{
  public id: number = 0;
}
let ts1: TreeSet<TestEntry> = new TreeSet<TestEntry>((t1: TestEntry, t2: TestEntry): boolean => {return t1.id > t2.id;});
let entry1: TestEntry = {
  id: 0
};
let entry2: TestEntry = {
  id: 1
}
ts1.add(entry1);
ts1.add(entry2);
console.info("treeSet: ", ts1.length);
```

## entries

```TypeScript
entries(): IterableIterator<[T, T]>
```

Returns a new Iterator object that contains the [key, value] pairs for each element in the Set object in insertion order

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[T, T]&gt; |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The entries method cannot be bound. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let it = treeSet.entries();
let t: IteratorResult<Object[]> = it.next();
while(!t.done) {
  console.info("TreeSet: " + t.value[1]);
  t = it.next()
}
// TreeSet: sparrow
// TreeSet: squirrel
```

```TypeScript
// You are not advised to use the set or remove APIs in entries because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let treeSet = new TreeSet<string>();
for(let i = 0; i < 10; i++) {
  treeSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  treeSet.remove("sparrow" + i);
}
```

## forEach

```TypeScript
forEach(callbackFn: (value?: T, key?: T, set?: TreeSet<T>) => void, thisArg?: Object): void
```

Executes a provided function once for each value in the Set object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value?: T, key?: T, set?: TreeSet&lt;T&gt;) =&gt; void | Yes | callbackFn callbackFn (required) A function that accepts up to three arguments. The function to be called for each element. |
| thisArg | Object | No | thisArg thisArg (Optional) The value to be used as this value for when callbackFn is called. If thisArg is omitted, undefined is used as the this value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The forEach method cannot be bound. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("sparrow");
treeSet.add("gull");
treeSet.forEach((value: string, key: string): void => {
  console.info("value:" + value);
});
// value:gull
// value:sparrow
```

```TypeScript
// You are not advised to use the set or remove APIs in forEach because they may cause unpredictable risks such as infinite loops. You can use the for loop when inserting or deleting data.
let treeSet = new TreeSet<string>();
for(let i = 0; i < 10; i++) {
  treeSet.add("sparrow" + i);
}
for(let i = 0; i < 10; i++) {
  treeSet.remove("sparrow" + i);
}
```

## getFirstValue

```TypeScript
getFirstValue(): T
```

Gets the first elements in a set

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T | value or undefined |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getFirstValue method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-empty-container) | Container is empty.<br>**Applicable version:** 23 and later  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let result = treeSet.getFirstValue();
console.info("result:", result); // result: sparrow
```

## getHigherValue

```TypeScript
getHigherValue(key: T): T
```

Returns the least element greater than or equal to the specified key if the key does not exist, undefined is returned

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | T | Yes | the key to compare against |

**Return value:**

| Type | Description |
| --- | --- |
| T | key or undefined |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getHigherValue method cannot be bound. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
treeSet.add("gander");
let result = treeSet.getHigherValue("sparrow");
console.info("result:", result); // result: squirrel
```

## getLastValue

```TypeScript
getLastValue(): T
```

Gets the last elements in a set

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T | value or undefined |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getLastValue method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-empty-container) | Container is empty.<br>**Applicable version:** 23 and later  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let result = treeSet.getLastValue();
console.info("result:", result); // result: squirrel
```

## getLowerValue

```TypeScript
getLowerValue(key: T): T
```

Returns the greatest element smaller than or equal to the specified key if the key does not exist, undefined is returned

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | T | Yes | the key to compare against |

**Return value:**

| Type | Description |
| --- | --- |
| T | key or undefined |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getLowerValue method cannot be bound. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
treeSet.add("gander");
let result = treeSet.getLowerValue("sparrow");
console.info("result:", result); // result: gander
```

## has

```TypeScript
has(value: T): boolean
```

Returns whether the Set object contains the elements

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes | the value to check for presence in the set |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The has method cannot be bound. |

**Examples**

```TypeScript
let treeSet  = new TreeSet<number>();
treeSet.add(123);
let result = treeSet.has(123);
console.info("result:", result); // result: true
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

Returns whether the Set object contains elements

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The isEmpty method cannot be bound. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
let result = treeSet.isEmpty();
console.info("result:", result);  // result: true
```

## popFirst

```TypeScript
popFirst(): T
```

Return and delete the first element, returns undefined if tree set is empty

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T | first value or undefined |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The popFirst method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-empty-container) | Container is empty.<br>**Applicable version:** 23 and later  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let result = treeSet.popFirst();
console.info("result:", result); // result: sparrow
```

## popLast

```TypeScript
popLast(): T
```

Return and delete the last element, returns undefined if tree set is empty

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T | last value or undefined |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The popLast method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-empty-container) | Container is empty.<br>**Applicable version:** 23 and later  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let result = treeSet.popLast();
console.info("result:", result); // result: squirrel
```

## remove

```TypeScript
remove(value: T): boolean
```

Remove a specified element from a Set object

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes | the element to remove from the set |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | the boolean type(Is there contain this element) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The remove method cannot be bound. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let result = treeSet.remove("sparrow");
console.info("result:", result); // result: true
```

## values

```TypeScript
values(): IterableIterator<T>
```

Returns a new Iterator object that contains the values contained in this set

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;T&gt; |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The values method cannot be bound. |

**Examples**

```TypeScript
let treeSet = new TreeSet<string>();
treeSet.add("squirrel");
treeSet.add("sparrow");
let values = treeSet.values();
for (let value of values) {
  console.info("value:", value)
}
// value: sparrow
// value: squirrel
```

## length

```TypeScript
length: number
```

Gets the element number of the TreeSet.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
