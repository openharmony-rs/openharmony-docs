# GzErrorOutputInfo

```TypeScript
interface GzErrorOutputInfo
```

GzError return value information.

**Since:** 12

<!--Device-zlib-interface GzErrorOutputInfo--><!--Device-zlib-interface GzErrorOutputInfo-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## status

```TypeScript
status: ReturnStatus
```

Return Zlib status ReturnStatus the specific meaning is defined as enum.

**Type:** [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzErrorOutputInfo-status: ReturnStatus--><!--Device-GzErrorOutputInfo-status: ReturnStatus-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## statusMsg

```TypeScript
statusMsg: string
```

The last status message reported on the zlib file.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GzErrorOutputInfo-statusMsg: string--><!--Device-GzErrorOutputInfo-statusMsg: string-End-->

**System capability:** SystemCapability.BundleManager.Zlib
