# isMediaKeySystemSupported

## Modules to Import

```TypeScript
import { drm } from '@kit.DrmKit';
```

## isMediaKeySystemSupported

```TypeScript
function isMediaKeySystemSupported(name: string, mimeType: string, level: ContentProtectionLevel): boolean
```

Checks whether the device supports the combination of the DRM solution, MIME type, and content protection level.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | DRM solution name. Before calling this API, ensure that the DRM solution name is supported by calling [isMediaKeySystemSupported](#ismediakeysystemsupported-2). |
| mimeType | string | Yes | MIME type. The supported MIME types depend on the DRM solution. Before calling this API, ensure that the MIME type is supported by calling [isMediaKeySystemSupported](#ismediakeysystemsupported-1). |
| level | [ContentProtectionLevel](arkts-drm-drm-contentprotectionlevel-e.md) | Yes | Content protection level. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the combination. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let supported: boolean = drm.isMediaKeySystemSupported('com.clearplay.drm', 'video/avc', drm.ContentProtectionLevel.CONTENT_PROTECTION_LEVEL_SW_CRYPTO);
console.info("isMediaKeySystemSupported: ", supported);
```


<a id="ismediakeysystemsupported-1"></a>

## isMediaKeySystemSupported

```TypeScript
function isMediaKeySystemSupported(name: string, mimeType: string): boolean
```

Checks whether the device supports the combination of the DRM solution and MIME type.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | DRM solution name. Before calling this API, ensure that the DRM solution name is supported by calling [isMediaKeySystemSupported](#ismediakeysystemsupported-2). |
| mimeType | string | Yes | MIME type. The supported MIME types depend on the DRM solution. For example, video/avc and video/hevc. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the combination. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let supported: boolean = drm.isMediaKeySystemSupported('com.clearplay.drm', 'video/avc');
console.info("isMediaKeySystemSupported: ", supported);
```


<a id="ismediakeysystemsupported-2"></a>

## isMediaKeySystemSupported

```TypeScript
function isMediaKeySystemSupported(name: string): boolean
```

Checks whether the device supports the specified DRM solution.

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
| boolean | Check result for the support of the DRM solution. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed, the param name's length is zero or too big(exceeds 4096 Bytes). |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let supported: boolean = drm.isMediaKeySystemSupported('com.clearplay.drm');
console.info("isMediaKeySystemSupported: ", supported);
```
