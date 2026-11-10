# Module Description
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=71db7138e2704708b0a19c70a4e677ab1c2014cd translatedAt=2026-11-06T08:57:47.927Z pushedAt=2026-11-09T09:20:14.619Z nl=2 -->

The ArkTS container set provided by this module can be used for high-performance data transfer in concurrent scenarios. Its functions are similar to those of the corresponding built-in JavaScript containers, but an ArkTS container instance cannot add or update properties through `"."` or `"[]"`.

When an ArkTS container is passed between multiple concurrent instances, the default behavior is reference passing, which allows multiple concurrent instances to operate on the same container instance at the same time. In addition, copy passing is also supported, that is, each concurrent instance holds an ArkTS container instance.

ArkTS containers are not thread-safe. They internally use a fail-fast mechanism: when it is detected that multiple concurrent instances make structural changes to a container at the same time, an exception is triggered. Therefore, when reading from and writing to a container in multiple threads, the container user must use the asynchronous lock mechanism provided by ArkTS to ensure safe access to the ArkTS container.

Currently, the following ArkTS containers are provided: [Array](arkts-apis-arkts-collections-Array.md), [Map](arkts-apis-arkts-collections-Map.md), [Set](arkts-apis-arkts-collections-Set.md), TypedArray ([Int8Array](arkts-apis-arkts-collections-Int8Array.md), [Uint8Array](arkts-apis-arkts-collections-Uint8Array.md), [Int16Array](arkts-apis-arkts-collections-Int16Array.md), [Uint16Array](arkts-apis-arkts-collections-Uint16Array.md), [Int32Array](arkts-apis-arkts-collections-Int32Array.md), [Uint32Array](arkts-apis-arkts-collections-Uint32Array.md), [Uint8ClampedArray](arkts-apis-arkts-collections-Uint8ClampedArray.md) and [Float32Array](arkts-apis-arkts-collections-Float32Array.md)), [ArrayBuffer](arkts-apis-arkts-collections-ArrayBuffer.md), [BitVector](arkts-apis-arkts-collections-BitVector.md), and [ConcatArray](arkts-apis-arkts-collections-ConcatArray.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module can be imported only to ArkTS files (with the file name extension .ets).

## Modules to Import

```ts
import { collections } from '@kit.ArkTS';
```