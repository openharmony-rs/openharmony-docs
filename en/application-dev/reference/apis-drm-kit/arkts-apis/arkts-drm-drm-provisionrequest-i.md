# ProvisionRequest

```TypeScript
interface ProvisionRequest
```

Defines a device certificate provisioning request.

**Since:** 11

<!--Device-drm-interface ProvisionRequest--><!--Device-drm-interface ProvisionRequest-End-->

**System capability:** SystemCapability.Multimedia.Drm.Core

## Modules to Import

```TypeScript
import { drm } from '@kit.DrmKit';
```

## data

```TypeScript
data: Uint8Array
```

Binary data of the provisioning request.

**Type:** Uint8Array

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 14.

<!--Device-ProvisionRequest-data: Uint8Array--><!--Device-ProvisionRequest-data: Uint8Array-End-->

**System capability:** SystemCapability.Multimedia.Drm.Core

## defaultURL

```TypeScript
defaultURL: string
```

URL of the device certificate provisioning server.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 14.

<!--Device-ProvisionRequest-defaultURL: string--><!--Device-ProvisionRequest-defaultURL: string-End-->

**System capability:** SystemCapability.Multimedia.Drm.Core
