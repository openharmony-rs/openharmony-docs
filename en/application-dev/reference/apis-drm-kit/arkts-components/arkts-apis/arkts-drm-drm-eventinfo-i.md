# EventInfo

```TypeScript
interface EventInfo
```

Defines the DRM event information.

**Since:** 11

<!--Device-drm-interface EventInfo--><!--Device-drm-interface EventInfo-End-->

**System capability:** SystemCapability.Multimedia.Drm.Core

## Modules to Import

```TypeScript
import { drm } from '@kit.DrmKit';
```

## extraInfo

```TypeScript
extraInfo: string
```

Additional event context.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-EventInfo-extraInfo: string--><!--Device-EventInfo-extraInfo: string-End-->

**System capability:** SystemCapability.Multimedia.Drm.Core

## info

```TypeScript
info: Uint8Array
```

Event payload data.

**Type:** Uint8Array

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-EventInfo-info: Uint8Array--><!--Device-EventInfo-info: Uint8Array-End-->

**System capability:** SystemCapability.Multimedia.Drm.Core
