# Uint8ClampedArray

```TypeScript
class Uint8ClampedArray
```

A linear data structure that is implemented on [ArkTS ArrayBuffer](arkts-arkts-collections-arraybuffer-c.md).

> **NOTE:** 
> 
> - This module can be imported only to ArkTS files (with the file name extension .ets).
> **Decorator**: \@Sendable

**Since:** 12

**Decorator:** @Sendable

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { collections } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<number>
```

Returns an iterator that iterates over numbers.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;number&gt; | Iterator object that yields numbers. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The Symbol.iterator method cannot be bound. |

## at

```TypeScript
at(index: number): number | undefined
```

Returns the element at the given index. If no element is found, **undefined** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | The zero-based index of the desired code unit.<br> A negative index will count back from the last item. |

**Return value:**

| Type | Description |
| --- | --- |
| number &#124; undefined | Element obtained. If no element is found, **undefined** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The at method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## constructor

```TypeScript
constructor()
```

A constructor used to create an empty ArkTS Uint8ClampedArray.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The Uint8ClampedArray's constructor cannot be directly invoked. |

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(length: number)
```

A constructor used to create an ArkTS Uint8ClampedArray of a given length.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes | Length of the ArkTS Uint8ClampedArray. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The Uint8ClampedArray's constructor cannot be directly invoked. |

<a id="constructor-2"></a>

## constructor

```TypeScript
constructor(elements: Iterable<number>)
```

A constructor that creates an ArkTS Uint8ClampedArray from an iterable object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elements | Iterable&lt;number&gt; | Yes | An iterable collection of numbers used to construct an ArkTS Uint8 ClampedArray object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The Uint8ClampedArray's constructor cannot be directly invoked. |

<a id="constructor-3"></a>

## constructor

```TypeScript
constructor(array: ArrayLike<number> | ArrayBuffer)
```

A constructor that creates an ArkTS Uint8ClampedArray from an array-like object or ArkTS ArrayBuffer.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | ArrayLike&lt;number&gt; &#124; ArrayBuffer | Yes | Object used to construct the ArkTS Uint8ClampedArray. When the parameter type is ArrayBuffer, the number of bytes occupied by the buffer must be an integer multiple of 1. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The Uint8ClampedArray's constructor cannot be directly invoked. |

<a id="constructor-4"></a>

## constructor

```TypeScript
constructor(buffer: ArrayBuffer, byteOffset?: number, length?: number)
```

A constructor that creates an ArkTS Uint8ClampedArray from an ArrayBuffer.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | Yes | ArrayBuffer object used to construct the ArkTS Uint8ClampedArray. The number of bytes occupied by the buffer must be an integer multiple of 1. |
| byteOffset | number | No | Byte offset of the buffer, beginning at 0. The default value is **0**. |
| length | number | No | Length of the ArkTS Uint8ClampedArray. The default value is **0**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The Uint8ClampedArray's constructor cannot be directly invoked. |

## copyWithin

```TypeScript
copyWithin(target: number, start: number, end?: number): Uint8ClampedArray
```

Copies elements within a given range from this ArkTS Uint8ClampedArray to another position in sequence.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | number | Yes | Start index of the range. If a negative number is passed in, it refers to the index of `target + array.length`. |
| start | number | Yes | Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint8ClampedArray.length`. |
| end | number | No | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint8ClampedArray.length`. The default value is the length of the ArkTS Uint8ClampedArray. |

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | Uint8ClampedArray after being modified. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The copyWithin method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## entries

```TypeScript
entries(): IterableIterator<[number, number]>
```

Returns an iterator object that contains the key-value pair of each element in this ArkTS Uint8ClampedArray.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[number, number]&gt; | Iterator object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The entries method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## every

```TypeScript
every(predicate: TypedArrayPredicateFn<number, Uint8ClampedArray>): boolean
```

Checks whether all elements in this ArkTS Uint8ClampedArray meet a given condition.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)&lt;number, [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md)&gt; | Yes | Assertion function used for the test. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if all elements meet the given condition; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The every method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## fill

```TypeScript
fill(value: number, start?: number, end?: number): Uint8ClampedArray
```

