# MediaKeySession

```TypeScript
interface MediaKeySession
```

MediaKeySession implements media key management. Before calling any API in MediaKeySession, you must use [createMediaKeySession](arkts-drm-drm-mediakeysystem-i.md#createmediakeysession) to create a MediaKeySession instance.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Drm.Core

## Modules to Import

```TypeScript
import { drm } from '@kit.DrmKit';
```

## checkMediaKeyStatus

```TypeScript
checkMediaKeyStatus(): MediaKeyStatus[]
```

Checks the status of the media keys in use.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Return value:**

| Type | Description |
| --- | --- |
| [MediaKeyStatus](arkts-drm-drm-mediakeystatus-i.md)[] | Media key status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
let keyStatus: drm.MediaKeyStatus[] =  mediaKeySession.checkMediaKeyStatus();
```

## clearMediaKeys

```TypeScript
clearMediaKeys(): void
```

Clears the media keys in use.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// mediaKeyResponse is obtained from the DRM service. Pass in the actual value as required.
let mediaKeyResponse = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.processMediaKeyResponse(mediaKeyResponse).then((mediaKeyId: Uint8Array) => {
  console.info('processMediaKeyResponse:' + mediaKeyId);
});
mediaKeySession.clearMediaKeys();
```

## destroy

```TypeScript
destroy(): void
```

Destroys this MediaKeySession instance.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.destroy();
```

## generateMediaKeyRequest

```TypeScript
generateMediaKeyRequest(mimeType: string, initData: Uint8Array, mediaKeyType: number, options?: OptionsData[]): Promise<MediaKeyRequest>
```

Generates a media key request. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mimeType | string | Yes | MIME type. The supported DRM solution names can be obtained by calling [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md#ismediakeysystemsupported-1). |
| initData | Uint8Array | Yes | Initial data. |
| mediaKeyType | number | Yes | Type of the media key. The value **0** means an online media key, and **1** means an offline media key. |
| options | [OptionsData](arkts-drm-drm-optionsdata-i.md)[] | No | Optional data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[MediaKeyRequest](arkts-drm-drm-mediakeyrequest-i.md)&gt; | Promise used to return the media key request generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) |  |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// Protection System Specific Header (PSSH) data is embedded in the encrypted stream. For MP4 files, it is located in the pssh box. In DASH streams, it is located in the MPD and MP4 pssh box. For HLS + TS streams, it is located in the m3u8 file and each TS segment. Pass in the actual value as required.
let uint8pssh = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.generateMediaKeyRequest('video/avc', uint8pssh, drm.MediaKeyType.MEDIA_KEY_TYPE_ONLINE).then((mediaKeyRequest: drm.MediaKeyRequest) =>{
  console.info('generateMediaKeyRequest' + mediaKeyRequest);
});
```

## generateOfflineReleaseRequest

```TypeScript
generateOfflineReleaseRequest(mediaKeyId: Uint8Array): Promise<Uint8Array>
```

Generates a request to release offline media keys. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mediaKeyId | Uint8Array | Yes | Array of offline media key IDs. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the request generated if the DRM solution on the device supports the release of offline media keys. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// mediaKeyId is the return value of processMediaKeyResponse or getOfflineMediaKeyIds. Pass in the actual value as required.
let mediaKeyId = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.generateOfflineReleaseRequest(mediaKeyId).then((offlineReleaseRequest: Uint8Array) => {
  console.info('generateOfflineReleaseRequest:' + offlineReleaseRequest);
});
```

## getContentProtectionLevel

```TypeScript
getContentProtectionLevel(): ContentProtectionLevel
```

Obtains the content protection level of this media key session.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ContentProtectionLevel](arkts-drm-drm-contentprotectionlevel-e.md) | Content protection level. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
let contentProtectionLevel: drm.ContentProtectionLevel = mediaKeySession.getContentProtectionLevel();
console.info(`contentProtectionLevel: ${contentProtectionLevel}`);
```

## off('keyRequired')

```TypeScript
off(type: 'keyRequired', callback?: (eventInfo: EventInfo) => void): void
```

Unsubscribes from events indicating that the application requests a media key. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyRequired' | Yes | Event type. The value is fixed at **'keyRequired'**. |
| callback | (eventInfo: EventInfo) =&gt; void | No | Callback used to return the event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.off('keyRequired');
```

## off('keyExpired')

```TypeScript
off(type: 'keyExpired', callback?: (eventInfo: EventInfo) => void): void
```

Unsubscribes from events indicating that a media key expires. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyExpired' | Yes | Event type. The value is fixed at **'keyExpired'**. |
| callback | (eventInfo: EventInfo) =&gt; void | No | Callback used to return the event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.off('keyExpired');
```

## off('vendorDefined')

```TypeScript
off(type: 'vendorDefined', callback?: (eventInfo: EventInfo) => void): void
```

Unsubscribes from vendor-defined events. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'vendorDefined' | Yes | Event type. The value is fixed at **'vendorDefined'**. |
| callback | (eventInfo: EventInfo) =&gt; void | No | Callback used to return the event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.off('vendorDefined');
```

## off('expirationUpdate')

```TypeScript
off(type: 'expirationUpdate', callback?: (eventInfo: EventInfo) => void): void
```

Unsubscribes from events indicating that a media key is updated upon expiry. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'expirationUpdate' | Yes | Event type. The value is fixed at **'expirationUpdate'**. |
| callback | (eventInfo: EventInfo) =&gt; void | No | Callback used to return the event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.off('expirationUpdate');
```

## off('keysChange')

```TypeScript
off(type: 'keysChange', callback?: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void
```

Unsubscribes from events indicating that a media key changes. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keysChange' | Yes | Event type. The value is fixed at **'keysChange'**. |
| callback | (keyInfo: KeysInfo[], newKeyAvailable: boolean) =&gt; void | No | Callback used to return the event information, including a list of key IDs, descriptions of their statuses, and whether each key is available. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.off('keysChange');
```

## on('keyRequired')

```TypeScript
on(type: 'keyRequired', callback: (eventInfo: EventInfo) => void): void
```

Subscribes to events indicating that the application requests a media key. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyRequired' | Yes | Event type. The value is fixed at **'keyRequired'**, which is triggered when the application requires a media key. |
| callback | (eventInfo: EventInfo) =&gt; void | Yes | Callback used to return the event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.on('keyRequired', (eventInfo: drm.EventInfo) => {
  console.info('keyRequired ' + 'extra: ' + eventInfo.extraInfo + 'data: ' + eventInfo.info);
});
```

## on('keyExpired')

```TypeScript
on(type: 'keyExpired', callback: (eventInfo: EventInfo) => void): void
```

Subscribes to events indicating that a media key expires. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyExpired' | Yes | Event type. The value is fixed at **'keyExpired'**, which is triggered when a media key expires. |
| callback | (eventInfo: EventInfo) =&gt; void | Yes | Callback used to return the event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.on('keyExpired', (eventInfo: drm.EventInfo) => {
  console.info('keyExpired ' + 'extra: ' + eventInfo.extraInfo + 'data: ' + eventInfo.info);
});
```

## on('vendorDefined')

```TypeScript
on(type: 'vendorDefined', callback: (eventInfo: EventInfo) => void): void
```

Subscribes to vendor-defined events. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'vendorDefined' | Yes | Event type. The value is fixed at **'vendorDefined'**, which is triggered when a vendor-defined event occurs. |
| callback | (eventInfo: EventInfo) =&gt; void | Yes | Callback used to return the event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.on('vendorDefined', (eventInfo: drm.EventInfo) => {
  console.info('vendorDefined ' + 'extra: ' + eventInfo.extraInfo + 'data: ' + eventInfo.info);
});
```

## on('expirationUpdate')

```TypeScript
on(type: 'expirationUpdate', callback: (eventInfo: EventInfo) => void): void
```

Subscribes to events indicating that a media key is updated upon expiry. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'expirationUpdate' | Yes | Event type. The value is fixed at **'expirationUpdate'**, which is triggered when a media key is updated upon expiry. |
| callback | (eventInfo: EventInfo) =&gt; void | Yes | Callback used to return the event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.on('expirationUpdate', (eventInfo: drm.EventInfo) => {
  console.info('expirationUpdate ' + 'extra: ' + eventInfo.extraInfo + 'data: ' + eventInfo.info);
});
```

## on('keysChange')

```TypeScript
on(type: 'keysChange', callback: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void
```

Subscribes to events indicating that a media key changes. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keysChange' | Yes | Event type. The value is fixed at **'keysChange'**, which is triggered when a media key changes. |
| callback | (keyInfo: KeysInfo[], newKeyAvailable: boolean) =&gt; void | Yes | Callback used to return the event information, including a list of key IDs, descriptions of their statuses, and whether each key is available. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.on('keysChange', (keyInfo: drm.KeysInfo[], newKeyAvailable: boolean) => {
  for (let i = 0; i < keyInfo.length; i++) {
    console.info('keysChange' + 'keyId:' + keyInfo[i].keyId + ' data:' + keyInfo[i].value);
  }
});
```

## processMediaKeyResponse

```TypeScript
processMediaKeyResponse(response: Uint8Array): Promise<Uint8Array>
```

Processes a media key response. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| response | Uint8Array | Yes | Media key response. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return an array of media key IDs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// mediaKeyResponse is obtained from the DRM service. Pass in the actual value as required.
let mediaKeyResponse = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.processMediaKeyResponse(mediaKeyResponse).then((mediaKeyId: Uint8Array) => {
  console.info('processMediaKeyResponse:' + mediaKeyId);
});
```

## processOfflineReleaseResponse

```TypeScript
processOfflineReleaseResponse(mediaKeyId: Uint8Array, response: Uint8Array): Promise<void>
```

Processes a response to a request for releasing offline media keys. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mediaKeyId | Uint8Array | Yes | Array of offline media key IDs. |
| response | Uint8Array | Yes | Response to the request for releasing offline media keys. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result if the DRM solution on the device supports the release of offline media keys. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// mediaKeyId is the return value of processMediaKeyResponse or getOfflineMediaKeyIds. Apply for memory based on the actual length.
let mediaKeyId = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.generateOfflineReleaseRequest(mediaKeyId).then((offlineReleaseRequest: Uint8Array) => {
  console.info('generateOfflineReleaseRequest:' + offlineReleaseRequest);
});
// offlineReleaseResponse is obtained from the DRM service. Apply for memory based on the actual length.
let offlineReleaseResponse = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.processOfflineReleaseResponse(mediaKeyId, offlineReleaseResponse).then(() => {
  console.info('processOfflineReleaseResponse');
});
```

## requireSecureDecoderModule

```TypeScript
requireSecureDecoderModule(mimeType: string): boolean
```

Checks whether secure decoding is required.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mimeType | string | Yes | MIME type. The supported MIME types depend on the DRM solution and can be obtained by calling [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md#ismediakeysystemsupported-1). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether secure decoding is required. **true** if required, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
let status: boolean = mediaKeySession.requireSecureDecoderModule('video/avc');
```

## restoreOfflineMediaKeys

```TypeScript
restoreOfflineMediaKeys(mediaKeyId: Uint8Array): Promise<void>
```

Restores offline media keys. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Drm.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mediaKeyId | Uint8Array | Yes | Array of offline media key IDs. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-unknown-error) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-service-exception) | Fatal service error, for example, service died. |

**Examples**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// mediaKeyId is the return value of processMediaKeyResponse or getOfflineMediaKeyIds. Pass in the actual value as required.
let mediaKeyId = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.restoreOfflineMediaKeys(mediaKeyId).then(() => {
  console.info("restoreOfflineMediaKeys");
});
```
