# MediaKeySystemInfo

Defines the DRM information for encrypted content.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Drm.Core

## Modules to Import

```TypeScript
import { drm } from '@kit.DrmKit';
```

## pssh

```TypeScript
pssh: Uint8Array
```

PSSH(protection scheme specific header) contain drm info.

**Type:** Uint8Array

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

## uuid

```TypeScript
uuid: string
```

Drm system ID.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core