Fills all elements in a given range in this ArkTS Uint8ClampedArray with a value.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Value to fill in. |
| start | number | No | Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint8ClampedArray.length`. The default value is **0**. |
| end | number | No | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint8ClampedArray.length`. The default value is the length of the ArkTS Uint8ClampedArray. |

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | Filled ArkTS Uint8ClampedArray. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The fill method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## filter

```TypeScript
filter(predicate: TypedArrayPredicateFn<number, Uint8ClampedArray>): Uint8ClampedArray
```

Returns a new ArkTS Uint8ClampedArray that contains all elements that meet the given condition.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)&lt;number, [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md)&gt; | Yes | Assertion function used for the test. |

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | Filtered ArkTS Uint8ClampedArray. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The filter method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## find

```TypeScript
find(predicate: TypedArrayPredicateFn<number, Uint8ClampedArray>): number | undefined
```

Returns the value of the first element that passes a test provided by a callback function. If none of the elements pass the test, **undefined** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)&lt;number, [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md)&gt; | Yes | Assertion function used for the test. |

**Return value:**

| Type | Description |
| --- | --- |
| number &#124; undefined | Value of the first element that passes the test. If none of the elements pass the test, **undefined** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The find method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## findIndex

```TypeScript
findIndex(predicate: TypedArrayPredicateFn<number, Uint8ClampedArray>): number
```

Returns the index of the first element that passes a test provided by a callback function. If none of the elements pass the test, **-1** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)&lt;number, [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md)&gt; | Yes | Assertion function used for the test. |

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
forEach(callbackFn: TypedArrayForEachCallback<number, Uint8ClampedArray>): void
```

Calls a callback function for each element in this ArkTS Uint8ClampedArray.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayForEachCallback](arkts-arkts-collections-typedarrayforeachcallback-t.md)&lt;number, [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md)&gt; | Yes | Callback function to run for each element. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The forEach method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## from

```TypeScript
static from(arrayLike: ArrayLike<number>): Uint8ClampedArray
```

Creates an ArkTS Uint8ClampedArray from an array-like or iterator object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;number&gt; | Yes | Array-like object used to construct the ArkTS Uint8ClampedArray. |

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | New ArkTS Uint8ClampedArray generated. |

<a id="from-1"></a>

## from

```TypeScript
static from<T>(arrayLike: ArrayLike<T>, mapFn: TypedArrayFromMapFn<T, number>): Uint8ClampedArray
```

Creates an ArkTS Uint8ClampedArray from an array-like object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | ArrayLike&lt;T&gt; | Yes | Array-like object used to construct the ArkTS Uint8ClampedArray. |
| mapFn | [TypedArrayFromMapFn](arkts-arkts-collections-typedarrayfrommapfn-t.md)&lt;T, number&gt; | Yes | A mapping function to call on every element of the array. |

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | New ArkTS Uint8ClampedArray generated. |

<a id="from-2"></a>

## from

```TypeScript
static from(arrayLike: Iterable<number>, mapFn?: TypedArrayFromMapFn<number, number>): Uint8ClampedArray
```

Creates an ArkTS Uint8ClampedArray from an iterator object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| arrayLike | Iterable&lt;number&gt; | Yes | Iterator object used to construct the ArkTS Uint8ClampedArray. |
| mapFn | [TypedArrayFromMapFn](arkts-arkts-collections-typedarrayfrommapfn-t.md)&lt;number, number&gt; | No | Mapping function. If no value is passed in, no special processing is conducted on the elements. |

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | New ArkTS Uint8ClampedArray generated. |

## includes

```TypeScript
includes(searchElement: number, fromIndex?: number): boolean
```

Checks whether elements are contained in this ArkTS Uint8ClampedArray.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | number | Yes | The element to search for. |
| fromIndex | number | No | The position in this array at which to begin searching for searchElement. |

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
indexOf(searchElement: number, fromIndex?: number): number
```

Returns the index of the first occurrence of a value in this ArkTS Uint8ClampedArray. If the value is not found, **-1** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | number | Yes | Value to search for. |
| fromIndex | number | No | Index from which the search starts. The default value is **0**. If the index is greater than or equal to the length of the ArkTS Uint8ClampedArray, **-1** is returned. If a negative number is passed in, the search starts from the end of the ArkTS Uint8ClampedArray. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the first occurrence of the value. If the value is not found, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The indexOf method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## join

