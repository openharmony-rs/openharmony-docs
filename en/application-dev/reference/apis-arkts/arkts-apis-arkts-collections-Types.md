# Types
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-11-06T08:42:19.440Z pushedAt=2026-11-13T01:57:23.047Z nl=2 -->

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module can be imported only to ArkTS files (with the file name extension .ets).

## ISendable

type ISendable = lang.ISendable

**ISendable** is the parent type of all sendable types except `null` and `undefined`. It does not define any methods or properties that must be implemented.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Type| Description  |
| ------ | ------ |
| [lang.ISendable](js-apis-arkts-lang.md#isendable)   | The parent type of all Sendable types. |

## ArrayFromMapFn<sup>18+</sup>
type ArrayFromMapFn<FromElementType, ToElementType> = (value: FromElementType, index: number) => ToElementType

ArkTS Array mapping function type, used by the [from](arkts-apis-arkts-collections-Array.md#from18) interface of the Array class.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| value | FromElementType | Yes | Current ArkTS Array element being traversed, used for mapping conversion into a new array element. |
| index | number | Yes | Element index of the current ArkTS Array element being traversed, starting from 0. |

**Return value**

| Type  | Description                         |
| ------ | --------------------------- |
| ToElementType | Result of the mapping function, which is used as the new element of the array. |

## ArrayPredicateFn<sup>18+</sup>
type ArrayPredicateFn<ElementType, ArrayType> = (value: ElementType, index: number, array: ArrayType) => boolean

ArkTS Array assertion function type, used by the [some](arkts-apis-arkts-collections-Array.md#some18) and [every](arkts-apis-arkts-collections-Array.md#every18) interfaces of the Array class to determine whether array elements satisfy the test condition.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| value | ElementType | Yes | Current ArkTS Array element being traversed, used to determine whether the test condition is met. |
| index | number | Yes | Index of the current ArkTS Array element being traversed, starting from 0. |
| array | ArrayType | Yes| ArkTS array that is being traversed.|

**Return value**

| Type  | Description                         |
| ------ | --------------------------- |
| boolean | Result of the assertion function, which determines whether the current element passes the test condition. When true, it indicates that the current or a previous element has met the condition; when false, it indicates that no element meeting the condition has been found yet. |

## ArrayReduceCallback<sup>18+</sup>
type ArrayReduceCallback<AccType, ElementType, ArrayType> = (previousValue: AccType, currentValue: ElementType, currentIndex: number, array: ArrayType) => AccType

ArkTS Array reduction function type, used by the [reduceRight](arkts-apis-arkts-collections-Array.md#reduceright18) interface of the Array class.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| previousValue | AccType | Yes| Accumulated value of the current traversal.|
| currentValue | ElementType | Yes | Current ArkTS Array element being traversed, which will be used for reduction calculation with previousValue. |
| currentIndex | number | Yes | Index of the current ArkTS Array element being traversed, starting from 0. |
| array | ArrayType | Yes| ArkTS array that is being traversed.|

**Return value**

| Type  | Description                         |
| ------ | --------------------------- |
| AccType | Result of the reduction function, which is used as the **previousValue** parameter in the next call of **ArrayReduceCallback**.|

## ArrayElementPredicateFn

type ArrayElementPredicateFn\<ElementType> = (value: ElementType) => boolean

ArkTS Array assertion function type, used by the [retainAll](arkts-apis-arkts-collections-Array.md#retainall-2) interface of the Array class to determine whether an array element satisfies the test condition.

**Since:** 26.0.1

**Model restriction:** This type can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type   | Mandatory | Description                          |
| ------- | ------ | ---- | --------------------------- |
| value | ElementType | Yes | Current ArkTS Array element being traversed, used to determine whether it satisfies the test condition.|

**Return value**

| Type   | Description                          |
| ------ | --------------------------- |
| boolean | Result of the assertion function. **true** indicates that the current element satisfies the condition, and **false** indicates that the current element does not satisfy the condition. |

## TypedArrayFromMapFn
type TypedArrayFromMapFn\<FromElementType, ToElementType> = (value: FromElementType, index: number) => ToElementType

ArkTS TypedArray mapping function type, used by the from() interface of the TypedArray class.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| value | FromElementType | Yes| Element that is currently traversed and used to construct an ArkTS TypedArray.|
| index | number | Yes | Element index of the current traversal used to construct the ArkTS TypedArray, starting from 0. |

**Return value**

| Type  | Description                         |
| ------ | --------------------------- |
| ToElementType | Element value after the mapping.|

## TypedArrayPredicateFn
type TypedArrayPredicateFn\<ElementType, ArrayType> = (value: ElementType, index: number, array: ArrayType) => boolean

ArkTS TypedArray assertion function type, used by the some(), every(), filter(), find(), and findIndex() interfaces of the TypedArray class.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| value | ElementType | Yes | Current ArkTS TypedArray element being traversed, used to determine whether the test condition is met. |
| index | number | Yes | Index of the current ArkTS TypedArray element being traversed, starting from 0. |
| array | ArrayType | Yes| ArkTS TypedArray that is being traversed.|

**Return value**

| Type  | Description                         |
| ------ | --------------------------- |
| boolean | Result of the assertion function, which determines whether the current element passes the test condition. When true, the current element satisfies the test condition; when false, the current element does not satisfy the test condition. |

## TypedArrayForEachCallback
type TypedArrayForEachCallback\<ElementType, ArrayType> = (value: ElementType, index: number, array: ArrayType) => void

ArkTS TypedArray traversal function type, used by the forEach() interface of the TypedArray class.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| value | ElementType | Yes | Current ArkTS TypedArray element being traversed. |
| index | number | Yes | Index of the current ArkTS TypedArray element being traversed, starting from 0. |
| array | ArrayType | Yes | Current ArkTS TypedArray instance being traversed. |

## TypedArrayMapCallback
type TypedArrayMapCallback\<ElementType, ArrayType> = (value: ElementType, index: number, array: ArrayType) => ElementType

ArkTS TypedArray mapping function type, used by the map() interface of the TypedArray class.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| value | ElementType | Yes| Element that is being mapped in the ArkTS TypedArray.|
| index | number | Yes | Index of the current mapped ArkTS TypedArray element, starting from 0. |
| array | ArrayType | Yes| ArkTS TypedArray that is being mapped.|

**Return value**

| Type  | Description                         |
| ------ | --------------------------- |
| ElementType | Element value after the mapping.|

## TypedArrayReduceCallback
type TypedArrayReduceCallback\<AccType, ElementType, ArrayType> = (previousValue: AccType, currentValue: ElementType, currentIndex: number, array: ArrayType) => AccType

ArkTS TypedArray reduction function type, used by the reduce() and reduceRight() interfaces of the TypedArray class.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| previousValue | AccType | Yes| Accumulated value of the current traversal.|
| currentValue | ElementType | Yes | Current ArkTS TypedArray element being traversed, which will be used for reduction calculation with previousValue. |
| currentIndex | number | Yes | Index of the current ArkTS TypedArray element being traversed, starting from 0. |
| array | ArrayType | Yes| ArkTS TypedArray that is being traversed.|

**Return value**

| Type  | Description                         |
| ------ | --------------------------- |
| AccType | Result of the reduce function. The result is passed in to the **previousValue** parameter when **TypedArrayReduceCallback** is called next time.|

## TypedArrayCompareFn
type TypedArrayCompareFn\<ElementType> = (first: ElementType, second: ElementType) => number

ArkTS TypedArray sorting function type, used by the sort() interface of the TypedArray class.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| first | ElementType | Yes| First element to be compared.|
| second | ElementType | Yes| Second element to be compared.|

**Return value**

| Type  | Description                         |
| ------ | --------------------------- |
| number | Comparison result of the elements. If `first` is less than `second`, the return value is a negative number. If `first` is greater than `second`, the return value is a positive number. If `first` is equal to `second`, the return value is 0.|
