# native_mediakeysystem.h

## Overview

The file declares the MediaKeySystem APIs for DRM operations. The APIs can be used to check the support for a DRM solution, create a media key session, obtain and set configurations, obtain DRM metrics, obtain the content protection level, generate media key system requests, process responses to media key system requests, listen for events, and manage offline media keys.

**Library**: libnative_drm.so

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Related module**: [Drm](capi-drm.md)

## Summary

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef Drm_ErrCode (\*MediaKeySystem_Callback)(DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)](#mediakeysystem_callback) | MediaKeySystem_Callback | Call back will be invoked when event triggers. |
| [typedef Drm_ErrCode (\*OH_MediaKeySystem_Callback)(MediaKeySystem *mediaKeySystem, DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)](#oh_mediakeysystem_callback) | OH_MediaKeySystem_Callback | Call back will be invoked when event triggers. |
| [Drm_ErrCode OH_MediaKeySystem_SetCallback(MediaKeySystem *mediaKeySystem, OH_MediaKeySystem_Callback callback)](#oh_mediakeysystem_setcallback) | - | Set media key system event callback. |
| [Drm_ErrCode OH_MediaKeySystem_GetMediaKeySystems(DRM_MediaKeySystemDescription *descs, uint32_t *count)](#oh_mediakeysystem_getmediakeysystems) | - | Acquire supported media key systems' name and uuid. |
| [bool OH_MediaKeySystem_IsSupported(const char *name)](#oh_mediakeysystem_issupported) | - | Checks whether the device supports the specified DRM solution. |
| [bool OH_MediaKeySystem_IsSupported2(const char *name, const char *mimeType)](#oh_mediakeysystem_issupported2) | - | Checks whether the device supports the combination of the DRM solution and MIME type. |
| [bool OH_MediaKeySystem_IsSupported3(const char *name, const char *mimeType, DRM_ContentProtectionLevel contentProtectionLevel)](#oh_mediakeysystem_issupported3) | - | Checks whether the device supports the combination of the DRM solution, MIME type, and content protection level. |
| [Drm_ErrCode OH_MediaKeySystem_Create(const char *name, MediaKeySystem **mediaKeySystem)](#oh_mediakeysystem_create) | - | Creates a media key system instance from the name. |
| [Drm_ErrCode OH_MediaKeySystem_SetConfigurationString(MediaKeySystem *mediaKeySystem, const char *configName, const char *value)](#oh_mediakeysystem_setconfigurationstring) | - | Set media key system configuration value by name. |
| [Drm_ErrCode OH_MediaKeySystem_GetConfigurationString(MediaKeySystem *mediaKeySystem, const char *configName, char *value, int32_t valueLen)](#oh_mediakeysystem_getconfigurationstring) | - | Get media key system configuration value by name. |
| [Drm_ErrCode OH_MediaKeySystem_SetConfigurationByteArray(MediaKeySystem *mediaKeySystem, const char *configName, uint8_t *value, int32_t valueLen)](#oh_mediakeysystem_setconfigurationbytearray) | - | Set media key system configuration value by name. |
| [Drm_ErrCode OH_MediaKeySystem_GetConfigurationByteArray(MediaKeySystem *mediaKeySystem, const char *configName, uint8_t *value, int32_t *valueLen)](#oh_mediakeysystem_getconfigurationbytearray) | - | Get media key system configuration value by name. |
| [Drm_ErrCode OH_MediaKeySystem_GetStatistics(MediaKeySystem *mediaKeySystem, DRM_Statistics *statistics)](#oh_mediakeysystem_getstatistics) | - | Get media key system statistics info. |
| [Drm_ErrCode OH_MediaKeySystem_GetMaxContentProtectionLevel(MediaKeySystem *mediaKeySystem, DRM_ContentProtectionLevel *contentProtectionLevel)](#oh_mediakeysystem_getmaxcontentprotectionlevel) | - | Get the max content protection level media key system supported. |
| [Drm_ErrCode OH_MediaKeySystem_SetMediaKeySystemCallback(MediaKeySystem *mediaKeySystem, MediaKeySystem_Callback callback)](#oh_mediakeysystem_setmediakeysystemcallback) | - | Set media key system event callback. |
| [Drm_ErrCode OH_MediaKeySystem_CreateMediaKeySession(MediaKeySystem *mediaKeySystem, DRM_ContentProtectionLevel *level, MediaKeySession **mediaKeySession)](#oh_mediakeysystem_createmediakeysession) | - | Create a media key session instance. |
| [Drm_ErrCode OH_MediaKeySystem_GenerateKeySystemRequest(MediaKeySystem *mediaKeySystem, uint8_t *request, int32_t *requestLen, char *defaultUrl, int32_t defaultUrlLen)](#oh_mediakeysystem_generatekeysystemrequest) | - | Generate a media key system provision request. |
| [Drm_ErrCode OH_MediaKeySystem_ProcessKeySystemResponse(MediaKeySystem *mediaKeySystem, uint8_t *response, int32_t responseLen)](#oh_mediakeysystem_processkeysystemresponse) | - | Process a media key system provision response. |
| [Drm_ErrCode OH_MediaKeySystem_GetOfflineMediaKeyIds(MediaKeySystem *mediaKeySystem, DRM_OfflineMediakeyIdArray *offlineMediaKeyIds)](#oh_mediakeysystem_getofflinemediakeyids) | - | Get offline media key ids . |
| [Drm_ErrCode OH_MediaKeySystem_GetOfflineMediaKeyStatus(MediaKeySystem *mediaKeySystem, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen, DRM_OfflineMediaKeyStatus *status)](#oh_mediakeysystem_getofflinemediakeystatus) | - | Get offline media key status. |
| [Drm_ErrCode OH_MediaKeySystem_ClearOfflineMediaKeys(MediaKeySystem *mediaKeySystem, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen)](#oh_mediakeysystem_clearofflinemediakeys) | - | Clear an offline media key by id. |
| [Drm_ErrCode OH_MediaKeySystem_GetCertificateStatus(MediaKeySystem *mediaKeySystem, DRM_CertificateStatus *certStatus)](#oh_mediakeysystem_getcertificatestatus) | - | Get certificate status of media key system. |
| [Drm_ErrCode OH_MediaKeySystem_Destroy(MediaKeySystem *mediaKeySystem)](#oh_mediakeysystem_destroy) | - | Destroy a media key system instance. |

### Variable

| Name | Description |
| -- | -- |
| Drm_ErrCode (*MediaKeySystem_Callback)(DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra) | Call back will be invoked when event triggers.<br>**Since**: 11 |
| Drm_ErrCode (*OH_MediaKeySystem_Callback)(MediaKeySystem *mediaKeySystem, DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra) | Call back will be invoked when event triggers.<br>**Since**: 12 |

## Function description

### MediaKeySystem_Callback()

```c
typedef Drm_ErrCode (*MediaKeySystem_Callback)(DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)
```

**Description**

Call back will be invoked when event triggers.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| DRM_EventType eventType | Event type. |
| uint8_t \*info | Event info gotten from media key system. |
| int32_t infoLen | Event info len. |
| char \*extra | Extra info gotten from media key system. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | DRM_ERR_INVALID_VAL when the params checked failure, return DRM_ERR_OK when function called successfully. |

### OH_MediaKeySystem_Callback()

```c
typedef Drm_ErrCode (*OH_MediaKeySystem_Callback)(MediaKeySystem *mediaKeySystem, DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)
```

**Description**

Call back will be invoked when event triggers.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem \*mediaKeySystem | MediaKeySystem instance. |
| DRM_EventType eventType | Event type. |
| uint8_t \*info | Event info gotten from media key system. |
| int32_t infoLen | Event info len. |
| char \*extra | Extra info gotten from media key system. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | DRM_ERR_INVALID_VAL when the params checked failure, return DRM_ERR_OK when function called successfully. |

### OH_MediaKeySystem_SetCallback()

```c
Drm_ErrCode OH_MediaKeySystem_SetCallback(MediaKeySystem *mediaKeySystem, OH_MediaKeySystem_Callback callback)
```

**Description**

Set media key system event callback.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| [OH_MediaKeySystem_Callback](capi-native-mediakeysystem-h.md#oh_mediakeysystem_callback) callback | Callback to be set to the media key system. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - If the mediaKeySystem instance is nullptr or invalid,          or the mediaKeySession is nullptr or invalid. |

### OH_MediaKeySystem_GetMediaKeySystems()

```c
Drm_ErrCode OH_MediaKeySystem_GetMediaKeySystems(DRM_MediaKeySystemDescription *descs, uint32_t *count)
```

**Description**

Acquire supported media key systems' name and uuid.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| DRM_MediaKeySystemDescription *descs | Array used to save media key systems' name and uuid. |
| uint32_t *count | Used to indicate count of struct DRM_MediaKeySystemDescription. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - Probably caused by:<br>        1.the description or the count is nullptr.<br>        2. the size of the description array is smaller than the actual number obtained.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_IsSupported()

```c
bool OH_MediaKeySystem_IsSupported(const char *name)
```

**Description**

Checks whether the device supports the specified DRM solution.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | Pointer to the DRM solution name. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Check result for the support of the DRM solution. true if supported, false otherwise. |

### OH_MediaKeySystem_IsSupported2()

```c
bool OH_MediaKeySystem_IsSupported2(const char *name, const char *mimeType)
```

**Description**

Checks whether the device supports the combination of the DRM solution and MIME type.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | Pointer to the DRM solution name. |
| const char *mimeType | Pointer to the MIME type. The supported MIME types depend on the DRM solution. Example types are video/avc and video/hev. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Check result for the support of the combination. true if supported, false otherwise. |

### OH_MediaKeySystem_IsSupported3()

```c
bool OH_MediaKeySystem_IsSupported3(const char *name, const char *mimeType, DRM_ContentProtectionLevel contentProtectionLevel)
```

**Description**

Checks whether the device supports the combination of the DRM solution, MIME type, and content protection level.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | Pointer to the DRM solution name. |
| const char *mimeType | Pointer to the MIME type. The supported MIME types depend on the DRM solution. Example types are video/avc and video/hev. |
| DRM_ContentProtectionLevel contentProtectionLevel | Content protection level. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Check result for the support of the combination. true if supported, false otherwise. |

### OH_MediaKeySystem_Create()

```c
Drm_ErrCode OH_MediaKeySystem_Create(const char *name, MediaKeySystem **mediaKeySystem)
```

**Description**

Creates a media key system instance from the name.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | Specifies which drm system will be created by name. |
| MediaKeySystem **mediaKeySystem | Media key system instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - Probably caused by:<br>        1. the name is nullptr or the length of name is zero.<br>        2. the mediaKeySystem is nullptr.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs.<br>        {@link DRM_ERR_SERVICE_DIED} 24700507 - Service died.<br>        {@link DRM_ERR_MAX_SYSTEM_NUM_REACHED} 24700510 - The maximum number of media key systems is reached. |

### OH_MediaKeySystem_SetConfigurationString()

```c
Drm_ErrCode OH_MediaKeySystem_SetConfigurationString(MediaKeySystem *mediaKeySystem, const char *configName, const char *value)
```

**Description**

Set media key system configuration value by name.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| const char *configName | Configuration name string. |
| const char *value | Configuration value string to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetConfigurationString()

```c
Drm_ErrCode OH_MediaKeySystem_GetConfigurationString(MediaKeySystem *mediaKeySystem, const char *configName, char *value, int32_t valueLen)
```

**Description**

Get media key system configuration value by name.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| const char *configName | Configuration name string. |
| char *value | Configuration value string to be get. |
| int32_t valueLen | Configuration value string len for in buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_NO_MEMORY} 24700501 - Memory errors.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_SetConfigurationByteArray()

```c
Drm_ErrCode OH_MediaKeySystem_SetConfigurationByteArray(MediaKeySystem *mediaKeySystem, const char *configName, uint8_t *value, int32_t valueLen)
```

**Description**

Set media key system configuration value by name.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| const char *configName | Configuration name string. |
| uint8_t *value | Configuration value in byte array to be set. |
| int32_t valueLen | Value array len. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_NO_MEMORY} 24700501 - Memory errors.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetConfigurationByteArray()

```c
Drm_ErrCode OH_MediaKeySystem_GetConfigurationByteArray(MediaKeySystem *mediaKeySystem, const char *configName, uint8_t *value, int32_t *valueLen)
```

**Description**

Get media key system configuration value by name.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| const char *configName | Configuration name string. |
| uint8_t *value | Configuration value in byte array to be get. |
| int32_t *valueLen | Configuration value len for in buffer and out data. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_NO_MEMORY} 24700501 - Memory errors.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetStatistics()

```c
Drm_ErrCode OH_MediaKeySystem_GetStatistics(MediaKeySystem *mediaKeySystem, DRM_Statistics *statistics)
```

**Description**

Get media key system statistics info.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| DRM_Statistics *statistics | Statistic info gotten. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_NO_MEMORY} 24700501 - Memory errors.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetMaxContentProtectionLevel()

```c
Drm_ErrCode OH_MediaKeySystem_GetMaxContentProtectionLevel(MediaKeySystem *mediaKeySystem, DRM_ContentProtectionLevel *contentProtectionLevel)
```

**Description**

Get the max content protection level media key system supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| DRM_ContentProtectionLevel *contentProtectionLevel | Content protection level. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_SetMediaKeySystemCallback()

```c
Drm_ErrCode OH_MediaKeySystem_SetMediaKeySystemCallback(MediaKeySystem *mediaKeySystem, MediaKeySystem_Callback callback)
```

**Description**

Set media key system event callback.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| [MediaKeySystem_Callback](capi-native-mediakeysystem-h.md#mediakeysystem_callback) callback | Callback to be set to the media key system. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid. |

### OH_MediaKeySystem_CreateMediaKeySession()

```c
Drm_ErrCode OH_MediaKeySystem_CreateMediaKeySession(MediaKeySystem *mediaKeySystem, DRM_ContentProtectionLevel *level, MediaKeySession **mediaKeySession)
```

**Description**

Create a media key session instance.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance which will create the media key session. |
| DRM_ContentProtectionLevel *level | Specifies the content protection level. |
| MediaKeySession **mediaKeySession | Media key session instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_NO_MEMORY} 24700501 - Memory errors.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - Probably caused by:<br>        1. The parameter passed in is a null pointer or invalid.<br>        2. the level is beyond reasonable range.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs.<br>        {@link DRM_ERR_SERVICE_DIED} 24700507 - Service died.<br>        {@link DRM_ERR_MAX_SESSION_NUM_REACHED} 24700511 - The maximum number of media key sessions is reached. |

### OH_MediaKeySystem_GenerateKeySystemRequest()

```c
Drm_ErrCode OH_MediaKeySystem_GenerateKeySystemRequest(MediaKeySystem *mediaKeySystem, uint8_t *request, int32_t *requestLen, char *defaultUrl, int32_t defaultUrlLen)
```

**Description**

Generate a media key system provision request.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| uint8_t *request | Provision request data sent to provision server. |
| int32_t *requestLen | Provision request data len for in buffer and out data. |
| char *defaultUrl | Provision server URL. |
| int32_t defaultUrlLen | Provision server URL len for in buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_NO_MEMORY} 24700501 - Memory errors.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_ProcessKeySystemResponse()

```c
Drm_ErrCode OH_MediaKeySystem_ProcessKeySystemResponse(MediaKeySystem *mediaKeySystem, uint8_t *response, int32_t responseLen)
```

**Description**

Process a media key system provision response.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| uint8_t *response | The provision response will be processed. |
| int32_t responseLen | The response len. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetOfflineMediaKeyIds()

```c
Drm_ErrCode OH_MediaKeySystem_GetOfflineMediaKeyIds(MediaKeySystem *mediaKeySystem, DRM_OfflineMediakeyIdArray *offlineMediaKeyIds)
```

**Description**

Get offline media key ids .

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| DRM_OfflineMediakeyIdArray *offlineMediaKeyIds | Media key ids of all offline media keys. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_NO_MEMORY} 24700501 - Memory errors.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetOfflineMediaKeyStatus()

```c
Drm_ErrCode OH_MediaKeySystem_GetOfflineMediaKeyStatus(MediaKeySystem *mediaKeySystem, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen, DRM_OfflineMediaKeyStatus *status)
```

**Description**

Get offline media key status.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t offlineMediaKeyIdLen | Offline media key identifier len. |
| DRM_OfflineMediaKeyStatus *status | The media key status gotten. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_ClearOfflineMediaKeys()

```c
Drm_ErrCode OH_MediaKeySystem_ClearOfflineMediaKeys(MediaKeySystem *mediaKeySystem, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen)
```

**Description**

Clear an offline media key by id.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t offlineMediaKeyIdLen | Offline media key identifier len. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetCertificateStatus()

```c
Drm_ErrCode OH_MediaKeySystem_GetCertificateStatus(MediaKeySystem *mediaKeySystem, DRM_CertificateStatus *certStatus)
```

**Description**

Get certificate status of media key system.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Media key system instance. |
| DRM_CertificateStatus *certStatus | Status will be gotten. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_Destroy()

```c
Drm_ErrCode OH_MediaKeySystem_Destroy(MediaKeySystem *mediaKeySystem)
```

**Description**

Destroy a media key system instance.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySystem *mediaKeySystem | Specifies which media key system instance will be destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | {@link DRM_ERR_OK} 0 - Success.<br>        {@link DRM_ERR_INVALID_VAL} 24700503 - The parameter passed in is a null pointer or invalid.<br>        {@link DRM_ERR_UNKNOWN} 24700506 - Internal error occurred, it is recommended to check the logs. |


