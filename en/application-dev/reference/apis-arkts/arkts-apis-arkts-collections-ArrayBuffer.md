# Class (ArrayBuffer)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=ee30fc06a4d48737c123d3032041ea2f72a0d534 translatedAt=2026-11-06T08:19:47.376Z pushedAt=2026-11-12T13:57:11.517Z nl=2 -->

Underlying data structure of the ArkTS TypedArray ([Int8Array](arkts-apis-arkts-collections-Int8Array.md), [Uint8Array](arkts-apis-arkts-collections-Uint8Array.md), [Int16Array](arkts-apis-arkts-collections-Int16Array.md), [Uint16Array](arkts-apis-arkts-collections-Uint16Array.md), [Int32Array](arkts-apis-arkts-collections-Int32Array.md), [Uint32Array](arkts-apis-arkts-collections-Uint32Array.md), [Uint8ClampedArray](arkts-apis-arkts-collections-Uint8ClampedArray.md), and [Float32Array](arkts-apis-arkts-collections-Float32Array.md)).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module can be imported only to ArkTS files (with the file name extension .ets).

**Decorator**: \@Sendable

## Modules to Import

```ts
import { collections } from '@kit.ArkTS';
```

## Properties

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 12.

| Name  | Type  | Read Only| Optional| Description             |
| ------ | ------ | ---- | ---- | ----------------|
| byteLength | number | Yes  | No  | Number of bytes occupied by the buffer.|

## constructor
constructor(byteLength: number)

A constructor used to create an ArkTS ArrayBuffer of a given length.

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------|
| byteLength  | number | Yes   | The number of bytes occupied by the buffer. The value ranges from 0 to 2147483647. Otherwise, an exception is thrown. 0 indicates that the length of the constructed ArkTS ArrayBuffer is 0, and 2147483647 indicates that the length of the constructed ArkTS ArrayBuffer is 2147483647. |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 10200012 | The ArrayBuffer's constructor cannot be directly invoked. |

**Example**

```ts
let arrayBuffer: collections.ArrayBuffer = new collections.ArrayBuffer(10);
console.info("byteLength: " + arrayBuffer.byteLength); // byteLength: 10
```

## slice
slice(begin: number, end?: number): ArrayBuffer

Selects a range of elements in this ArkTS ArrayBuffer to create an ArkTS ArrayBuffer.

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name| Type  | Mandatory| Description                                             |
| ------ | ------ | ---- | ------------------------------------------------ |
| begin  | number | Yes   | Start index. If `begin < 0`, the start position is `begin + arrayBuffer.byteLength`. If `begin < -arrayBuffer.byteLength`, the start position is 0. |
| end    | number | No   | End index (excluding the element at this index). If `end < 0`, the end position is `end + arrayBuffer.byteLength`. If `end > arrayBuffer.byteLength`, the slice ends at arrayBuffer.byteLength. The default value is the length of the original ArkTS ArrayBuffer. |

**Return value**

| Type        | Description     |
| ------------ | --------- |
| ArrayBuffer | collections.ArrayBuffer, a new ArkTS ArrayBuffer object containing the content of the specified range of the original ArkTS ArrayBuffer |

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID|                    Error Message                  |
| -------- | -------------------------------------------- |
| 10200011 | The slice method cannot be bound.            |
| 10200201 | Concurrent modification error.               |

**Example**

```ts
let arrayBuffer: collections.ArrayBuffer = new collections.ArrayBuffer(10);
let slicedBuffer: collections.ArrayBuffer = arrayBuffer.slice(0, 4);
console.info("byteLength: " + slicedBuffer.byteLength); // byteLength: 4
```
