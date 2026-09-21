# BitVector

```TypeScript
class BitVector
```

A linear data structure that is implemented on arrays. A bit vector stores bit values and provides bit-level storage and processing.

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

Returns an iterator that iterates over bit vector.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;number&gt; | A new iterable iterator object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The Symbol.iterator method cannot be bound. |

## constructor

```TypeScript
constructor(length: number)
```

Constructor used to create a bit vector.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | number | Yes | Length of the bit vector. |

## flipBitByIndex

```TypeScript
flipBitByIndex(index: number): void
```

Flips the bit value (from 0 to 1 or from 1 to 0) at a given index in this bit vector.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index. If **index** is less than **0** or greater than or equal to **length**, an error is reported. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The flipBitByIndex method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## flipBitsByRange

```TypeScript
flipBitsByRange(fromIndex: number, toIndex: number): void
```

Flips the bit values (from 0 to 1 or from 1 to 0) in a given range in this bit vector.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fromIndex | number | Yes | Start index of the range (inclusive). If **fromIndex** is less than **0** or greater than or equal to **toIndex**, an error is thrown. |
| toIndex | number | Yes | End index of the range (exclusive). If **toIndex** is less than **0** or greater than or equal to **length**, an error is thrown. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of fromIndex or toIndex is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The flipBitsByRange method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## getBitCountByRange

```TypeScript
getBitCountByRange(element: number, fromIndex: number, toIndex: number): number
```

Counts the number of bit values in a given range of this bit vector.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | number | Yes | Bit value. The value **0** indicates bit value 0, and other values indicate bit value 1. |
| fromIndex | number | Yes | Start index of the range (inclusive). If **fromIndex** is less than **0** or greater than or equal to **toIndex**, an error is thrown. |
| toIndex | number | Yes | End index of the range (exclusive). If **toIndex** is less than **0** or greater than or equal to **length**, an error is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of bit values. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of fromIndex or toIndex is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getBitCountByRange method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## getBitsByRange

```TypeScript
getBitsByRange(fromIndex: number, toIndex: number): BitVector
```

Obtains bit values within a given range of this bit vector.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fromIndex | number | Yes | Start index of the range (inclusive). If **fromIndex** is less than **0** or greater than or equal to **toIndex**, an error is thrown. |
| toIndex | number | Yes | End index of the range (exclusive). If **toIndex** is less than **0** or greater than or equal to **length**, an error is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| [BitVector](arkts-arkts-collections-bitvector-c.md) | Bit vector containing the bit values obtained. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of fromIndex or toIndex is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getBitsByRange method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## getIndexOf

```TypeScript
getIndexOf(element: number, fromIndex: number, toIndex: number): number
```

Returns the index of the first occurrence of a bit value in this bit vector. If the bit value is not found, **-1** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | number | Yes | Bit value. The value **0** indicates bit value 0, and other values indicate bit value 1. |
| fromIndex | number | Yes | Start index of the range (inclusive). If **fromIndex** is less than **0** or greater than or equal to **toIndex**, an error is thrown. |
| toIndex | number | Yes | End index of the range (exclusive). If **toIndex** is less than **0** or greater than or equal to **length**, an error is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the first occurrence of the bit value. If the bit value is not found, **-1** is returned. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of fromIndex or toIndex is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getIndexOf method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## getLastIndexOf

```TypeScript
getLastIndexOf(element: number, fromIndex: number, toIndex: number): number
```

Returns the index of the last occurrence of a bit value in this bit vector. If the bit value is not found, **-1** is returned.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | number | Yes | Bit value. The value **0** indicates bit value 0, and other values indicate bit value 1. |
| fromIndex | number | Yes | Start index of the range (inclusive). If **fromIndex** is less than **0** or greater than or equal to **toIndex**, an error is thrown. |
| toIndex | number | Yes | End index of the range (exclusive). If **toIndex** is less than **0** or greater than or equal to **length**, an error is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the last occurrence of the bit value. If the bit value is not found, **-1** is returned. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of fromIndex or toIndex is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The getLastIndexOf method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## has

```TypeScript
has(element: number, fromIndex: number, toIndex: number): boolean
```

Checks whether a bit value is included in a given range of this bit vector.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | number | Yes | Bit value. The value **0** indicates bit value 0, and other values indicate bit value 1. |
| fromIndex | number | Yes | Start index of the range (inclusive). If **fromIndex** is less than **0** or greater than or equal to **toIndex**, an error is thrown. |
| toIndex | number | Yes | End index of the range (inclusive). If **toIndex** is less than **0** or greater than or equal to **length**, an error is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the bit value exists; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of fromIndex or toIndex is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The has method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## pop

```TypeScript
pop(): number
```

Removes the last element from this bit vector.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Element (bit value) removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The pop method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## push

```TypeScript
push(element: number): boolean
```

Adds an element at the end of this bit vector.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | number | Yes | Element to add. The value **0** indicates bit value 0, and other values indicate bit value 1. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. The value **true** is returned if the element is added; otherwise, **false** is returned. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The push method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## resize

```TypeScript
resize(size: number): void
```

Resizes this bit vector. If **size** is greater than the length of the existing bit vector, the bit vector is extended, and elements of the extra part are set to 0. If **size** is less than or equal to the length of the existing bit vector, the bit vector is shrunk according to the size.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | New length. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The resize method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## setAllBits

```TypeScript
setAllBits(element: number): void
```

Sets all elements in this bit vector to a bit value.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | number | Yes | Bit value to set. The value **0** indicates bit value 0, and other values indicate bit value 1. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The setAllBits method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## setBitsByRange

```TypeScript
setBitsByRange(element: number, fromIndex: number, toIndex: number): void
```

Sets elements in a given range in this bit vector to a bit value.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| element | number | Yes | Bit value to set. The value **0** indicates bit value 0, and other values indicate bit value 1. |
| fromIndex | number | Yes | Start index of the range (inclusive). If **fromIndex** is less than **0** or greater than or equal to **toIndex**, an error is thrown. |
| toIndex | number | Yes | End index of the range (exclusive). If **toIndex** is less than **0** or greater than or equal to **length**, an error is thrown. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of fromIndex or toIndex is out of range. |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The setBitsByRange method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## values

```TypeScript
values(): IterableIterator<number>
```

Returns an iterator object that contains the value of each element in this bit vector.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;number&gt; | Bit vector iterator object. |

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

## length

```TypeScript
readonly length: number
```

Number of elements in a bit vector.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
