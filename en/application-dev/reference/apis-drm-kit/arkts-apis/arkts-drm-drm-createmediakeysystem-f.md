# createMediaKeySystem

## Modules to Import

```TypeScript
import { drm } from '@kit.DrmKit';
```

## createMediaKeySystem

```TypeScript
function createMediaKeySystem(name: string): MediaKeySystem
```

Creates a MediaKeySystem instance.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | DRM solution name, for example, **"com.clearplay.drm"**. |

**Return value:**

| Type | Description |
| --- | --- |
| [MediaKeySystem](arkts-drm-drm-mediakeysystem-i.md) | MediaKeySystem instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700103](../errorcode-drm.md#24700103-too-many-mediakeysystem-instances) | Meet max MediaKeySystem num limit. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';
// name indicates the DRM solution name. You can obtain the DRM solution name supported by the device through the drm.getMediaKeySystems API, for example, **com.clearplay.drm**.
let name = 'com.clearplay.drm';
let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem(name);
console.info(`createMediaKeySystem success, name: ${name}`);
```
