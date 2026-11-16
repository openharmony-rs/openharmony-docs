# Interfaces (Others)

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=2058a696dfae025aecb385ae301d1efe33545c92 translatedAt=2026-11-04T04:13:45.986Z pushedAt=2026-11-04T10:12:50.066Z nl=1 -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
## ProvisionRequest

Defines a device certificate provisioning request.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name     | Type                       | Read-Only| Optional| Description        |
| -------- | ------------------------|----|----| ------------- |
| data   | Uint8Array| No | No | Binary data of the provisioning request.     |
| defaultURL     | string         | No  | No  | URL of the Provision service (device certificate request service). It must comply with the URL format specification, and HTTPS is recommended.       |

## OptionsData

Defines optional parameters for a device certificate request.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name     | Type                       | Read-Only| Optional| Description        |
| -------- | --------------------------|----|----| ------------- |
| name   | string | No  | No  | Name of the optional data, used to identify the key of the optional data.      |
| value     | string             | No  | No  | Value of the optional data, corresponding to the name of the optional data. |

## MediaKeyRequest

Defines a media key request.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name     | Type                      | Read-Only| Optional| Description        |
| -------- | --------------------------|----|----| ------------- |
| mediaKeyRequestType   | [MediaKeyRequestType](arkts-apis-drm-e.md#mediakeyrequesttype)| No  | No  | Type of the media key request. It is used to specify the scenario for requesting a key, including the initial request, renewal request, release request, update request, and other types.      |
| data     | Uint8Array               |  No  | No  | Media key request data, which contains the raw byte data of the media key request.       |
| defaultURL     | string              |  No  | No  | URL of the media key service. It must comply with the URL format specification, and HTTPS is recommended.       |

## EventInfo

Defines the DRM event information.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name     | Type                        | Read-Only| Optional   | Description        |
| -------- | --------------------------|----|-------| ------------- |
| info   | Uint8Array |   No | No      | Event information data, containing the raw byte data related to the event. The specific format and content depend on the event type.      |
| extraInfo     | string             |   No | No  | Event extension information, providing additional description or metadata of the event. The specific content depends on the event type. |

## StatisticKeyValue

Defines a key-value pair for metrics.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name     | Type                      | Read-Only| Optional  | Description        |
| -------- | -------------------------|----|------| ------------- |
| name   | string | No  | No     | Name of the metric record, used as the key name to identify the metric.      |
| value     | string              | No   | No   | Value of the metric record, indicating the value or status of the metric. |

## MediaKeyStatus

Defines a status attribute for a media key.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name      | Type                        | Read-Only | Optional      | Description         |
| -------- | -------------------------|----|---------| ------------- |
| name   | string | No  |  No       | Name of the media key status type. Common types include the media key expiration time and content protection security level.      |
| value     | string            | No   | No  | Media key status value, which indicates the specific status information corresponding to the status name. |

## KeysInfo

Defines the key information of a media key.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name     | Type                      | Read-Only| Optional| Description        |
| -------- | -------------------------|----|---| ------------- |
| keyId   | Uint8Array | No  | No | Media key ID, a byte array used to uniquely identify a media key, usually 16 bytes (128 bits).      |
| value     | string                 | No | No| Media key status.|

## MediaKeySystemInfo

Defines the DRM information for encrypted content.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name     | Type                     | Read-Only| Optional| Description        |
| -------- | ------------------------|----|--| ------------- |
| uuid   | string |  No  | No | Unique identifier of the DRM content protection system, which must be in a valid UUID format. If an invalid UUID is passed in, the API returns a failure.      |
| pssh     | Uint8Array              |  No  | No | DRM content protection system-specific header, a byte array that contains DRM-related metadata and initialization data. The specific structure is defined by the DRM scheme. |

## MediaKeySystemDescription<sup>12+</sup>

Defines the DRM plugin information.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.Drm.Core

| Name     | Type                       | Read-Only| Optional| Description        |
| -------- | --------------------------|----|--| ------------- |
| name   | string | No  | No | Name of the plugin, a string used to identify the DRM plugin. It is usually defined by the DRM scheme provider.      |
| uuid   | string | No  | No | Unique identifier of the plugin, which must be in a valid UUID format. If an invalid UUID is passed in, the API returns a failure. |
