# List

```TypeScript
declare class List<T>
```

List is implemented based on the singly linked list. Each node has a reference pointing to the next element. When querying an element, the system traverses the list from the beginning.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { List } from '@kit.ArkTS';
import { ListComparatorFn } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

returns an iterator.Each item of the iterator is a Javascript Object

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
let list = new List<number>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);

// Method 1:
for (let item of list) {
  console.info("value: " + item);
}
// value: 2
// value: 4
// value: 5
// value: 4

// Method 2:
let iter = list[Symbol.iterator]();
let temp: IteratorResult<number> = iter.next();
while(!temp.done) {
  console.info("value: " + temp.value);
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

Adds an element at the end of this List.

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
let list = new List<string | number | boolean | object>();
let result1 = list.add("a");
let result2 = list.add(1);
let b = [1, 2, 3];
let result3 = list.add(b);
class C {
  name: string = ''
  age: string = ''
}
let c: C = {name : "Dylan", age : "13"};
let result4 = list.add(c);
let result5 = list.add(false);
console.info("result = ", result5) // result =  true
```

## clear

```TypeScript
clear(): void
```

Clears this List and sets its length to **0**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The clear method cannot be bound. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(4);
list.clear();
let result = list.isEmpty();
console.info("result:", result);  // result: true
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **List** instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The List's constructor cannot be directly invoked. |

**Examples**

```TypeScript
let list = new List<string | number | boolean | object>();
```

## convertToArray

```TypeScript
convertToArray(): Array<T>
```

Converts this List into an array and returns the array.

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
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.convertToArray();
console.info("result:", result);  // result: 2,4,5,4
```

## equal

```TypeScript
equal(obj: Object): boolean
```

Compares whether a specified object is equal to this List.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | Object | Yes | Object used for comparison. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the two are equal; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The equal method cannot be bound. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
let obj = new List<number>();
obj.add(2);
obj.add(4);
obj.add(5);
let result = list.equal(obj);
console.info("result:", result);  // result: true
```

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, List?: List<T>) => void, thisArg?: Object): void
```

Uses a callback to traverse each element in the **List** instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, List?: List&lt;T&gt;) =&gt; void | Yes | Callback used to return the result. |
| thisArg | Object | No | Value of **this** to use when **callbackFn** is invoked. The default value is this instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The forEach method cannot be bound. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(4);
list.forEach((value: number, index: number) => {
  console.info("value:" + value, "index:" + index);
});
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3
```

## get

```TypeScript
get(index: number): T
```

Obtains the element at the specified position in this List.

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
| T | Element obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The get method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range.<br>**Applicable version:** 23 and later  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(2);
list.add(1);
list.add(2);
list.add(4);
let result = list.get(2);
console.info("result:", result);  // result: 5
```

## getFirst

```TypeScript
getFirst(): T
```

Obtains the first element in this List.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T | The first element obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getFirst method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-empty-container) | Container is empty.<br>**Applicable version:** 23 and later  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.getFirst();
console.info("result:", result);  // result: 2
```

## getIndexOf

```TypeScript
getIndexOf(element: T): number
```

Obtains the index of the first occurrence of the specified element in this List.

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
| number | Index of the element. If no match is found, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getIndexOf method cannot be bound. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(2);
list.add(1);
list.add(2);
list.add(4);
let result = list.getIndexOf(2);
console.info("result:", result); // result: 0
```

## getLast

```TypeScript
getLast(): T
```

