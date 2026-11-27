# @ohos.util.Vector (Linear Container Vector)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @Malzahar-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=a211d88dec3940df73a753a1732c7250fbff3179 translatedAt=2026-11-16T06:02:33.121Z pushedAt=2026-11-16T06:31:14.296Z nl=1 -->

Vector is a linear data structure implemented based on arrays, which solves the data storage problem that requires dynamic capacity expansion and efficient random access. When the memory of Vector is exhausted, a larger contiguous memory area is automatically allocated, the original elements are copied to the new memory area, and the old memory area is released. Using Vector enables efficient and fast access to elements. Its 2x capacity expansion policy reduces frequent memory reallocation, and its rich operation interfaces provide more flexible data management capabilities.

Both Vector and [ArrayList](js-apis-arraylist.md) are implemented based on arrays, but Vector provides more interfaces for operating the arrays. Both of them can dynamically adjust the capacity. Vector doubles the capacity each time, whereas ArrayList increases the capacity by 50%.

**Recommended use cases:** When frequent random access to elements by index is required and the data volume is large, Vector is recommended for storing and accessing data.

Generics are used in this document, involving the following generic type parameter:<br>
- T: Type

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with the superscript to indicate their earliest API version.
>
> Since API version 9, this API is no longer maintained. It is recommended that you use [ArrayList](js-apis-arraylist.md).

## Modules to Import

```ts
import { Vector } from '@kit.ArkTS';
```


## Vector

### Properties

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Number of elements in a Vector.|


### constructor

constructor()

A constructor used to create a **Vector** instance.

**System capability**: SystemCapability.Utils.Lang

**Example**

```ts
let vector : Vector<string | number | Array<number>> = new Vector();
```


### add

add(element: T): boolean

Inserts an element at the end of Vector. After the insertion succeeds, the length of Vector increases by 1.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes | Added element. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Operation result. The value **true** is returned if the element is added; otherwise, **false** is returned.|

**Example**

```ts
// Define the custom class PersonInfo.
class PersonInfo {
  name: string = ""
  age: string = ""
}
// Create a Vector instance.
let vector : Vector<string | number | PersonInfo | Array<number>> = new Vector();
// Add a string element.
let result = vector.add("a");
// Add a number element.
let result1 = vector.add(1);
let numArray = [1, 2, 3];
// Add an array element.
let result2 = vector.add(numArray);
let personInfo: PersonInfo = {name : "Jack", age : "13"};
// Add a custom class instance.
let result3 = vector.add(personInfo);
```

### insert

insert(element: T, index: number): void

Inserts an element at a specified position within the length range, and moves the elements after this position to the right.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes| Target element.|
| index | number | Yes | Position index of the element to be inserted. Value range: [0, length]. |

**Example**

```ts
// Create a Vector instance.
let vector : Vector<string | number | Object | Array<number>> = new Vector();
// Insert the string "A" at index 0.
vector.insert("A", 0);
// Insert the number 0 at index 1.
vector.insert(0, 1);
// Insert the boolean value true at index 2.
vector.insert(true, 2);
```

### has

has(element: T): boolean

Checks whether this Vector has the specified element.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes| Target element.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the Vector has the specified element; otherwise, **false** is returned.|

**Example**

```ts
// Create a Vector instance.
let vector : Vector<string> = new Vector();
// Determine whether it contains "squirrel" before adding an element. Expected return: false.
let result = vector.has("squirrel");
// Add element "squirrel".
vector.add("squirrel");
// Determine whether it contains "squirrel" after adding an element. Expected return: true.
let result1 = vector.has("squirrel");
```

### getIndexOf

getIndexOf(element: T): number

