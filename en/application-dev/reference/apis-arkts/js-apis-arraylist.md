# @ohos.util.ArrayList (Linear Container ArrayList)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8c7d93ae96e9cd8aa2eda0aa88bce1694d2b4f4c translatedAt=2026-11-06T09:11:27.854Z pushedAt=2026-11-13T03:42:17.203Z nl=1 -->

ArrayList is a linear data structure implemented based on arrays, which overcomes the limitation that fixed-size arrays cannot be dynamically expanded. ArrayList dynamically adjusts its capacity based on actual needs, increasing the capacity by 50% each time it expands.

Compared with [LinkedList](js-apis-linkedlist.md), ArrayList provides higher random access efficiency. However, because the addition and deletion operations of ArrayList may require moving other elements in the array, LinkedList provides higher efficiency for addition and deletion operations.

**Recommended use cases:** When you need to frequently read or randomly access elements in a collection by index, use ArrayList. When you need to dynamically manage an ordered data collection with a low frequency of addition and deletion operations, use ArrayList as well.

Generics are used in this document. The following generic type parameters are involved:
- T: Type

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - Container classes, implemented in static languages, have restrictions on storage locations and properties, and do not support custom properties or methods.


## Modules to Import

```ts
import { ArrayList } from '@kit.ArkTS';
```

## ArrayList

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| length | number | Yes| No| Number of elements in an ArrayList.|


### constructor

constructor()

The constructor of ArrayList, used to create an empty ArrayList instance. This constructor must be called with the new keyword and cannot be called directly as a regular function; otherwise, an exception will be thrown.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200012 | The ArrayList's constructor cannot be directly invoked. |

**Example**

```ts
let arrayList = new ArrayList<string | number>();
```


### add

add(element: T): boolean

