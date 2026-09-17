# ArrayList

ArrayList is a linear data structure that is implemented based on arrays. ArrayList can dynamically adjust the capacity based on project requirements. It increases the capacity by 50% each time.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { ArrayList } from '@kit.ArkTS';
import { ArrayListComparatorFn } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

Obtains an iterator, each item of which is a JavaScript object.

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
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);

// Method 1:
for (let value of arrayList) {
  console.info("value:", value);
}
// value: 2
// value: 4
// value: 5
// value: 4

// Method 2:
let iter = arrayList[Symbol.iterator]();
let temp: IteratorResult<number> = iter.next();
while(!temp.done) {
  console.info("value:", temp.value);
  temp = iter.next();
}
// value: 2
// value: 4
// value: 5
// value: 4
```

## add

```TypeScript
add(element: T): boolean
```

Adds an element at the end of this ArrayList.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if the element is added; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The add method cannot be bound. |

**Examples**

```TypeScript
class C1 {
  name: string = ""
  age: string = ""
}
let arrayList = new ArrayList<string | number | boolean | Array<number> | C1>();
arrayList.add("a");
arrayList.add(1);
let b = [1, 2, 3];
arrayList.add(b);
let c : C1 = {name: "Dylan", age: "13"}
let result1 = arrayList.add(c);
let result2 = arrayList.add(false);
console.info("result1:", result1);  // result1: true
console.info("result2:", result2);  // result2: true
console.info("length:", arrayList.length);  // length: 5
```

## clear

```TypeScript
clear(): void
```

Clears this ArrayList and sets its length to **0**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The clear method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.clear();
```

## clone

```TypeScript
clone(): ArrayList<T>
```

Clones this ArrayList and returns a copy. The modification to the copy does not affect the original instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [ArrayList](arkts-arkts-util-arraylist-arraylist-c.md)&lt;T&gt; | New **ArrayList** instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The clone method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result:  ArrayList<number> = arrayList.clone();
console.info("result = ", result.length); // result = 4
```

## constructor

```TypeScript
constructor()
```

A constructor used to create an **ArrayList** instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The ArrayList's constructor cannot be directly invoked. |

**Examples**

```TypeScript
let arrayList = new ArrayList<string | number>();
```

## convertToArray

```TypeScript
convertToArray(): Array<T>
```

Converts this ArrayList into an array.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Array obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The convertToArray method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: Array<number> = arrayList.convertToArray();
console.info("result = ", result); // result =  2,4,5,4
```

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, arrlist?: ArrayList<T>) => void, thisArg?: Object): void
```

Uses a callback to traverse each element in the **ArrayList** instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, arrlist?: ArrayList&lt;T&gt;) =&gt; void | Yes | Callback invoked for the replacement. |
| thisArg | Object | No | Value of **this** to use when **callbackFn** is invoked. The default value is this instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The forEach method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.forEach((value: number, index?: number) => {
  console.info("value:" + value, "index:" + index);
});
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3
```

## getCapacity

```TypeScript
getCapacity(): number
```

Obtains the capacity of this ArrayList.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Capacity obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getCapacity method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: number = arrayList.getCapacity();
console.info("result = ", result); // result = 10
```

## getIndexOf

```TypeScript
getIndexOf(element: T): number
```

Obtains the index of the first occurrence of the specified element in this ArrayList.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the position index if obtained; returns **-1** if the specified element is not found. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getIndexOf method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(2);
arrayList.add(1);
arrayList.add(2);
arrayList.add(4);
let result: number = arrayList.getIndexOf(2); 
console.info("result = ", result); // result = 0
```

## getLastIndexOf

```TypeScript
getLastIndexOf(element: T): number
```

Obtains the index of the last occurrence of the specified element in this ArrayList.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the position index if obtained; returns **-1** if the specified element is not found. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getLastIndexOf method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(2);
arrayList.add(1);
arrayList.add(2);
arrayList.add(4);
let result: number = arrayList.getLastIndexOf(2);
console.info("result = ", result); // result = 5
```

## has

```TypeScript
has(element: T): boolean
```

Checks whether this ArrayList has the specified element.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the specified element is contained; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The has method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<string>();
arrayList.add("squirrel");
let result: boolean = arrayList.has("squirrel");
console.info("result:", result);  // result: true
```

## increaseCapacityTo

```TypeScript
increaseCapacityTo(newCapacity: number): void
```

