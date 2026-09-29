# MediaKeyRequest

```TypeScript
interface MediaKeyRequest
```

Defines a media key request.

**Since:** 11

<!--Device-drm-interface MediaKeyRequest--><!--Device-drm-interface MediaKeyRequest-End-->

**System capability:** SystemCapability.Multimedia.Drm.Core

## Modules to Import

```TypeScript
import { drm } from '@kit.DrmKit';
```

## data

```TypeScript
data: Uint8Array
```

Binary data of the media key request.

**Type:** Uint8Array

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-MediaKeyRequest-data: Uint8Array--><!--Device-MediaKeyRequest-data: Uint8Array-End-->

**System capability:** SystemCapability.Multimedia.Drm.Core

## defaultURL

```TypeScript
defaultURL: string
```

URL of the license server.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-MediaKeyRequest-defaultURL: string--><!--Device-MediaKeyRequest-defaultURL: string-End-->

**System capability:** SystemCapability.Multimedia.Drm.Core

## mediaKeyRequestType

```TypeScript
mediaKeyRequestType: MediaKeyRequestType
```

Type of the media key request.

**Type:** [MediaKeyRequestType](arkts-drm-drm-mediakeyrequesttype-e.md)

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-MediaKeyRequest-mediaKeyRequestType: MediaKeyRequestType--><!--Device-MediaKeyRequest-mediaKeyRequestType: MediaKeyRequestType-End-->

**System capability:** SystemCapability.Multimedia.Drm.Core