Returns the index of the first occurrence of the specified element. If the search fails, -1 is returned. Difference from [getLastIndexOf](#getlastindexof): getIndexOf returns the position of the first occurrence of the element, while getLastIndexOf returns the position of the last occurrence of the element.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes| Target element.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Index of the element. If no match is found, **-1** is returned.|

**Example**

```ts
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

### getLastIndexOf

getLastIndexOf(element: T): number

Obtains the index of the last occurrence of the specified element in this Vector.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes| Target element.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Index of the element. If no match is found, **-1** is returned.|

**Example**

```ts
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

### removeByIndex

removeByIndex(index: number): T

Finds the corresponding element by index and deletes it, moves the elements after this position to the left, and returns the deleted element. The value range of index is [0, length-1].

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| index | number | Yes | Position index of the element to be removed. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Return the removed element. Return undefined when Vector is empty, and throw an exception when the index is out of bounds. |

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(2);
vector.add(4);
let result = vector.removeByIndex(2);
```

### remove

remove(element: T): boolean

Deletes the first found specified element and moves the elements after it to the left.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes| Target element.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns true if the deletion is successful, and false if the deletion fails. |

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.remove(2);
```

### removeByRange

removeByRange(fromIndex: number, toIndex: number): void

Deletes elements from a range, including the start value but excluding the end value. After deletion, subsequent elements shift left, and the length of the Vector decreases accordingly.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fromIndex | number | Yes | Start index, including the element corresponding to this index. |
| toIndex | number | Yes | End index, excluding the element corresponding to this index. |

**Example**

```ts
// Create a Vector instance and add element.
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// Delete elements between index 2 and 4 (include the start index 2, not include the end index 4).
vector.removeByRange(2,4);
```

### replaceAllElements

replaceAllElements(callbackFn: (value: T, index?: number, vector?: Vector&lt;T&gt;) => T, thisArg?: Object): void

Operates on the elements in the Vector through a callback function, replacing the original elements with the elements returned by the callback function.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function used to operate on the elements in Vector and replace the original elements with the operation results. |
| thisArg | Object | No | Value used as this when callbackFn is called. Default value is the current instance object. |

callbackFn parameters

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes| Value of the element that is currently traversed.|
| index | number | No | Index value of the current iteration. |
| vector | [Vector&lt;T&gt;](#vector) | No | Instance object that currently calls the replaceAllElements method. Default value is the current instance object. |

**Example**

```ts
// Create a Vector instance and add element
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// Perform a replace operation on each element in the Vector, and the callback function returns the replaced element
vector.replaceAllElements((value : number) : number => {
  // Add the user operation logic based on the actual scenario.
  return value;
});
```

### forEach

forEach(callbackFn: (value: T, index?: number, vector?: Vector&lt;T&gt;) => void, thisArg?: Object): void

Uses a callback to traverse the elements in this Vector and obtain their position indexes.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function used to iterate over each element in Vector. |
| thisArg | Object | No | Value used as this when callbackFn is called. Default value is the current instance object. |

callbackFn parameters

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes| Value of the element that is currently traversed.|
| index | number | No | Index value of the current iteration. |
| vector | [Vector&lt;T&gt;](#vector) | No | Instance object that currently calls the forEach method. Default value is the current instance object. |

**Example**

```ts
// Create a Vector instance and add elements.
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// Traverse each element in the Vector, and print the element value and index.
vector.forEach((value : number, index?: number) : void => {
  console.info("value:" + value, "index:" + index);
});
```

### sort

sort(comparator?: (firstValue: T, secondValue: T) => number): void

Sorts the elements in the Vector. After sorting, the index positions of the elements change. Index values obtained before sorting through methods such as getIndexOf and getLastIndexOf are no longer valid and must be queried again.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| comparator | function | No | Callback function. If this parameter is not passed, elements are sorted by the default sorting rule. |

comparator

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| firstValue | T | Yes| Previous element.|
| secondValue | T | Yes| Next element.|

**Example**

```ts
// Create a Vector instance and add elements.
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// Sort in ascending order.
vector.sort((a: number, b: number) => a - b);
// Sort in descending order.
vector.sort((a: number, b: number) => b - a);
// Use the default sorting rule.
vector.sort();
```

### subVector

subVector(fromIndex: number, toIndex: number): Vector&lt;T&gt;

Intercepts a range of elements in the Vector by index and returns this Vector instance, including the start value but excluding the end value.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fromIndex | number | Yes | Start index. Value range: 0 ≤ fromIndex < length. |
| toIndex | number | Yes | End index. Value range: 0 ≤ toIndex ≤ length, and toIndex must be greater than fromIndex. |

**Return value**

| Type| Description|
| -------- | -------- |
| Vector&lt;T&gt; | Returns a Vector object instance containing elements from the start index to the end index (excluding the end index). |

**Example**

```ts
// Create a Vector instance and add element
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.add(6);
vector.add(8);
// Extract elements between index 0 and 4 (include the start index 0, not include the end index 4, and toIndex is greater than fromIndex)
let result = vector.subVector(0,4);
// Extract elements between index 2 and 4 (include the start index 2, not include the end index 4)
let result1 = vector.subVector(2,4);

```

### clear

clear(): void

Clears all elements in this Vector and sets its length to **0**.

**System capability**: SystemCapability.Utils.Lang

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.clear();
```

### clone

clone(): Vector&lt;T&gt;

Clones this Vector and returns a copy. The modification to the copy does not affect the original instance.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| Vector&lt;T&gt; | Returns a cloned Vector object instance with the same content as the original instance. Modifying the cloned instance does not affect the original instance. |

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.clone();
```

### getCapacity

getCapacity(): number

Obtains the capacity of this Vector.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| number | Capacity obtained.|

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getCapacity();
```

### convertToArray

convertToArray(): Array&lt;T&gt;

Converts this Vector into an array.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| Array&lt;T&gt; | Returns an array containing all elements in the Vector. |

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.convertToArray();
```

### isEmpty

isEmpty(): boolean

Checks whether this Vector is empty (contains no elements).

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Return true when empty, and false when not empty. |

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.isEmpty();
```

### increaseCapacityTo

increaseCapacityTo(newCapacity: number): void

If the new capacity passed in is greater than or equal to the number of elements in the current Vector instance, the capacity is changed to the new capacity. If the new capacity passed in is less than the number of elements in the current Vector instance, no change is made.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| newCapacity | number | Yes | New capacity, which must be greater than or equal to the number of elements in the current Vector. The value does not take effect if it is less than the number of elements. |

**Example**

```ts
// Create a Vector instance and add element
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// Pass in capacity 2, which is less than the number of elements 4. The capacity is not changed.
vector.increaseCapacityTo(2);
// Pass in capacity 12, which is greater than the number of elements 4. The capacity changes to 12.
vector.increaseCapacityTo(12);
```

### trimToCurrentLength

trimToCurrentLength(): void

Limits the capacity to the current length. This is suitable for releasing excess memory space after element addition is complete, optimizing memory usage.

**System capability**: SystemCapability.Utils.Lang

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.trimToCurrentLength();
```

### toString

toString(): string

Uses commas (,) to concatenate elements in this Vector into a string.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| string | Returns a string formed by concatenating the elements in the Vector in order with ",". |

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.toString();
```

### copyToArray

copyToArray(array: Array&lt;T&gt;): void

Copies the elements in the Vector instance to the corresponding positions in the specified array according to their index correspondence.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| array | Array&lt;T&gt; | Yes | Target array that receives the copied elements. |

### getFirstElement

getFirstElement(): T

Obtains the first element in the instance. Returns undefined when the Vector is empty.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Returns the first element in the Vector instance; returns undefined if the Vector is empty. |

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getFirstElement();
```

### getLastElement

getLastElement(): T

Obtains the last element in the Vector instance. Returns undefined when the Vector is empty.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| T | Returns the last element in the Vector instance; if the Vector is empty, returns undefined. |

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getLastElement();
```

### getLastIndexFrom

getLastIndexFrom(element: T, index: number): number

Searches from the specified index toward lower indices and returns the index of the element.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes| Target element.|
| index | number | Yes | Search starts from the specified index. Value range: [0, length-1]. Returns -1 when out of range. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Index of the element. If no match is found, **-1** is returned.|

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getLastIndexFrom(4,3);
```

### getIndexFrom

getIndexFrom(element: T, index: number): number

Searches from the specified index toward higher indices and returns the index of the element.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes| Target element.|
| index | number | Yes | Starting position for forward search from the specified index. Value range: [0, length-1]. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Index of the element. If no match is found, **-1** is returned.|

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.getIndexFrom(4, 3);
```

### setLength

setLength(newSize: number): void

Sets the number of elements in the Vector instance. If newSize is greater than the current number of elements, capacity expansion is performed. If newSize is less than the current number of elements, the excess elements are truncated and removed. When newSize is 0, all elements are cleared and length is set to 0.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| newSize | number | Yes | New length to set. Value rule: newSize ≥ 0. |

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
vector.setLength(8);
vector.setLength(2);
```

### get

get(index: number): T 

Obtains the element in the Vector instance by index. The value range of index is [0, length-1]. Returns undefined when the Vector is empty or the index is out of bounds.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | index | number | Yes | Index value to search for. Value range: 0 ≤ index < length. |

**Return value**

  | Type| Description|
  | -------- | -------- |
  | T | Element obtained.|

**Example**

```ts
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
let result = vector.get(2);
```

### set

set(index: number, element: T): T

Replaces an element at the specified position in this Vector with a given element.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| index | number | Yes | Index value to search for. Value range: [0, length-1]. |
| element | T | Yes| Element to be used for replacement.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | T | Returns the original element at the replaced position. |

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;

Returns an iterator used for iteration over the elements in the Vector.

**System capability**: SystemCapability.Utils.Lang

**Return value**
| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Returns an iterator used for iteration over the elements in the Vector instance. |

**Example**

```ts
// Create a Vector instance and add elements.
let vector : Vector<number> = new Vector();
vector.add(2);
vector.add(4);
vector.add(5);
vector.add(4);
// Usage 1: Convert the Vector to an array via convertToArray, then traverse it using for-of.
let nums: Array<number> =  vector.convertToArray()
for (let item of nums) {
  console.info("value:" + item);
}

// Usage 2: Obtain the iterator via Symbol.iterator, then access elements one by one using next().
let iter = vector[Symbol.iterator]();
let temp: IteratorResult<number> = iter.next().value;
while(temp != undefined) {
  console.info("value:" + temp);
  temp = iter.next().value;
}
```