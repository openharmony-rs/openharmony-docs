# ConcatArray

An array-like object that can be concatenated. This API extends **ISendable**.

> **NOTE:** 
> 
> - This module can be imported only to ArkTS files (with the file name extension .ets).This section uses the following to identify the use of generics:

- T: type, which can be any of the [sendable data types](../../../arkts-utils/arkts-sendable.md#sendable-data-types).

**Inheritance/Implementation:** ConcatArray extends [ISendable](arkts-arkts-collections-isendable-t.md)

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { collections } from '@kit.ArkTS';
```

## join

```TypeScript
join(separator?: string): string
```

Concatenates all elements in this array into a string, with a given separator.

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

## slice

```TypeScript
slice(start?: number, end?: number): ConcatArray<T>
```

Selects a range of elements in this array to create an array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | No | Start index of the range. If a negative number is passed in, it refers to the index of 'start + array.length' The default value is '0'. |
| end | number | No | End index of the range (exclusive). If a negative number is passed in, it refers to the index of 'end + array.length'. The default value is the length of the ArkTS array. |

**Return value:**

| Type | Description |
| --- | --- |
| ConcatArray&lt;T&gt; | New array containing the selected elements. |

## [index: number]

```TypeScript
readonly [index: number]: T
```

Returns the element at a given index in this ConcatArray.

**Type:** T

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-value-out-of-range) | The value of index is out of range. |

## length

```TypeScript
readonly length: number
```

Number of elements in a ConcatArray.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