Obtains the last element in this List.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T | The last element obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getLast method cannot be bound. |
| [10200010](../errorcode-utils.md#10200010-empty-container) | Container is empty.<br>**Applicable version:** 23 and later  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.getLast();
console.info("result:", result);  // result: 4
```

## getLastIndexOf

```TypeScript
getLastIndexOf(element: T): number
```

Obtains the index of the last occurrence of the specified element in this List.

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
| number | Index of the element. If no match is found, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getLastIndexOf method cannot be bound. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(2);
list.add(1);
list.add(2);
list.add(4);
let result = list.getLastIndexOf(2);
console.info("result:", result); // result: 5
```

## getSubList

```TypeScript
getSubList(fromIndex: number, toIndex: number): List<T>
```

Obtains elements within a range in this List, including the element at the start position but not that at the end position, and returns these elements as a new **List** instance.

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
| [List](arkts-arkts-util-list-list-c.md)&lt;T&gt; | New **List** instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getSubList method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of fromIndex or toIndex is out of range. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(6);
list.add(8);
let result = list.getSubList(1, 3);
console.info("result:", result.convertToArray());  // result: 4,6
```

## has

```TypeScript
has(element: T): boolean
```

Checks whether this List has the specified element.

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
| boolean | Operation result. The value **true** is returned if the specified element is contained; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The has method cannot be bound. |

**Examples**

```TypeScript
let list = new List<string>();
list.add("squirrel");
let result = list.has("squirrel");
console.info("result:", result);  // result: true
```

## insert

```TypeScript
insert(element: T, index: number): void
```

Inserts an element at the specified position in this List.

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
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The insert method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

**Examples**

```TypeScript
let list = new List<string | number | boolean>();
list.insert("A", 0);
list.insert(0, 1);
list.insert(true, 2);
console.info("result:", list.get(1));  // result: 0
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

Checks whether this List is empty (contains no element).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the List is empty; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The isEmpty method cannot be bound. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.isEmpty();
console.info("result:", result);  // result: false
```

## remove

```TypeScript
remove(element: T): boolean
```

Removes the first occurrence of the specified element from this List.

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
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.remove(2);
console.info("result:", result);  // result: true
```

## removeByIndex

```TypeScript
removeByIndex(index: number): T
```

Searches for an element based on its index and then removes it.

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
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The removeByIndex method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(2);
list.add(4);
let result = list.removeByIndex(2);
console.info("result:", result);  // result: 5
```

## replaceAllElements

```TypeScript
replaceAllElements(callbackFn: (value: T, index?: number, list?: List<T>) => T, thisArg?: Object): void
```

Replaces all elements in this List with new elements, and returns the new ones.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, list?: List&lt;T&gt;) =&gt; T | Yes | Callback invoked for the replacement. |
| thisArg | Object | No | Value of **this** to use when **callbackFn** is invoked. The default value is this instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The replaceAllElements method cannot be bound. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(4);
list.add(5);
list.add(4);
list.replaceAllElements((value: number) => {
  // Add the user operation logic based on the actual scenario.
  if (value === 5) {
    return value * 2;
  }
  return value;
});

console.info("result:", list.get(2));  // result: 10
```

## set

```TypeScript
set(index: number, element: T): T
```

Replaces an element at the specified position in this List with a given element.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the target element. The value must be less than or equal to int32_max, that is, 2147483647. |
| element | T | Yes | Element to be used for replacement. |

**Return value:**

| Type | Description |
| --- | --- |
| T | New element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The set method cannot be bound. |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

**Examples**

```TypeScript
let list = new List<number | string>();
list.add(2);
list.add(4);
list.add(5);
list.add(4);
let result = list.set(2, "b");
console.info("result:", JSON.stringify(list));  // result: {"0":2,"1":4,"2":"b","3":4}
```

## sort

```TypeScript
sort(comparator: ListComparatorFn<T>): void
```

Sorts elements in this List.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| comparator | [ListComparatorFn](arkts-arkts-listcomparatorfn-t.md)&lt;T&gt; | Yes | Callback used to return the result.<br> There has been a compatibility change since API version 23. In API version 22 and earlier versions, the type is `(firstValue: T, secondValue: T) =&gt; number`.<br>**Since:** 23 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The sort method cannot be bound. |

**Examples**

```TypeScript
let list = new List<number>()
list.add(2);
list.add(1);
list.add(3);
list.add(4);
list.sort((a: number, b: number) => a - b);  // The elements are sorted in ascending order.
console.info("result:", list.convertToArray());  // result: 1,2,3,4

list.sort((a: number, b: number) => b - a);  // The elements are sorted in descending order.
console.info("result:", list.convertToArray());  // result: 4,3,2,1
```

## length

```TypeScript
length: number
```

Number of elements in a List.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
