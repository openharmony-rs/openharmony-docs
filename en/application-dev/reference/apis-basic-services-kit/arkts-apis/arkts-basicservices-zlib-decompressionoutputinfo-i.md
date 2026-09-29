# DecompressionOutputInfo

```TypeScript
interface DecompressionOutputInfo
```

Uncompress2 return value information.

**Since:** 12

<!--Device-zlib-interface DecompressionOutputInfo--><!--Device-zlib-interface DecompressionOutputInfo-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## destLength

```TypeScript
destLength: number
```

Total length of the destination buffer.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DecompressionOutputInfo-destLength: long--><!--Device-DecompressionOutputInfo-destLength: long-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## sourceLength

```TypeScript
sourceLength: number
```

Length of the source buffer.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DecompressionOutputInfo-sourceLength: long--><!--Device-DecompressionOutputInfo-sourceLength: long-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## status

```TypeScript
status: ReturnStatus
```

For details, see [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md).

**Type:** [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DecompressionOutputInfo-status: ReturnStatus--><!--Device-DecompressionOutputInfo-status: ReturnStatus-End-->

**System capability:** SystemCapability.BundleManager.Zlib