Increases the capacity of this ArrayList.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newCapacity | number | Yes | New capacity. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The increaseCapacityTo method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.increaseCapacityTo(2);
arrayList.increaseCapacityTo(8);
console.info("result = ", arrayList.length); // result = 4
```

## insert

```TypeScript
insert(element: T, index: number): void
```

Inserts an element at a specified index within the length range. If index is out of range, the insertion fails.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |
| index | number | Yes | Index of the position where the element is to be inserted. The value must be less than or equal to int32_max, that is, 2147483647. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The insert method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number | string | boolean>();
arrayList.insert("A", 0);
arrayList.insert(0, 1);
arrayList.insert(true, 2);
console.info("length:", arrayList.length);  // length: 3
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

Checks whether this ArrayList is empty (contains no element).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the ArrayList is empty; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The isEmpty method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: boolean = arrayList.isEmpty();
console.info("result = ", result); // result =  false
```

## remove

```TypeScript
remove(element: T): boolean
```

Removes the first occurrence of the specified element from this ArrayList.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if the element is removed; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The remove method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: boolean = arrayList.remove(2);
console.info("result = ", result); // result =  true
```

## removeByIndex

```TypeScript
removeByIndex(index: number): T
```

Removes an element with the specified position from this ArrayList.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the target element. The value must be less than or equal to int32_max, that is, 2147483647. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Element removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of "index" is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The removeByIndex method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(2);
arrayList.add(4);
let result: number = arrayList.removeByIndex(2);
console.info("result = ", result); // result = 5
```

## removeByRange

```TypeScript
removeByRange(fromIndex: number, toIndex: number): void
```

Removes elements within the range [fromIndex, toIndex).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fromIndex | number | Yes | Index of the start position. |
| toIndex | number | Yes | Index of the end position. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of fromIndex or toIndex is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The removeByRange method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.removeByRange(2, 4);
```

## replaceAllElements

```TypeScript
replaceAllElements(callbackFn: (value: T, index?: number, arrlist?: ArrayList<T>) => T, thisArg?: Object): void
```

Replaces all elements in this ArrayList with new elements, and returns the new ones.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, arrlist?: ArrayList&lt;T&gt;) =&gt; T | Yes | Callback invoked for the replacement. |
| thisArg | Object | No | Value of **this** to use when **callbackFn** is invoked. The default value is this instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The replaceAllElements method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.replaceAllElements((value: number): number => {
  // Add the user operation logic based on the actual scenario.
  return value;
});
```

## sort

```TypeScript
sort(comparator?: ArrayListComparatorFn<T>): void
```

Sorts elements in an ArrayList according to the order defined by the specified comparator.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| comparator | [ArrayListComparatorFn](arkts-arkts-arraylistcomparatorfn-t.md)&lt;T&gt; | No | Callback invoked for sorting. The default value is the callback function for sorting elements in ascending order.<br> There has been a compatibility change since API version 2 3. In API version 22 and earlier versions, the type is `(firstValue: T, secondValue: T) =&gt; number`.<br>**Since:** 23 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The sort method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.sort((a: number, b: number) => a - b);
arrayList.sort((a: number, b: number) => b - a);
arrayList.sort();
```

## subArrayList

```TypeScript
subArrayList(fromIndex: number, toIndex: number): ArrayList<T>
```

Obtains elements from this **ArrayList** within the range [fromIndex, toIndex) and returns them as a new ArrayList instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fromIndex | number | Yes | Index of the start position. |
| toIndex | number | Yes | Index of the end position. |

**Return value:**

| Type | Description |
| --- | --- |
| [ArrayList](arkts-arkts-util-arraylist-arraylist-c.md)&lt;T&gt; | New **ArrayList** instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of fromIndex or toIndex is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The subArrayList method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: ArrayList<number> = arrayList.subArrayList(2, 4);
console.info("result = ", result.length); // result = 2
```

## trimToCurrentLength

```TypeScript
trimToCurrentLength(): void
```

Releases the reserved space in this ArrayList by adjusting the capacity to the actual number of elements in it.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The trimToCurrentLength method cannot be bound. |

**Examples**

```TypeScript
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.trimToCurrentLength();
console.info("result = ", arrayList.length); // result = 4
```

## [index: int]

```TypeScript
[index: number]: T
```

Returns the element at the given index.

**Type:** T

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## length

```TypeScript
length: number
```

Number of elements in an ArrayList.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
