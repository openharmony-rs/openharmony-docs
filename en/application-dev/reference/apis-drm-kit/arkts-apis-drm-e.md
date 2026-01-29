# Enums

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## DrmErrorCode

Enumerates the DRM error codes.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| ERROR_UNKNOWN       | 24700101    | Unknown error.  |
| MAX_SYSTEM_NUM_REACHED   | 24700103    | Maximum number of MediaKeySystem instances (64) reached.   |
| MAX_SESSION_NUM_REACHED    | 24700104    | Maximum number of MediaKeySession instances (64) reached.    |
| SERVICE_FATAL_ERROR  | 24700201    | DRM service fatal error.    |

## PreDefinedConfigName

Enumerates the predefined configuration properties.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| CONFIG_DEVICE_VENDOR        | 'vendor'    | Plugin vendor name, which corresponds to the value of **vendor** in the return value of [getConfigurationString](arkts-apis-drm-MediaKeySystem.md#getconfigurationstring).  |
| CONFIG_DEVICE_VERSION    | 'version'    | Plugin version number, which corresponds to the value of **version** in the return value of [getConfigurationString](arkts-apis-drm-MediaKeySystem.md#getconfigurationstring).    |
| CONFIG_DEVICE_DESCRIPTION     | 'description'    | Device description, which corresponds to the value of **description** in the return value of [getConfigurationString](arkts-apis-drm-MediaKeySystem.md#getconfigurationstring).     |
| CONFIG_DEVICE_ALGORITHMS   | 'algorithms'    | Supported algorithms, which correspond to the value of **algorithms** in the return value of [getConfigurationString](arkts-apis-drm-MediaKeySystem.md#getconfigurationstring).    |
| CONFIG_DEVICE_UNIQUE_ID    | 'deviceUniqueId'    | Unique device ID, which corresponds to the value of **deviceUniqueId** in the return value of [getConfigurationByteArray](arkts-apis-drm-MediaKeySystem.md#getconfigurationbytearray).    |
| CONFIG_SESSION_MAX         | 'maxSessionNum'    | Maximum number of supported sessions, which corresponds to the value of **maxSessionNum** in the return value of [getConfigurationString](arkts-apis-drm-MediaKeySystem.md#getconfigurationstring).    |
| CONFIG_SESSION_CURRENT   | 'currentSessionNum'    | Number of active sessions, which corresponds to the value of **currentSessionNum** in the return value of [getConfigurationString](arkts-apis-drm-MediaKeySystem.md#getconfigurationstring).    |

## MediaKeyType

Enumerates the types of media keys.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| MEDIA_KEY_TYPE_OFFLINE        | 0    | Offline media key.  |
| MEDIA_KEY_TYPE_ONLINE   | 1    | Online media key.    |

## OfflineMediaKeyStatus

Enumerates the statuses of offline media keys.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| OFFLINE_MEDIA_KEY_STATUS_UNKNOWN        | 0    | Unknown status.  |
| OFFLINE_MEDIA_KEY_STATUS_USABLE   | 1    | The media key is available.    |
| OFFLINE_MEDIA_KEY_STATUS_INACTIVE     | 2    | The media key is inactive.      |

## CertificateStatus

Enumerates the statuses of device certificates.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| CERT_STATUS_PROVISIONED        | 0    | A device certificate is provisioned.  |
| CERT_STATUS_NOT_PROVISIONED   | 1    | A device certificate is not provisioned.    |
| CERT_STATUS_EXPIRED    | 2    | The device certificate has expired.      |
| CERT_STATUS_INVALID  | 3    | The device certificate is invalid.    |
| CERT_STATUS_UNAVAILABLE  | 4    | The device certificate is unavailable.    |

## MediaKeyRequestType

Enumerates the types of media key requests.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| MEDIA_KEY_REQUEST_TYPE_UNKNOWN        | 0    | Unknown type.  |
| MEDIA_KEY_REQUEST_TYPE_INITIAL    | 1    | Initial request.    |
| MEDIA_KEY_REQUEST_TYPE_RENEWAL     | 2    | Renewal request.      |
| MEDIA_KEY_REQUEST_TYPE_RELEASE   | 3    | Release request.    |
| MEDIA_KEY_REQUEST_TYPE_NONE    | 4    | No request.    |
| MEDIA_KEY_REQUEST_TYPE_UPDATE    | 5    | Update request.    |

## ContentProtectionLevel

Enumerates the content protection levels.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| CONTENT_PROTECTION_LEVEL_UNKNOWN        | 0    | Unknown content protection level.  |
| CONTENT_PROTECTION_LEVEL_SW_CRYPTO   | 1    | Software-based content protection.    |
| CONTENT_PROTECTION_LEVEL_HW_CRYPTO    | 2    | Hardware-based content protection.      |
| CONTENT_PROTECTION_LEVEL_ENHANCED_HW  | 3    | Enhanced hardware-based content protection.    |
| CONTENT_PROTECTION_LEVEL_MAX  | 4    | Maximum content protection level.    |
