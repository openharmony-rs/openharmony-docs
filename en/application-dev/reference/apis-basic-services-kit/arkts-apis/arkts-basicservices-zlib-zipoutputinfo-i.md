# ZipOutputInfo

```TypeScript
interface ZipOutputInfo
```

Compression and decompression return value information.

**Since:** 12

<!--Device-zlib-interface ZipOutputInfo--><!--Device-zlib-interface ZipOutputInfo-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## destLen

```TypeScript
destLen: number
```

Total length of the destination buffer.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ZipOutputInfo-destLen: long--><!--Device-ZipOutputInfo-destLen: long-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## status

```TypeScript
status: ReturnStatus
```

For details, see [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md).

**Type:** [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ZipOutputInfo-status: ReturnStatus--><!--Device-ZipOutputInfo-status: ReturnStatus-End-->

**System capability:** SystemCapability.BundleManager.Zlib
