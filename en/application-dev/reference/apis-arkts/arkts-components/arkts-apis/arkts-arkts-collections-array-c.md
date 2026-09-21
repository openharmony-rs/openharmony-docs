# Array

```TypeScript
class Array<T> implements ConcatArray<T>
```

A linear data structure that is implemented on arrays and can be passed between ArkTS concurrent instances. Pass-by-reference is recommended for better transfer performance.

> **NOTE:** 
> 
> - This module can be imported only to ArkTS files (with the file name extension .ets).This section uses the following to identify the use of generics:

- T: type, which can be any of the [sendable data types](../../../arkts-utils/arkts-sendable.md#sendable-data-types). **Decorator**: \@Sendable

**Inheritance/Implementation:** Array implements ConcatArray<T>

**Since:** 12

**Decorator:** @Sendable

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { collections } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

Obtains an iterator, each item of which is a JavaScript object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;T&gt; | Iterator object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The Symbol.iterator method cannot be bound. |

## at

```TypeScript
at(index: number): T | undefined
```

Returns the element at a given index in this ArkTS array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the element. The index in an array always starts from 0 and is an integer. If a negative number is passed in, it refers to the index of **index + array.length**. |

**Return value:**

| Type | Description |
| --- | --- |
| T &#124; undefined | Element at the given index. If the index is out of range or invalid, **undefined** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The at method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## concat

```TypeScript
concat(...items: ConcatArray<T>[]): Array<T>
```

Concatenates this ArkTS array with one or more arrays.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | ConcatArray&lt;T&gt;[] | Yes | Concatenates this ArkTS array with one or more arrays. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | New array generated. Not a valid array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The concat method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## constructor

```TypeScript
constructor()
```

A constructor used to create an empty ArkTS array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The Array's constructor cannot be directly invoked. |

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(first: T, ...left: T[])
```

A constructor used to create an ArkTS array with the given elements.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| first | T | Yes | First element to be included in the ArkTS array. |
| left | T[] | Yes | Remaining elements to be included in the ArkTS array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The Array's constructor cannot be directly invoked. |

<a id="constructor-2"></a>

## constructor

```TypeScript
constructor(...items: T[])
```

A constructor used to create an ArkTS array with the given elements.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | T[] | Yes | Elements to be included in the ArkTS array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The Array's constructor cannot be directly invoked. |

## containsAll

```TypeScript
containsAll(elements: Array<T>): boolean
```

Checks whether all elements in a specified ArkTS Array are contained in this ArkTS Array.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elements | Array&lt;T&gt; | Yes | ArkTS Array whose elements are to be checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if all elements are contained in this ArkTS array; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The containsAll method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification exception |

<a id="containsall-1"></a>

## containsAll

```TypeScript
containsAll(elements: readonly T[]): boolean
```

Checks whether all elements in a specified JavaScript built-in Array are contained in this ArkTS Array.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elements | readonly T[] | Yes | JavaScript built-in Array whose elements are to be checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if all elements are contained in this ArkTS array; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The containsAll method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification exception |

## copyWithin

```TypeScript
copyWithin(target: number, start: number, end?: number): Array<T>
```

Copies elements within a given range from this ArkTS array to another position in sequence.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | number | Yes | Start index of the range. If a negative number is passed in, it refers to the index of `target + array.length`. |
| start | number | Yes | Start index of the range. If a negative number is passed in, it refers to the index of **start + array.length**. |
| end | number | No | End index of the range. If a negative number is passed in, it refers to the index of `end + array.length`. The default value is the length of the ArkTS array. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | ArkTS array after being modified. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The copyWithin method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## create

```TypeScript
static create<T>(arrayLength: number, initialValue: T): Array<T>
```

Creates an ArkTS array of a fixed length, with each element set to a given initial value.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLength | number | Yes | Length of the ArkTS array. |
| initialValue | T | Yes | Initial value of each element in the ArkTS array. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Newly created ArkTS array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The create method cannot be bound.<br>**Applicable version:** 12 - 17 |

## entries

```TypeScript
entries(): IterableIterator<[number, T]>
```

Returns an iterator object that contains the key-value pair of each element in this ArkTS array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[number, T]&gt; | Iterator object that contains the key-value pair of each element in the array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The entries method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## every

```TypeScript
every(predicate: ArrayPredicateFn<T, Array<T>>): boolean
```

Checks whether all elements in this ArkTS array meet a given condition.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | [ArrayPredicateFn](arkts-arkts-collections-arraypredicatefn-t.md)&lt;T, Array&lt;T&gt;&gt; | Yes | Assertion function used for the test. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if all elements meet the given condition; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The every method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## extendTo

```TypeScript
extendTo(arrayLength: number, initialValue: T): void
```

Extends this array to a given length by adding elements with the specified initial value.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLength | number | Yes | New length of the array. If a value less than or equal to the current array length is passed in, the array does not change. |
| initialValue | T | Yes | Initial value of the elements to be added. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The extendTo method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## fill

```TypeScript
fill(value: T, start?: number, end?: number): Array<T>
```

Fills elements in the specified range of this ArkTS array with a given value.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | T | Yes | Value to fill in. |
| start | number | No | Start index of the range. The default value is **0**. |
| end | number | No | End index of the range (exclusive). If no value is passed in, it refers to the last element of the array. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Filled array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The fill method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## filter

```TypeScript
filter(predicate: (value: T, index: number, array: Array<T>) => boolean): Array<T>
```

Returns a new array containing all elements that pass a test provided by a callback function.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: T, index: number, array: Array&lt;T&gt;) =&gt; boolean | Yes | Function that takes three arguments. It is used to filter elements. The value **true** means that the current element passes the test and should be retained in the new array. The value **false** means that the current element fails the test and should be excluded from the new array. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | New array containing elements that pass the test. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The filter method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## find

```TypeScript
find(predicate: (value: T, index: number, obj: Array<T>) => boolean): T | undefined
```

Returns the value of the first element that passes a test provided by a callback function. If none of the elements pass the test, **undefined** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: T, index: number, obj: Array&lt;T&gt;) =&gt; boolean | Yes | Function that takes three arguments. It is used to filter elements. The value **true** means that the current element meets the conditions, the traversal stops, and that element is returned. The value **false** means that the current element does not meet the condition, and the traversal continues until the element that meets the condition is found or the entire array is traversed. |

**Return value:**

| Type | Description |
| --- | --- |
| T &#124; undefined | Value of the first element that passes the test. If none of the elements pass the test, **undefined** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The find method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## findIndex

```TypeScript
findIndex(predicate: (value: T, index: number, obj: Array<T>) => boolean): number
```

Returns the index of the first element that passes a test provided by a callback function. If none of the elements pass the test, **-1** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | (value: T, index: number, obj: Array&lt;T&gt;) =&gt; boolean | Yes | Function that takes three arguments. It is used to filter elements. The value **true** means that the current element meets the conditions, the traversal stops, and the index of that element is returned. The value **false** means that the current element does not meet the condition, and the traversal continues until the element that meets the condition is found or the entire array is traversed. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the first element that passes the test. If none of the elements pass the test, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The findIndex method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## forEach

```TypeScript
forEach(callbackFn: (value: T, index: number, array: Array<T>) => void): void
```

Calls a callback function for each element in this ArkTS Array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: T, index: number, array: Array&lt;T&gt;) =&gt; void | Yes | Callback function to run for each element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The forEach method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## from

```TypeScript
static from<T>(arrayLike: ArrayLike<T>): Array<T>
```

Creates an ArkTS array from an array-like object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; | Yes | Array-like object. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Newly created ArkTS array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The from method cannot be bound.<br>**Applicable version:** 12 - 17 |

<a id="from-1"></a>

## from

```TypeScript
static from<T>(iterable: Iterable<T>): Array<T>
```

Creates an ArkTS array from an iterable object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| iterable | Iterable&lt;T&gt; | Yes | Array-like object. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Newly created ArkTS array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The from method cannot be bound.<br>**Applicable version:** 12 - 17 |

<a id="from-2"></a>

## from

```TypeScript
static from<T>(arrayLike: ArrayLike<T> | Iterable<T>, mapFn: ArrayFromMapFn<T, T>): Array<T>
```

Creates an ArkTS array from an array-like object, and uses a custom function to process each array element.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; &#124; Iterable&lt;T&gt; | Yes | Array-like object. |
| mapFn | [ArrayFromMapFn](arkts-arkts-collections-arrayfrommapfn-t.md)&lt;T, T&gt; | Yes | Functions used to process the array elements. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Newly created ArkTS array. |

<a id="from-3"></a>

## from

```TypeScript
static from<U, T>(arrayLike: ArrayLike<U> | Iterable<U>, mapFn: ArrayFromMapFn<U, T>): Array<T>
```

Creates an ArkTS array from an array-like object, and uses a custom function to process each array element. The type of the elements in the array-like object can be different from that of the array elements.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;U&gt; &#124; Iterable&lt;U&gt; | Yes | Array-like object. |
| mapFn | [ArrayFromMapFn](arkts-arkts-collections-arrayfrommapfn-t.md)&lt;U, T&gt; | Yes | Functions used to process the array elements. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Newly created ArkTS array. |

## includes

```TypeScript
includes(searchElement: T, fromIndex?: number): boolean
```

Checks whether this ArkTS array contains an element and returns a Boolean value.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | T | Yes | Element to search for. |
| fromIndex | number | No | Index from which the search starts. The default value is **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the element exists; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The includes method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## indexOf

```TypeScript
indexOf(searchElement: T, fromIndex?: number): number
```

Returns the index of the first occurrence of a value in this ArkTS Array. If the value is not found, **-1** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | T | Yes | Value to search for. |
| fromIndex | number | No | Index from which the search starts. The value begins at 0. The default value is **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the first occurrence of the value. If the value is not found, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The indexOf method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## isArray

```TypeScript
static isArray(value: Object | undefined | null): boolean
```

Check whether the input parameter is an ArkTS array.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object &#124; undefined &#124; null | Yes | Value to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the input parameter is an ArkTS array; otherwise, **false** is returned. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

## join

```TypeScript
join(separator?: string): string
```

Concatenates all elements in this ArkTS array into a string, with a given separator.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| separator | string | No | Separator to be used. If no value is passed in, a comma (,) is used as the separator. |

**Return value:**

| Type | Description |
| --- | --- |
| string | String obtained. If the array is empty, an empty string is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The join method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## keys

```TypeScript
keys(): IterableIterator<number>
```

Returns an iterator object that contains the index of each element in this ArkTS array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;number&gt; | Iterator object that contains the index of each element in the array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The keys method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## lastIndexOf

```TypeScript
lastIndexOf(searchElement: T, fromIndex?: number): number
```

Obtains the index of the last occurrence of the specified value in this ArkTS array.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | T | Yes | Value to search for. |
| fromIndex | number | No | Index from which the search starts. The default value is the ArkTS Int8Array length minus 1 (i.e., starting from the end). If the index is greater than or equal to the length of the ArkTS array, **-1** is returned. If a negative number is passed in, it refers to the index of **fromIndex + array.length**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the last occurrence of the value. If the value is not found, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The lastIndexOf method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## map

```TypeScript
map<U>(callbackFn: (value: T, index: number, array: Array<T>) => U): Array<U>
```

Calls a callback function for each element in this ArkTS Array and returns a new array that contains the result of the callback function.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: T, index: number, array: Array&lt;T&gt;) =&gt; U | Yes | Callback function to run for each element. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;U&gt; | New array containing the result of the callback function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The map method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## of

```TypeScript
static of<T>(...items: T[]): Array<T>
```

Creates an ArkTS array with a variable number of parameters.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | T[] | Yes | Array of elements used to create the array. The number of elements can be zero, one, or more. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Newly created ArkTS array. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

## pop

```TypeScript
pop(): T | undefined
```

Removes the last element from this ArkTS array and returns that element. If the array is empty, **undefined** is returned and the array does not change.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T &#124; undefined | Element removed. If the array is empty, **undefined** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The pop method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## push

```TypeScript
push(...items: T[]): number
```

Adds elements to the end of this ArkTS array and returns the new length of the array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | T[] | Yes | Elements to add. |

**Return value:**

| Type | Description |
| --- | --- |
| number | New length of the array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The push method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## reduce

```TypeScript
reduce(callbackFn: (previousValue: T, currentValue: T, currentIndex: number, array: Array<T>) => T): T
```

Calls a callback function for each element in this ArkTS array, uses the previous return value of the function as an accumulated value, and returns the final result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (previousValue: T, currentValue: T, currentIndex: number, array: Array&lt;T&gt;) =&gt; T | Yes | Function that takes four arguments. It performs an operation on each element and passes the result as an accumulated value to the next element. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Final result obtained from the last call of the callback function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

<a id="reduce-1"></a>

## reduce

```TypeScript
reduce<U>(
      callbackFn: (previousValue: U, currentValue: T, currentIndex: number, array: Array<T>) => U,
      initialValue: U
    ): U
```

Similar to the previous API, this API takes an initial value as the second parameter to initialize the accumulator before the array traversal starts.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (previousValue: U, currentValue: T, currentIndex: number, array: Array&lt;T&gt;) =&gt; U | Yes | Function that takes four arguments. It performs an operation on each element and passes the result as an accumulated value to the next element. |
| initialValue | U | Yes | Initial value of the accumulator. |

**Return value:**

| Type | Description |
| --- | --- |
| U | Final result obtained from the last call of the callback function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## reduceRight

```TypeScript
reduceRight<U = T>(callbackFn: ArrayReduceCallback<U, T, Array<T>>, initialValue: U): U
```

This API is similar to the [reduceRight](#reduceright-1) API, but it takes an initial value as the second parameter to initialize the accumulator before the array traversal starts from right to left.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | [ArrayReduceCallback](arkts-arkts-collections-arrayreducecallback-t.md)&lt;U, T, Array&lt;T&gt;&gt; | Yes | Function that takes four arguments. It performs an operation on each element and passes the result as an accumulated value to the next element. |
| initialValue | U | Yes | Initial value of the accumulator. |

**Return value:**

| Type | Description |
| --- | --- |
| U | Final result obtained from the last call of the callback function. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The reduceRight method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

<a id="reduceright-1"></a>

## reduceRight

```TypeScript
reduceRight(callbackFn: ArrayReduceCallback<T, T, Array<T>>): T
```

Goes through each element in this ArkTS array from right to left, uses a callback function to combine them into a single value, and returns that final value.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | [ArrayReduceCallback](arkts-arkts-collections-arrayreducecallback-t.md)&lt;T, T, Array&lt;T&gt;&gt; | Yes | Function that takes four arguments. It performs an operation on each element and passes the result as an accumulated value to the next element. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Final result obtained from the last call of the callback function. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The reduceRight method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## retainAll

```TypeScript
retainAll(elements: Array<T>): boolean
```

Retains only the elements in this ArkTS Array that are contained in the specified ArkTS Array.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elements | Array&lt;T&gt; | Yes | ArkTS Array whose elements are to be retained. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if any elements are removed from this ArkTS array; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The retainAll method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification exception |

<a id="retainall-1"></a>

## retainAll

```TypeScript
retainAll(elements: readonly T[]): boolean
```

Retains only the elements in this ArkTS Array that are contained in the specified JavaScript built-in Array.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elements | readonly T[] | Yes | JavaScript built-in Array whose elements are to be retained. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if any elements are removed from this ArkTS array; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The retainAll method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification exception |

<a id="retainall-2"></a>

## retainAll

```TypeScript
retainAll(predicate: ArrayElementPredicateFn<T>): boolean
```

Retains only the elements in this ArkTS Array that satisfy the specified predicate.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | [ArrayElementPredicateFn](arkts-arkts-collections-arrayelementpredicatefn-t.md)&lt;T&gt; | Yes | Predicate function used to test each element. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if any elements are removed from this ArkTS array; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The retainAll method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification exception |

## reverse

```TypeScript
reverse(): Array<T>
```

Reverses elements in this ArkTS array and returns a reference to the same array.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Reversed ArkTS array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The reverse method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## shift

```TypeScript
shift(): T | undefined
```

Removes the first element from this ArkTS array and returns that element. If the array is empty, **undefined** is returned and the array does not change.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| T &#124; undefined | Element removed. If the array is empty, **undefined** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The shift method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## shrinkTo

```TypeScript
shrinkTo(arrayLength: number): void
```

Shrinks this ArkTS array to a given length.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLength | number | Yes | New length of the array. If a value greater than or equal to the current array length is passed in, the array does not change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The shrinkTo method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## slice

```TypeScript
slice(start?: number, end?: number): Array<T>
```

Selects a range of elements in this ArkTS array to create an array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | No | Start index of the range. If a negative number is passed in, it refers to the index of start + array.length. The default value is 0. |
| end | number | No | End index of the range (exclusive). If a negative number is passed in, it refers to the index of end + array.length. The default value is the length of the ArkTS array. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | New array containing the selected elements. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The slice method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## some

```TypeScript
some(predicate: ArrayPredicateFn<T, Array<T>>): boolean
```

Checks whether this ArkTS array contains an element that meets certain conditions.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | [ArrayPredicateFn](arkts-arkts-collections-arraypredicatefn-t.md)&lt;T, Array&lt;T&gt;&gt; | Yes | Assertion function used for the test. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if an element meeting the given condition exists; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The some method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## sort

```TypeScript
sort(compareFn?: (a: T, b: T) => number): Array<T>
```

Sorts elements in this ArkTS array and returns a new array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| compareFn | (a: T, b: T) =&gt; number | No | Function that determines the sort order. By default, elements are sorted in ascending order. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Array with the sorted elements. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The sort method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## splice

```TypeScript
splice(start: number): Array<T>
```

Removes elements from a specified position (start) and all elements after the specified position in an array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Index from which the removal starts. If -array.length =&lt; start &lt; 0, the removal starts from start + array.length. If start &lt; -array.length, the removal starts from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | **Array** object that contains the removed elements. If no element is removed, an empty **Array** object is returned.Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The splice method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

<a id="splice-1"></a>

## splice

```TypeScript
splice(start: number, deleteCount: number, ...items: T[]): Array<T>
```

Removes elements from a specified position in an array, and inserts new elements from the same position.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Index from which the removal starts. If -array.length =&lt; start &lt; 0, the removal starts from start + array.length. If start &lt; -array.length, the removal starts from 0. |
| deleteCount | number | Yes | Number of elements to remove. |
| items | T[] | Yes | New elements to insert from the start position. If no value is passed in, only the elements in the array are removed. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | **Array** object that contains the removed elements. If no element is removed, an empty **Array** object is returned. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The splice method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## toLocaleString

```TypeScript
toLocaleString(): string
```

Generates a string that matches the cultural conversions of the current system locale. Each element converts itself to a string via its **toLocaleString** API, and these strings are then joined in sequence with commas (,).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | A string that contains all elements of the array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The toLocaleString method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## toString

```TypeScript
toString(): string
```

Converts an ArkTS array into a string.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | A string that contains all elements of the array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The toString method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## unshift

```TypeScript
unshift(...items: T[]): number
```

Adds elements to the beginning of this ArkTS array and returns the new length of the array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | T[] | Yes | Elements to add. |

**Return value:**

| Type | Description |
| --- | --- |
| number | New length of the array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The unshift method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## values

```TypeScript
values(): IterableIterator<T>
```

Returns an iterator object that contains the value of each element in this ArkTS array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;T&gt; | Iterator object that contains the value of each element in the array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The values method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## [index: number]

```TypeScript
[index: number]: T
```

Returns the element at a given index in this array.

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
readonly length: number
```

Number of elements in an ArkTS array.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