```TypeScript
join(separator?: string): string
```

Concatenates all elements in this ArkTS Uint8ClampedArray into a string, with a given separator.

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

Returns an iterator object that contains the key (index) of each element in this ArkTS Uint8ClampedArray.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;number&gt; | Iterator object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The keys method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## lastIndexOf

```TypeScript
lastIndexOf(searchElement: number, fromIndex?: number): number
```

Obtains the index of the last occurrence of the specified value in this ArkTS Uint8ClampedArray.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchElement | number | Yes | Value to search for. |
| fromIndex | number | No | Index from which the search starts. The default value is the ArkTS Uint8ClampedArray length minus 1 (i.e., starting from the end). If the index is greater than or equal to the length of the ArkTS Uint8ClampedArray, **-1** is returned. If a negative number is passed in, the search starts from the end of the ArkTS Uint8ClampedArray. |

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
map(callbackFn: TypedArrayMapCallback<number, Uint8ClampedArray>): Uint8ClampedArray
```

Applies a callback function to each element in this ArkTS Uint8ClampedArray and uses the result to create an ArkTS Uint8ClampedArray.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayMapCallback](arkts-arkts-collections-typedarraymapcallback-t.md)&lt;number, [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md)&gt; | Yes | A function that accepts up to three arguments. The map method calls the callbackfn function one time for each element in the array. |

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | New ArkTS Uint8ClampedArray. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The map method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## of

```TypeScript
static of(...items: number[]): Uint8ClampedArray
```

Creates an ArkTS Uint8ClampedArray with a variable number of parameters.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | number[] | Yes | Array of elements used to create the array. The number of elements can be zero, one, or more. |

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | New ArkTS Uint8ClampedArray instance. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## reduce

```TypeScript
reduce(callbackFn: TypedArrayReduceCallback<number, number, Uint8ClampedArray>): number
```

Applies a reduce function on each element in this ArkTS Uint8ClampedArray and returns the final reduction result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)&lt;number, number, [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md)&gt; | Yes | A function that accepts up to four arguments. The reduce method calls the callbackfn function one time for each element in the array. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Final result obtained from the last call of the reduce function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

<a id="reduce-1"></a>

## reduce

```TypeScript
reduce<U = number>(callbackFn: TypedArrayReduceCallback<U, number, Uint8ClampedArray>, initialValue: U): U
```

Applies a reduce function for each element in this ArkTS Uint8ClampedArray, receives an initial value as the parameter called by the reduce function for the first time, and returns the final reduction result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)&lt;U, number, [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md)&gt; | Yes | A function that accepts up to four arguments. The reduce method calls the callbackfn function one time for each element in the array. |
| initialValue | U | Yes | If initialValue is specified, it is used as the initial value to start the accumulation. The first call to the callbackfn function provides this value as an argument instead of an array value. |

**Return value:**

| Type | Description |
| --- | --- |
| U | Final result obtained from the last call of the reduce function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The reduce method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## reduceRight

```TypeScript
reduceRight<U = number>(callbackFn: TypedArrayReduceCallback<U, number, Uint8ClampedArray>, initialValue: U): U
```

Reversely traverses this ArkTS Uint8ClampedArray, applies a reduce function for each element in the array, receives an initial value as the parameter called by the reduce function for the first time, and returns the final reduction result.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)&lt;U, number, [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md)&gt; | Yes | A function that is called for each element in the Uint8ClampedArray. |
| initialValue | U | Yes | A value to use as the first argument to the first call of the callback.<br>If no initial value is provided, the last element of the Uint8ClampedArray will be used, <br>and the callback will start with the second-to-last element. |

**Return value:**

| Type | Description |
| --- | --- |
| U | Final result obtained from the last call of the reduce function. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The reduceRight method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

<a id="reduceright-1"></a>

## reduceRight

```TypeScript
reduceRight(callbackFn: TypedArrayReduceCallback<number, number, Uint8ClampedArray>): number
```

Reversely traverses this ArkTS Uint8ClampedArray, applies a reduce function on each element in the array, and returns the final reduction result.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md)&lt;number, number, [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md)&gt; | Yes | A function that is called for each element in the Uint8ClampedArray. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Final result obtained from the last call of the reduce function. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The reduceRight method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## reverse

```TypeScript
reverse(): Uint8ClampedArray
```

Reverses this ArkTS Uint8ClampedArray.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | Reversed ArkTS Uint8ClampedArray. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The reverse method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## set

```TypeScript
set(array: ArrayLike<number>, offset?: number): void
```

Writes the elements in an array-like object to the given start position in sequence.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | ArrayLike&lt;number&gt; | Yes | A typed or untyped array of values to set. |
| offset | number | No | The index in the current array at which the values are to be written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The set method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## slice

```TypeScript
slice(start?: number, end?: number): Uint8ClampedArray
```

Selects a range of elements in this ArkTS Uint8ClampedArray to create an ArkTS Uint8ClampedArray.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | No | Start index of the range. If a negative number is passed in, it refers to the index of `start + Uint8ClampedArray.length`. The default value is **0**. |
| end | number | No | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint8ClampedArray.length`. The default value is the length of the ArkTS Uint8ClampedArray. |

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | New ArkTS Uint8ClampedArray. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The slice method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## some

