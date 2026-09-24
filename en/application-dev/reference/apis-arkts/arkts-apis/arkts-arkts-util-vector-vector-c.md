# Vector

```TypeScript
declare class Vector<T>
```

Vector is a linear data structure that is implemented based on arrays. When the memory of a vector is used up, a larger contiguous memory area is automatically allocated, all the elements are copied to the new memory area, and the current memory area is reclaimed. Vector can be used to efficiently access elements. Both Vector and [ArrayList](arkts-arkts-util-arraylist-arraylist-c.md) are implemented based on arrays, but Vector provides more interfaces for operating the arrays. Both of them can dynamically adjust the capacity. Vector doubles the capacity each time, whereas ArrayList increases the capacity by 50%. **Recommended use case**: Use Vector when the data volume is large. This topic uses the following to identify the use of generics:

- T: Type

> **NOTE:** 
> 
> - The APIs provided by this module are deprecated since API version 9. You are advised to use [@ohos.util.ArrayList](arkts-arkts-util-arraylist-arraylist-c.md).

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [ArrayList](arkts-arkts-util-arraylist-arraylist-c.md)

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { Vector } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

returns an ES6 iterator.Each item of the iterator is a Javascript Object

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;T&gt; |  |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// Method 1:
let nums: Array<number> =  vector.convertToArray()
for (let item of nums) {
  console.info("value:" + item);
}

// Method 2:
let iter = vector[Symbol.iterator]();
let temp: IteratorResult<number> = iter.next().value;
while(temp != undefined) {
  console.info("value:" + temp);
  temp = iter.next().value;
}
```

## add

```TypeScript
add(element: T): boolean
```

Adds an element at the end of this Vector.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if the element is added; otherwise, **false** is returned. |

**Examples**

```TypeScript
class C1 {
  name: string = ""
  age: string = ""
}
let vector : Vector<string | number | C1 | Array<number>> = new Vector();
let result = vector.add("a");
let result1 = vector.add(1);
let b = [1, 2, 3];
let result2 = vector.add(b);
let c: C1 = {name : "Jack", age : "13"};
let result3 = vector.add(c);
```

## clear

```TypeScript
clear(): void
```

Clears all elements in this Vector and sets its length to **0**.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.clear();
```

## clone

```TypeScript
clone(): Vector<T>
```

Clones this Vector and returns a copy. The modification to the copy does not affect the original instance.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Vector](arkts-arkts-util-vector-vector-c.md)&lt;T&gt; | New **Vector** instance obtained. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.clone();
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **Vector** instance.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let vector : Vector<string | number | Array<number>> = new Vector();
```

## convertToArray

```TypeScript
convertToArray(): Array<T>
```

Converts this Vector into an array.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Array obtained. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.convertToArray();
```

## copyToArray

```TypeScript
copyToArray(array: Array<T>): void
```

Copies elements in this Vector into an array to overwrite elements of the same position indexes.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | Array&lt;T&gt; | Yes | Array to which the elements in the Vector will be copied. |

## forEach

```TypeScript
forEach(callbackFn: (value: T, index?: number, vector?: Vector<T>) => void, thisArg?: Object): void
```

Uses a callback to traverse the elements in this Vector and obtain their position indexes.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, vector?: Vector&lt;T&gt;) =&gt; void | Yes | Callback invoked for replacement. |
| thisArg | Object | No | Value of **this** to use when **callbackFn** is invoked. The default value is this instance. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.forEach((value : number, index ?: number) : void => {
  console.info("value:" + value, "index:" + index);
});
```

## get

```TypeScript
get(index: number): T
```

Obtains an element at the specified position in this Vector.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the target element. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Element obtained. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.get(2);
```

## getCapacity

```TypeScript
getCapacity(): number
```

Obtains the capacity of this Vector.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Capacity obtained. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getCapacity();
```

## getFirstElement

```TypeScript
getFirstElement(): T
```

Obtains the first element in this Vector.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T | The first element obtained. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getFirstElement();
```

## getIndexFrom

```TypeScript
getIndexFrom(element: T, index: number): number
```

Searches for an element forward from the specified position index and returns the position index of the element.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |
| index | number | Yes | Position index where the search starts. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the element. If no match is found, **-1** is returned. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getIndexFrom(4, 3);
```

## getIndexOf

```TypeScript
getIndexOf(element: T): number
```

Obtains the index of the first occurrence of the specified element in this Vector.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the element. If no match is found, **-1** is returned. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(2);
vector.add(1);
vector.add(2);
vector.add(4);
let result = vector.getIndexOf(2);
```

## getLastElement

```TypeScript
getLastElement(): T
```

Obtains the last element in this Vector.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T | The last element obtained. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getLastElement();
```

## getLastIndexFrom

```TypeScript
getLastIndexFrom(element: T, index: number): number
```

Searches for an element backward from the specified position index and returns the position index of the element.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |
| index | number | Yes | Position index where the search starts. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the element. If no match is found, **-1** is returned. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getLastIndexFrom(4,3);
```

