# @ohos.multimedia.drm(Defines the DRM capability.)

The Digital Rights Management (DRM) framework enables you to develop digital rights management features for audio and video services. By calling the DRM plugins provided by the system, you can achieve the following:

- DRM certificate management: Generate certificate requests and handle certificate responses to facilitate  
certificate provisioning (downloading).  
- DRM media key management: Generate media key requests, manage media key responses, and handle offline media keys.  
- DRM content authorization: Allow DRM plugins to authorize content based on media key permissions.  
- DRM content decryption: Decrypt DRM content to support media playback functionality.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Drm.Core

## Modules to Import

```TypeScript
import { drm } from '@kit.DrmKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createMediaKeySystem](arkts-drm-drm-createmediakeysystem-f.md) | Creates a MediaKeySystem instance. |
| [getMediaKeySystems](arkts-drm-drm-getmediakeysystems-f.md) | Obtains the list of plugins supported by the device. |
| [getMediaKeySystemUuid](arkts-drm-drm-getmediakeysystemuuid-f.md) | Obtains the UUID of the DRM content protection system supported by the specified DRM solution. |
| [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md) | Checks whether the device supports the combination of the DRM solution, MIME type, and content protection level. |
| [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md) | Checks whether the device supports the combination of the DRM solution and MIME type. |
| [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md) | Checks whether the device supports the specified DRM solution. |

### Interfaces

| Name | Description |
| --- | --- |
| [EventInfo](arkts-drm-drm-eventinfo-i.md) | Defines the DRM event information. |
| [KeysInfo](arkts-drm-drm-keysinfo-i.md) | Defines the status information of a media key. |
| [MediaKeyRequest](arkts-drm-drm-mediakeyrequest-i.md) | Defines a media key request. |
| [MediaKeySession](arkts-drm-drm-mediakeysession-i.md) | MediaKeySession implements media key management. Before calling any API in MediaKeySession, you must use [createMediaKeySession](arkts-drm-drm-mediakeysystem-i.md#createmediakeysession) to create a MediaKeySession instance. |
| [MediaKeyStatus](arkts-drm-drm-mediakeystatus-i.md) | Defines a status attribute for a media key. |
| [MediaKeySystem](arkts-drm-drm-mediakeysystem-i.md) | MediaKeySystem manages MediaKeySystem instances, handles device certificate (DRM certificate) requests and processing, creates sessions, manages offline media keys, obtains DRM metrics, and obtain device configurations. Before calling any API in MediaKeySystem, you must use [createMediaKeySystem](arkts-drm-drm-createmediakeysystem-f.md) to create a MediaKeySystem instance. |
| [MediaKeySystemDescription](arkts-drm-drm-mediakeysystemdescription-i.md) | Defines the DRM plugin information. |
| [MediaKeySystemInfo](arkts-drm-drm-mediakeysysteminfo-i.md) | Defines the DRM information for encrypted content. |
| [OptionsData](arkts-drm-drm-optionsdata-i.md) | Defines optional parameters for a device certificate request. |
| [ProvisionRequest](arkts-drm-drm-provisionrequest-i.md) | Defines a device certificate provisioning request. |
| [StatisticKeyValue](arkts-drm-drm-statistickeyvalue-i.md) | Defines a key-value pair for DRM metrics. |

### Enums

| Name | Description |
| --- | --- |
| [CertificateStatus](arkts-drm-drm-certificatestatus-e.md) | Enumerates the statuses of device certificates. |
| [ContentProtectionLevel](arkts-drm-drm-contentprotectionlevel-e.md) | Enumerates the content protection levels. |
| [DrmErrorCode](arkts-drm-drm-drmerrorcode-e.md) | Enumerates the DRM error codes. |
| [MediaKeyRequestType](arkts-drm-drm-mediakeyrequesttype-e.md) | Enumerates the types of media key requests. |
| [MediaKeyType](arkts-drm-drm-mediakeytype-e.md) | Enumerates the types of media keys. |
| [OfflineMediaKeyStatus](arkts-drm-drm-offlinemediakeystatus-e.md) | Enumerates the statuses of offline media keys. |
| [PreDefinedConfigName](arkts-drm-drm-predefinedconfigname-e.md) | Enumerates the predefined configuration properties. |