```TypeScript
some(predicate: TypedArrayPredicateFn<number, Uint8ClampedArray>): boolean
```

Checks whether any element in this ArkTS Uint8ClampedArray meets a given condition.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicate | [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md)&lt;number, [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md)&gt; | Yes | Assertion function used for the test. |

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
sort(compareFn?: TypedArrayCompareFn<number>): Uint8ClampedArray
```

Sorts elements in this ArkTS Uint8ClampedArray and returns the sorted ArkTS Uint8ClampedArray.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| compareFn | [TypedArrayCompareFn](arkts-arkts-collections-typedarraycomparefn-t.md)&lt;number&gt; | No | Function that determines the sort order. By default, elements are sorted in ascending order. |

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | Sorted ArkTS Uint8ClampedArray. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The sort method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## subarray

```TypeScript
subarray(begin?: number, end?: number): Uint8ClampedArray
```

Truncates an array from a specified position and returns a new ArkTS Uint8ClampedArray based on the same ArkTS ArrayBuffer.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| begin | number | No | Start index of the range. If a negative number is passed in, it refers to the index of `begin + Uint8ClampedArray.length`. The default value is **0**. |
| end | number | No | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + Uint8ClampedArray.length`. The default value is the length of the ArkTS Uint8ClampedArray. |

**Return value:**

| Type | Description |
| --- | --- |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | New ArkTS Uint8ClampedArray. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The subarray method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## toLocaleString

```TypeScript
toLocaleString(): string
```

Generates digits that match the cultural conventions of the current system locale. Each element converts its digits to a string via its **toLocaleString** API, and these strings are then joined in sequence with commas (,).

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

Converts an ArkTS Uint8ClampedArray into a string.

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

## values

```TypeScript
values(): IterableIterator<number>
```

Returns an iterator object that contains the value of each element in this ArkTS Uint8ClampedArray.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;number&gt; | Iterator object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The values method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## [index: number]

```TypeScript
[index: number]: number
```

Returns the item at that index.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## buffer

```TypeScript
readonly buffer: ArrayBuffer
```

Bottom-layer buffer used by an ArkTS Uint8ClampedArray.

**Type:** ArrayBuffer

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## byteLength

```TypeScript
readonly byteLength: number
```

Number of bytes occupied by an ArkTS Uint8ClampedArray.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## byteOffset

```TypeScript
readonly byteOffset: number
```

Offset between the ArkTS Uint8ClampedArray and the start position of the ArrayBuffer.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## BYTES_PER_ELEMENT

```TypeScript
static readonly BYTES_PER_ELEMENT: number
```

Number of bytes occupied by each element in the ArkTS Uint8ClampedArray.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## length

```TypeScript
readonly length: number
```

Number of elements in an ArkTS Uint8ClampedArray.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
