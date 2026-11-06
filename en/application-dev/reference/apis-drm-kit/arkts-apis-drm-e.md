# Enums

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=6a406b0bb845b0da8494b1faec75e3f21f431926 translatedAt=2026-11-03T06:42:39.758Z pushedAt=2026-11-04T03:11:19.894Z nl=1 -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## DrmErrorCode

Enumerates the DRM error codes.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| ERROR_UNKNOWN       | 24700101    | Unknown error. Returned when an exception that cannot be classified occurs. Check whether the input parameters are valid and whether the DRM service is running properly.   |
| MAX_SYSTEM_NUM_REACHED   | 24700103    | The number of MediaKeySystem instances exceeds the upper limit (64). Call [destroy](arkts-apis-drm-MediaKeySystem.md#destroy) to destroy the unnecessary MediaKeySystem instances and try again.    |
| MAX_SESSION_NUM_REACHED    | 24700104    | The number of MediaKeySession instances exceeds the upper limit (64). Call [destroy](arkts-apis-drm-MediaKeySession.md#destroy) to destroy the unnecessary MediaKeySession instances and try again.     |
| SERVICE_FATAL_ERROR  | 24700201    | DRM service error. Returned when a fatal error occurs in the DRM service. Possible causes: insufficient system resources, DRM service process crash, or system exception. Restart the application or the device and try again.     |

## PreDefinedConfigName

Enumerates the predefined configuration properties.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| CONFIG_DEVICE_VENDOR        | 'vendor'    | Plugin vendor name, which corresponds to the value of **vendor** in the return value of [getConfigurationString](arkts-apis-drm-MediaKeySystem.md#getconfigurationstring).  |
| CONFIG_DEVICE_VERSION    | 'version'    | Plugin version number, obtained through the [getConfigurationString](arkts-apis-drm-MediaKeySystem.md#getconfigurationstring) API to get the corresponding configuration value of the version.     |
| CONFIG_DEVICE_DESCRIPTION     | 'description'    | Device description, obtained through the [getConfigurationString](arkts-apis-drm-MediaKeySystem.md#getconfigurationstring) API to get the corresponding configuration value of the description.      |
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
| MEDIA_KEY_TYPE_OFFLINE | 0 | Offline media key, used in offline playback scenarios. |
| MEDIA_KEY_TYPE_ONLINE | 1 | Online media key, used in online playback scenarios. |

## OfflineMediaKeyStatus

Enumerates the statuses of offline media keys.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| OFFLINE_MEDIA_KEY_STATUS_UNKNOWN        | 0    | Unknown status.  |
| OFFLINE_MEDIA_KEY_STATUS_USABLE   | 1    | The media key is available.    |
| OFFLINE_MEDIA_KEY_STATUS_INACTIVE     | 2    | Inactive state, possibly caused by key expiration or server-side disabling, requiring the key to be re-obtained.       |

## CertificateStatus

Enumerates the statuses of device certificates.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| CERT_STATUS_PROVISIONED        | 0    | A device certificate is provisioned.  |
| CERT_STATUS_NOT_PROVISIONED   | 1    | A device certificate is not provisioned.    |
| CERT_STATUS_EXPIRED    | 2    | The device certificate has expired. A new device certificate needs to be applied for.       |
| CERT_STATUS_INVALID  | 3    | The device certificate is invalid.    |
| CERT_STATUS_UNAVAILABLE  | 4    | The device certificate is unavailable.    |

## MediaKeyRequestType

Enumerates the types of media key requests.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| MEDIA_KEY_REQUEST_TYPE_UNKNOWN        | 0    | Unknown type.  |
| MEDIA_KEY_REQUEST_TYPE_INITIAL    | 1    | Initial request, triggered when a media key is obtained for the first time.     |
| MEDIA_KEY_REQUEST_TYPE_RENEWAL     | 2    | Renewal request, triggered when a license is about to expire or its validity period needs to be extended.       |
| MEDIA_KEY_REQUEST_TYPE_RELEASE   | 3    | Release request, triggered when an offline key is actively released or a session is closed, used to notify the server to release resources.     |
| MEDIA_KEY_REQUEST_TYPE_NONE    | 4    | No request.    |
| MEDIA_KEY_REQUEST_TYPE_UPDATE    | 5    | Update request.    |

## ContentProtectionLevel

Enumerates the content protection levels.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name                      | Value  | Description           |
| ------------------------- | ---- | ------------    |
| CONTENT_PROTECTION_LEVEL_UNKNOWN        | 0    | Unknown content protection level.  |
| CONTENT_PROTECTION_LEVEL_SW_CRYPTO   | 1    | Software content protection level. Uses software decryption and is suitable for playback scenarios with low security requirements.     |
| CONTENT_PROTECTION_LEVEL_HW_CRYPTO    | 2    | Hardware content protection level. Uses hardware decryption, provides higher security, and is suitable for most commercial content playback scenarios.       |
| CONTENT_PROTECTION_LEVEL_ENHANCED_HW  | 3    | Hardware-enhanced content protection level. Uses a hardware security module for decryption, provides the highest security, and is suitable for high-value content playback scenarios.     |
| CONTENT_PROTECTION_LEVEL_MAX  | 4    | Maximum content protection level.    |