## getLastIndexOf

```TypeScript
getLastIndexOf(element: T): number
```

Obtains the index of the last occurrence of the specified element in this Vector.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the element. If no match is found, **-1** is returned. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(2);
vector.add(1);
vector.add(2);
vector.add(4);
let result = vector.getLastIndexOf(2);
```

## has

```TypeScript
has(element: T): boolean
```

Checks whether this Vector has the specified element.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the Vector has the specified element; otherwise, **false** is returned. |

**Examples**

```TypeScript
let vector : Vector<string> = new Vector();
let result = vector.has("squirrel");
vector.add("squirrel");
let result1 = vector.has("squirrel");
```

## increaseCapacityTo

```TypeScript
increaseCapacityTo(newCapacity: number): void
```

Increases the capacity of this Vector.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newCapacity | number | Yes | New capacity. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.increaseCapacityTo(2);
vector.increaseCapacityTo(12);
```

## insert

```TypeScript
insert(element: T, index: number): void
```

Inserts an element within the length range and moves its subsequent elements rightwards.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |
| index | number | Yes | Index of the position where the element is to be inserted. |

**Examples**

```TypeScript
let vector : Vector<string | number | Object | Array<number>> = new Vector();
vector.insert("A", 0);
vector.insert(0, 1);
vector.insert(true, 2);
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

Checks whether this Vector is empty (contains no elements).

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the Vector is empty; otherwise, **false** is returned. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.isEmpty();
```

## remove

```TypeScript
remove(element: T): boolean
```

Removes the first occurrence of the specified element from this Vector.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | T | Yes | Target element. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if the element is removed; otherwise, **false** is returned. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.remove(2);
```

## removeByIndex

```TypeScript
removeByIndex(index: number): T
```

Searches for an element based on its index, removes the element after returning it, and moves its subsequent elements leftwards.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the target element. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Element removed. If the Vector is empty, **undefined** is returned. If the index is out of range, an exception is thrown. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(2);
vector.add(4);
let result = vector.removeByIndex(2);
```

## removeByRange

```TypeScript
removeByRange(fromIndex: number, toIndex: number): void
```

Removes from this Vector all of the elements within a range, including the element at the start position but not that at the end position.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fromIndex | number | Yes | Index of the start position. |
| toIndex | number | Yes | Index of the end position. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.removeByRange(2,4);
```

## replaceAllElements

```TypeScript
replaceAllElements(callbackFn: (value: T, index?: number, vector?: Vector<T>) => T, thisArg?: Object): void
```

Replaces all elements in this Vector with new elements, and returns the new ones.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: T, index?: number, vector?: Vector&lt;T&gt;) =&gt; T | Yes | Callback invoked for replacement. |
| thisArg | Object | No | Value of **this** to use when **callbackFn** is invoked. The default value is this instance. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.replaceAllElements((value : number) : number => {
  // Add the user operation logic based on the actual scenario.
  return value;
});
```

## set

```TypeScript
set(index: number, element: T): T
```

Replaces an element at the specified position in this Vector with a given element.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Position index of the target element. |
| element | T | Yes | Element to be used for replacement. |

**Return value:**

| Type | Description |
| --- | --- |
| T | New element. |

## setLength

```TypeScript
setLength(newSize: number): void
```

Sets a new length for this Vector.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newSize | number | Yes | New length to set. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.setLength(8);
vector.setLength(2);
```

## sort

```TypeScript
sort(comparator?: (firstValue: T, secondValue: T) => number): void
```

Sorts elements in this Vector.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| comparator | (firstValue: T, secondValue: T) =&gt; number | No | Callback invoked for sorting. The default value is this instance. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.sort((a: number, b: number) => a - b);
vector.sort((a: number, b: number) => b - a);
vector.sort();
```

## subVector

```TypeScript
subVector(fromIndex: number, toIndex: number): Vector<T>
```

Obtains elements within a range in this Vector, including the element at the start position but not that at the end position, and returns these elements as a new **Vector** instance.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fromIndex | number | Yes | Index of the start position. |
| toIndex | number | Yes | Index of the end position. |

**Return value:**

| Type | Description |
| --- | --- |
| [Vector](arkts-arkts-util-vector-vector-c.md)&lt;T&gt; | New **Vector** instance obtained. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.add(6);
vector.add(8);
let result = vector.subVector(0,4);
let result1 = vector.subVector(2,4);
```

## toString

```TypeScript
toString(): string
```

Uses commas (,) to concatenate elements in this Vector into a string.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | String obtained. |

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.toString();
```

## trimToCurrentLength

```TypeScript
trimToCurrentLength(): void
```

Trims the capacity of this Vector into its current length.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.trimToCurrentLength();
```

## length

```TypeScript
length: number
```

Number of elements in a Vector.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Utils.Lang
