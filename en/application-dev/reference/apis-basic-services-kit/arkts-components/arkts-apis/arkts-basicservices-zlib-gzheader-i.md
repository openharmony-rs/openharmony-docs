# GzHeader

```TypeScript
interface GzHeader
```

Gzip header information passed to and from zlib routines.

**Since:** 12

<!--Device-zlib-interface GzHeader--><!--Device-zlib-interface GzHeader-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## comment

```TypeScript
comment?: ArrayBuffer
```

Comment.

**Type:** ArrayBuffer

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzHeader-comment?: ArrayBuffer--><!--Device-GzHeader-comment?: ArrayBuffer-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## done

```TypeScript
done?: boolean
```

Returns **True** after reading the gzip file header.

**Type:** boolean

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzHeader-done?: boolean--><!--Device-GzHeader-done?: boolean-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## extra

```TypeScript
extra?: ArrayBuffer
```

Extra field.

**Type:** ArrayBuffer

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzHeader-extra?: ArrayBuffer--><!--Device-GzHeader-extra?: ArrayBuffer-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## extraLen

```TypeScript
extraLen?: number
```

Length of the extra field.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzHeader-extraLen?: int--><!--Device-GzHeader-extraLen?: int-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## hcrc

```TypeScript
hcrc?: boolean
```

Returns **True** if the **crc** header exists.

**Type:** boolean

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzHeader-hcrc?: boolean--><!--Device-GzHeader-hcrc?: boolean-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## isText

```TypeScript
isText?: boolean
```

Returns **True** if the compressed data is considered text.

**Type:** boolean

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzHeader-isText?: boolean--><!--Device-GzHeader-isText?: boolean-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## name

```TypeScript
name?: ArrayBuffer
```

File name.

**Type:** ArrayBuffer

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzHeader-name?: ArrayBuffer--><!--Device-GzHeader-name?: ArrayBuffer-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## os

```TypeScript
os?: number
```

Operating system.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzHeader-os?: int--><!--Device-GzHeader-os?: int-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## time

```TypeScript
time?: number
```

Modification time.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzHeader-time?: long--><!--Device-GzHeader-time?: long-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## xflags

```TypeScript
xflags?: number
```

Extra flag.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzHeader-xflags?: int--><!--Device-GzHeader-xflags?: int-End-->

**System capability:** SystemCapability.BundleManager.Zlib
