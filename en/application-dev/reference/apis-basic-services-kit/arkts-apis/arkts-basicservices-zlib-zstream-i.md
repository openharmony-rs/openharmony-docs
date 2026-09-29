# ZStream

```TypeScript
interface ZStream
```

Process all the information required for compression and decompression.

**Since:** 12

<!--Device-zlib-interface ZStream--><!--Device-zlib-interface ZStream-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## adler

```TypeScript
adler?: number
```

Adler-32 or CRC-32 value of uncompressed data.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ZStream-adler?: long--><!--Device-ZStream-adler?: long-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## availableIn

```TypeScript
availableIn?: number
```

Number of bytes available for **nextIn**.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ZStream-availableIn?: int--><!--Device-ZStream-availableIn?: int-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## availableOut

```TypeScript
availableOut?: number
```

Number of remaining bytes available for **nextOut**.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ZStream-availableOut?: int--><!--Device-ZStream-availableOut?: int-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## dataType

```TypeScript
dataType?: number
```

Binary or text of **deflate**, or decoding state of **inflate**.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ZStream-dataType?: int--><!--Device-ZStream-dataType?: int-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## nextIn

```TypeScript
nextIn?: ArrayBuffer
```

Input bytes to be compressed.

**Type:** ArrayBuffer

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ZStream-nextIn?: ArrayBuffer--><!--Device-ZStream-nextIn?: ArrayBuffer-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## nextOut

```TypeScript
nextOut?: ArrayBuffer
```

Output bytes after compression.

**Type:** ArrayBuffer

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ZStream-nextOut?: ArrayBuffer--><!--Device-ZStream-nextOut?: ArrayBuffer-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## totalIn

```TypeScript
totalIn?: number
```

Total number of input bytes read so far.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ZStream-totalIn?: long--><!--Device-ZStream-totalIn?: long-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## totalOut

```TypeScript
totalOut?: number
```

Total number of output bytes.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ZStream-totalOut?: long--><!--Device-ZStream-totalOut?: long-End-->

**System capability:** SystemCapability.BundleManager.Zlib
