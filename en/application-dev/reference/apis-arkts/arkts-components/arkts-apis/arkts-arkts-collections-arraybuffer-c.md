# ArrayBuffer

```TypeScript
class ArrayBuffer
```

Underlying data structure of the ArkTS TypedArray ([Int8Array](arkts-arkts-collections-int8array-c.md), [Uint8Array](arkts-arkts-collections-uint8array-c.md), [Int16Array](arkts-arkts-collections-int16array-c.md), [Uint16Array](arkts-arkts-collections-uint16array-c.md), [Int32Array](arkts-arkts-collections-int32array-c.md), [Uint32Array](arkts-arkts-collections-uint32array-c.md), [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md), and [Float32Array](arkts-arkts-collections-float32array-c.md)).

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

## constructor

```TypeScript
constructor(byteLength: number)
```

A constructor used to create an ArkTS ArrayBuffer of a given length.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byteLength | number | Yes | Number of bytes occupied by the buffer. The maximum value is **2147483647**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200012](../errorcode-utils.md#10200012-constructor-calling-failure) | The ArrayBuffer's constructor cannot be directly invoked. |

## slice

```TypeScript
slice(begin: number, end?: number): ArrayBuffer
```

Selects a range of elements in this ArkTS ArrayBuffer to create an ArkTS ArrayBuffer.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| begin | number | Yes | Start index of the range. If a negative number is passed in, it refers to the index of `begin + arrayBuffer.byteLength`. |
| end | number | No | End index of the range (exclusive). If a negative number is passed in, it refers to the index of `end + arrayBuffer.byteLength`. The default value is the length of the original ArkTS ArrayBuffer. |

**Return value:**

| Type | Description |
| --- | --- |
| ArrayBuffer | New ArrayBuffer generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200011](../errorcode-utils.md#10200011-passed-thisobject-is-not-an-instance-of-the-containers-class) | The slice method cannot be bound. |
| [10200201](../errorcode-utils.md#10200201-concurrent-modification-error) | Concurrent modification error. |

## byteLength

```TypeScript
readonly byteLength: number
```

Number of bytes occupied by the buffer.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
