# DictionaryOutputInfo

```TypeScript
interface DictionaryOutputInfo
```

InflateGetDictionary and deflateGetDictionary return value information.

**Since:** 12

<!--Device-zlib-interface DictionaryOutputInfo--><!--Device-zlib-interface DictionaryOutputInfo-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## dictionaryLength

```TypeScript
dictionaryLength: number
```

Length of a dictionary.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DictionaryOutputInfo-dictionaryLength: int--><!--Device-DictionaryOutputInfo-dictionaryLength: int-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## status

```TypeScript
status: ReturnStatus
```

For details, see [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md).

**Type:** [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DictionaryOutputInfo-status: ReturnStatus--><!--Device-DictionaryOutputInfo-status: ReturnStatus-End-->

**System capability:** SystemCapability.BundleManager.Zlib