Inserts an element at the end of the ArrayList. When adding elements in batches, call [increaseCapacityTo](#increasecapacityto) first to expand the capacity, avoiding the performance overhead caused by multiple automatic expansions.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes | Element to insert. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Operation result. The value **true** is returned if the element is added; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The add method cannot be bound. |

**Example**

```ts
class Person {
  name: string = '';
  age: string = '';
}
let arrayList = new ArrayList<string | number | boolean | Array<number> | Person>();
// Add a string element
arrayList.add('a');
// Add a number element
arrayList.add(1);
let numberArray = [1, 2, 3];
// Add an array element
arrayList.add(numberArray);
let person: Person = {name: 'Dylan', age: '13'};
// Add a custom object element
let addPersonResult = arrayList.add(person);
// Add a boolean element
let addBooleanResult = arrayList.add(false);
console.info('addPersonResult:', addPersonResult);  // addPersonResult: true
console.info('addBooleanResult:', addBooleanResult);  // addBooleanResult: true
console.info('length:', arrayList.length);  // length: 5
```

### insert

insert(element: T, index: number): void

Inserts the element at the specified position index within the length range. After a successful call, the length of the ArrayList increases by 1, and the element at the index position and the elements after it are shifted backward by one position. If the index is out of range, an exception is thrown.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes| Target element.|
| index | number | Yes | Index to be inserted. Value Range: [0, ArrayList.length]. Must be less than or equal to int32_max, that is, 2147483647. Throws an exception when Out of Range. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of index is out of range. |
| 10200011 | The insert method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number | string | boolean>();
// Insert the string 'A' at position 0.
arrayList.insert('A', 0);
// Insert the number 0 at position 1.
arrayList.insert(0, 1);
// Insert the boolean value true at position 2.
arrayList.insert(true, 2);
console.info('length:', arrayList.length);  // length: 3
```

### has

has(element: T): boolean

Checks whether this ArrayList contains the specified element.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes | Element to check whether it is contained. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the specified element is contained; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The has method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<string>();
arrayList.add('squirrel');
let result: boolean = arrayList.has('squirrel');
console.info('result:', result);  // result: true
```

### getIndexOf

getIndexOf(element: T): number

Returns the index of the first occurrence of the specified element, or -1 if the element is not found. The difference from [getLastIndexOf](#getlastindexof) is that this method returns the position where the element first appears, while getLastIndexOf returns the position where the element last appears.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes | Element whose first occurrence position is to be found. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Returns the position index if obtained; returns **-1** if the specified element is not found.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getIndexOf method cannot be bound. |

**Example**

```ts
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

### getLastIndexOf

getLastIndexOf(element: T): number

Obtains the index of the last occurrence of the specified element in this ArrayList.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes | Element whose last occurrence position is to be found. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Returns the position index if obtained; returns **-1** if the specified element is not found.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getLastIndexOf method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(2);
arrayList.add(1);
arrayList.add(2);
arrayList.add(4);
let result: number = arrayList.getLastIndexOf(2);
console.info('result = ', result); // result = 5
```

### removeByIndex

removeByIndex(index: number): T

Deletes the element at the specified index and returns the deleted element. After the deletion, the length of the ArrayList decreases by 1, and the elements after the deleted element move forward by one position. If the index is out of range, an exception is thrown.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| index | number | Yes | Index value of the specified element. The value range is [0, ArrayList.length-1]. It must be less than or equal to int32_max, that is, 2147483647. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Element removed.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of "index" is out of range. |
| 10200011 | The removeByIndex method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(2);
arrayList.add(4);
let result: number = arrayList.removeByIndex(2);
console.info('result = ', result); // result = 5
```

### remove

remove(element: T): boolean

Deletes the first found specified element. After the deletion succeeds, the length of the ArrayList decreases by 1, and the elements after the deleted element move forward by one position. If the specified element is not found, no deletion operation is performed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| element | T | Yes | Element to delete. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Operation result. The value **true** is returned if the element is removed; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The remove method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: boolean = arrayList.remove(2);
console.info('result = ', result); // result =  true
```

### removeByRange

removeByRange(fromIndex: number, toIndex: number): void

Deletes elements in the specified range. The range includes fromIndex but excludes toIndex, that is, a left-closed, right-open interval [fromIndex, toIndex). After the deletion, the length of the ArrayList decreases by the corresponding number of elements, and the elements after toIndex move forward in sequence.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fromIndex | number | Yes | Start index, which is included in the range. It must be less than or equal to int32_max, that is, 2147483647. |
| toIndex | number | Yes | End index, which is excluded from the range. It must be less than or equal to int32_max, that is, 2147483647. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of fromIndex or toIndex is out of range. |
| 10200011 | The removeByRange method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
// Delete elements from index 2 to 4 (left-closed, right-open interval, i.e., delete the elements at indexes 2 and 3).
arrayList.removeByRange(2, 4);
```

### replaceAllElements

replaceAllElements(callbackFn: (value: T, index?: number, arrlist?: ArrayList&lt;T&gt;) => T, thisArg?: Object): void

Traverses each element in the ArrayList, executes the callback function on each element, and replaces the original element with the value returned by the callback function.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function used to operate on the element and return the replacement value. |
| thisArg | Object | No | Used as the this value when callbackFn is called. Pass this parameter when the callback function needs to reference an external object as the this context. If not passed, the default value is undefined. |

callbackFn parameters

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes| Value of the element that is currently traversed.|
| index | number | No| Position index of the element that is currently traversed. The default value is **0**.|
| arrlist | [ArrayList](#arraylist)&lt;T&gt; | No | The instance object that calls the replaceAllElements method. The default value is the current instance object. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The replaceAllElements method cannot be bound. |

**Example**

```ts
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

### forEach

forEach(callbackFn: (value: T, index?: number, arrlist?: ArrayList&lt;T&gt;) => void, thisArg?: Object): void

Uses a callback to traverse each element in the **ArrayList** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function used to perform an operation on each element. |
| thisArg | Object | No | Value used as **this** when callbackFn is invoked. Pass this parameter when the callback function needs to reference an external object as the **this** context. If not passed, the default value is undefined. |

callbackFn parameters

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | T | Yes| Value of the element that is currently traversed.|
| index | number | No| Position index of the element that is currently traversed. The default value is **0**.|
| arrlist | [ArrayList](#arraylist)&lt;T&gt; | No | The instance object on which the forEach method is currently called. The default value is the current instance object. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
// Traverse each element in the ArrayList and print the element value and index.
arrayList.forEach((value: number, index?: number) => {
  console.info('value:' + value, 'index:' + index);
});
// value:2 index:0
// value:4 index:1
// value:5 index:2
// value:4 index:3
```

### sort

sort(comparator?: ArrayListComparatorFn&lt;T&gt;): void

Sorts the elements in the ArrayList according to the order defined by the specified comparator. After sorting, the number of elements in the ArrayList remains unchanged, and the element positions are rearranged according to the order defined by the comparator.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| comparator | [ArrayListComparatorFn](#arraylistcomparatorfnt23)&lt;T&gt; | No | Comparator function used to define the sort order. The default is ascending order. Pass this parameter when descending order or custom comparison logic is required.<br>Compatibility change since API version 23. In API version 22 and earlier, its type is: `(firstValue: T, secondValue: T) => number`. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The sort method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
// Sort in ascending order.
arrayList.sort((firstValue: number, secondValue: number) => firstValue - secondValue);
// Sort in descending order.
arrayList.sort((firstValue: number, secondValue: number) => secondValue - firstValue);
// Default sorting (ascending order).
arrayList.sort();
```

### subArrayList

subArrayList(fromIndex: number, toIndex: number): ArrayList&lt;T&gt;

Extracts a segment of elements from the ArrayList based on the index and returns this ArrayList instance, that is, a left-closed, right-open interval [fromIndex, toIndex). If fromIndex or toIndex is out of range, an exception is thrown.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fromIndex | number | Yes | Start index, inclusive. The value range is [0, ArrayList.length-1]. It must be less than toIndex and less than or equal to int32_max, that is, 2147483647. An exception is thrown when it is out of range. |
| toIndex | number | Yes | End index, exclusive. The value range is (fromIndex, ArrayList.length]. It must be greater than fromIndex and less than or equal to int32_max, that is, 2147483647. An exception is thrown when it is out of range. |

**Return value**

| Type| Description|
| -------- | -------- |
| ArrayList&lt;T&gt; | Returns an ArrayList sublist instance containing elements in the range [fromIndex, toIndex). |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of fromIndex or toIndex is out of range. |
| 10200011 | The subArrayList method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: ArrayList<number> = arrayList.subArrayList(2, 4);
console.info('result = ', result.length); // result = 2
```

### clear

clear(): void

Clears all elements in the ArrayList and sets length to 0. This method does not release the reserved capacity. To release the capacity, call the [trimToCurrentLength](#trimtocurrentlength) method.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The clear method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.clear();
```

### clone

clone(): ArrayList&lt;T&gt;

Clones this ArrayList and returns a copy. The modification to the copy does not affect the original instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang


**Return value**

| Type| Description|
| -------- | -------- |
| ArrayList&lt;T&gt; | Returns a clone instance with the same content as the original ArrayList. Modifying the clone instance does not affect the original instance. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The clone method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: ArrayList<number> = arrayList.clone();
console.info('result = ', result.length); // result = 4
```

### getCapacity

getCapacity(): number

Obtains the capacity of this ArrayList.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| number | Returns the current capacity of the instance. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The getCapacity method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: number = arrayList.getCapacity();
console.info('result = ', result); // result = 10
```

### convertToArray

convertToArray(): Array&lt;T&gt;

Converts the current ArrayList instance into an array and returns the converted array. This operation does not modify the original ArrayList instance, and modifications to the returned array do not affect the original instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| Array&lt;T&gt; | Returns an array consisting of all elements in the ArrayList. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The convertToArray method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: Array<number> = arrayList.convertToArray();
console.info('result = ', result); // result =  2,4,5,4
```

### isEmpty

isEmpty(): boolean

Checks whether this ArrayList is empty (contains no element).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the ArrayList is empty; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: boolean = arrayList.isEmpty();
console.info('result = ', result); // result =  false
```

### \[index: number\]<sup>12+</sup>

\[index: number\]: T

Obtains the element at the position corresponding to the specified index. If the index is out of range, an exception is thrown.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| index | number | Yes | Index of the element. The value range is [0, ArrayList.length-1]. It must be less than or equal to int32_max, that is, 2147483647. An exception is thrown when the value is out of range. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Element obtained.|

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200001 | The value of index is out of range. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
let result: number = arrayList[2];
console.info('result = ', result); // result =  5
```

### increaseCapacityTo

increaseCapacityTo(newCapacity: number): void

If the new capacity passed in is greater than or equal to the number of elements in the ArrayList, the capacity is changed to the new capacity; if the new capacity passed in is less than the number of elements in the ArrayList, the capacity remains unchanged. When elements need to be added in batches, you can call this method in advance to expand the capacity, avoiding the performance overhead caused by multiple automatic expansions.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| newCapacity | number | Yes | New capacity. It takes effect only when it is greater than or equal to the number of elements in the current ArrayList; otherwise, the capacity does not change. It must be less than or equal to int32_max, that is, 2147483647. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The increaseCapacityTo method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.increaseCapacityTo(2);
arrayList.increaseCapacityTo(8);
console.info('result = ', arrayList.length); // result = 4
```

### trimToCurrentLength

trimToCurrentLength(): void

Releases the reserved space in the ArrayList and adjusts the capacity to the current number of elements. When the capacity of the ArrayList is much larger than the current number of elements (for example, after multiple deletion operations), you can call this method to release the excess space to optimize memory usage.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The trimToCurrentLength method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);
arrayList.trimToCurrentLength();
console.info('result = ', arrayList.length); // result = 4
```

### \[Symbol.iterator\]

\[Symbol.iterator\](): IterableIterator&lt;T&gt;

Returns an iterator that returns elements of type T in the order of the elements in the ArrayList.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;T&gt; | Returns an iterator. Traversing the iterator can obtain each element in the ArrayList in sequence. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**Example**

```ts
let arrayList = new ArrayList<number>();
arrayList.add(2);
arrayList.add(4);
arrayList.add(5);
arrayList.add(4);

// Method 1:
for (let value of arrayList) {
  console.info('value:', value);
}
// value: 2
// value: 4
// value: 5
// value: 4

// Method 2:
let iterator = arrayList[Symbol.iterator]();
let iteratorResult: IteratorResult<number> = iterator.next();
while (!iteratorResult.done) {
  console.info('value:', iteratorResult.value);
  iteratorResult = iterator.next();
}
// value: 2
// value: 4
// value: 5
// value: 4
```

## ArrayListComparatorFn&lt;T&gt;<sup>23+</sup>

type ArrayListComparatorFn&lt;T&gt; = (firstValue: T, secondValue: T) => number

Callback function of the **sort** method in ArrayList.

**Atomic service API**: This API can be used in atomic services since API version 23.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| firstValue | T | Yes| The first element to be sorted.|
| secondValue | T | Yes| The second element to be sorted.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Value returned through the callback function. ArrayList maintains the order of elements based on this comparison rule. A negative number indicates that firstValue is less than secondValue (firstValue is placed before secondValue), 0 indicates that the two are equal, and a positive number indicates that firstValue is greater than secondValue (firstValue is placed after secondValue). |