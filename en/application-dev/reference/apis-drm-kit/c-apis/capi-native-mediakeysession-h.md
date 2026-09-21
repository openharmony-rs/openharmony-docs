# native_mediakeysession.h

## Overview

The file declares the MediaKeySession APIs for DRM operations. The APIs can be used to generate media key requests, process responses to media key requests, listen for events, obtain content protection levels, check media key status, and remove media keys.

**Library**: libnative_drm.so

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Related module**: [Drm](capi-drm.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [MediaKeySession_Callback](capi-drm-mediakeysession-callback.md) | MediaKeySession_Callback | The MediaKeySession_Callback struct describes the callbacks for media key session events such as key expiration and key changes. It does not provide a MediaKeySession instance, making it suitable for single-session decryption scenarios. |
| [OH_MediaKeySession_Callback](capi-drm-oh-mediakeysession-callback.md) | OH_MediaKeySession_Callback | The OH_MediaKeySession_Callback struct describes the callbacks for media key session events such as key expiration and key changes. It provides a MediaKeySession instance, making it suitable for multi-session decryption scenarios. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef Drm_ErrCode (\*MediaKeySession_EventCallback)(DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)](#mediakeysession_eventcallback) | MediaKeySession_EventCallback | Defines the callback used to listen for media key session events, for example, key expiration events. |
| [typedef Drm_ErrCode (\*MediaKeySession_KeyChangeCallback)(DRM_KeysInfo *keysInfo, bool newKeysAvailable)](#mediakeysession_keychangecallback) | MediaKeySession_KeyChangeCallback | Call back will be invoked when key changes. |
| [typedef Drm_ErrCode (\*OH_MediaKeySession_EventCallback)(MediaKeySession *mediaKeySession, DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)](#oh_mediakeysession_eventcallback) | OH_MediaKeySession_EventCallback | Defines the callback used to listen for media key session events. |
| [typedef Drm_ErrCode (\*OH_MediaKeySession_KeyChangeCallback)(MediaKeySession *mediaKeySession, DRM_KeysInfo *keysInfo, bool newKeysAvailable)](#oh_mediakeysession_keychangecallback) | OH_MediaKeySession_KeyChangeCallback | Call back will be invoked when key changes. |
| [Drm_ErrCode OH_MediaKeySession_GenerateMediaKeyRequest(MediaKeySession *mediaKeySession, DRM_MediaKeyRequestInfo *info, DRM_MediaKeyRequest *mediaKeyRequest)](#oh_mediakeysession_generatemediakeyrequest) | - | Generate media key request. |
| [Drm_ErrCode OH_MediaKeySession_ProcessMediaKeyResponse(MediaKeySession *mediaKeySession, uint8_t *response, int32_t responseLen, uint8_t *offlineMediaKeyId, int32_t *offlineMediaKeyIdLen)](#oh_mediakeysession_processmediakeyresponse) | - | Process media key response. |
| [Drm_ErrCode OH_MediaKeySession_CheckMediaKeyStatus(MediaKeySession *mediaKeySession, DRM_MediaKeyStatus *mediaKeyStatus)](#oh_mediakeysession_checkmediakeystatus) | - | Check media key status. |
| [Drm_ErrCode OH_MediaKeySession_ClearMediaKeys(MediaKeySession *mediaKeySession)](#oh_mediakeysession_clearmediakeys) | - | Clear media keys of the current session . |
| [Drm_ErrCode OH_MediaKeySession_GenerateOfflineReleaseRequest(MediaKeySession *mediaKeySession, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen, uint8_t *releaseRequest, int32_t *releaseRequestLen)](#oh_mediakeysession_generateofflinereleaserequest) | - | Generate offline media key release request. |
| [Drm_ErrCode OH_MediaKeySession_ProcessOfflineReleaseResponse(MediaKeySession *mediaKeySession, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen, uint8_t *releaseResponse, int32_t releaseResponseLen)](#oh_mediakeysession_processofflinereleaseresponse) | - | Process offline media key release response. |
| [Drm_ErrCode OH_MediaKeySession_RestoreOfflineMediaKeys(MediaKeySession *mediaKeySession, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen)](#oh_mediakeysession_restoreofflinemediakeys) | - | Restore offline media keys by ID. |
| [Drm_ErrCode OH_MediaKeySession_GetContentProtectionLevel(MediaKeySession *mediaKeySession, DRM_ContentProtectionLevel *contentProtectionLevel)](#oh_mediakeysession_getcontentprotectionlevel) | - | Get content protection level of the session. |
| [Drm_ErrCode OH_MediaKeySession_RequireSecureDecoderModule(MediaKeySession *mediaKeySession, const char *mimeType, bool *status)](#oh_mediakeysession_requiresecuredecodermodule) | - | Whether the encrypted content require a secure decoder or not. |
| [Drm_ErrCode OH_MediaKeySession_SetMediaKeySessionCallback(MediaKeySession *mediaKeySession, MediaKeySession_Callback *callback)](#oh_mediakeysession_setmediakeysessioncallback) | - | Set media key session event callback. |
| [Drm_ErrCode OH_MediaKeySession_SetCallback(MediaKeySession *mediaKeySession, OH_MediaKeySession_Callback *callback)](#oh_mediakeysession_setcallback) | - | Set media key session event callback. |
| [Drm_ErrCode OH_MediaKeySession_Destroy(MediaKeySession *mediaKeySession)](#oh_mediakeysession_destroy) | - | Release the resource before the session going to be unused. |

### Variable

| Name | Description |
| -- | -- |
| Drm_ErrCode (*MediaKeySession_EventCallback)(DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra) | Defines the callback used to listen for media key session events, for example, key expiration events.<br>**Since**: 11 |
| Drm_ErrCode (*MediaKeySession_KeyChangeCallback)(DRM_KeysInfo *keysInfo, bool newKeysAvailable) | Call back will be invoked when key changes.<br>**Since**: 11 |
| Drm_ErrCode (*OH_MediaKeySession_EventCallback)(MediaKeySession *mediaKeySession, DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra) | Defines the callback used to listen for media key session events.<br>**Since**: 12 |
| Drm_ErrCode (*OH_MediaKeySession_KeyChangeCallback)(MediaKeySession *mediaKeySession, DRM_KeysInfo *keysInfo, bool newKeysAvailable) | Call back will be invoked when key changes.<br>**Since**: 12 |

## Function description

### MediaKeySession_EventCallback()

```c
typedef Drm_ErrCode (*MediaKeySession_EventCallback)(DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)
```

**Description**

Defines the callback used to listen for media key session events, for example, key expiration events.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| DRM_EventType eventType | Event type. |
| uint8_t \*info | Pointer to the event information obtained from the media key session. |
| int32_t infoLen | Length of the event information. |
| char \*extra | Pointer to the additional information obtained from the media key session. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | Error code. |

### MediaKeySession_KeyChangeCallback()

```c
typedef Drm_ErrCode (*MediaKeySession_KeyChangeCallback)(DRM_KeysInfo *keysInfo, bool newKeysAvailable)
```

**Description**

Call back will be invoked when key changes.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| DRM_KeysInfo \*keysInfo | Key info gotten from media key system. |
| bool newKeysAvailable | Whether new keys available. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | DRM_ERR_INVALID_VAL when the params checked failure, return DRM_ERR_OK when function called successfully. |

### OH_MediaKeySession_EventCallback()

```c
typedef Drm_ErrCode (*OH_MediaKeySession_EventCallback)(MediaKeySession *mediaKeySession, DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)
```

**Description**

Defines the callback used to listen for media key session events.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession \*mediaKeySession | Pointer to the MediaKeySession instance. |
| DRM_EventType eventType | Event type. |
| uint8_t \*info | Pointer to the event information. |
| int32_t infoLen | Length of the event information. |
| char \*extra | Pointer to the additional information. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | Error code. |

### OH_MediaKeySession_KeyChangeCallback()

```c
typedef Drm_ErrCode (*OH_MediaKeySession_KeyChangeCallback)(MediaKeySession *mediaKeySession, DRM_KeysInfo *keysInfo, bool newKeysAvailable)
```

**Description**

Call back will be invoked when key changes.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession \*mediaKeySession | MediaKeySession instance. |
| DRM_KeysInfo \*keysInfo | Key info gotten from media key system. |
| bool newKeysAvailable | Whether new keys available. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | DRM_ERR_INVALID_VAL when the params checked failure, return DRM_ERR_OK when function called successfully. |

### OH_MediaKeySession_GenerateMediaKeyRequest()

```c
Drm_ErrCode OH_MediaKeySession_GenerateMediaKeyRequest(MediaKeySession *mediaKeySession, DRM_MediaKeyRequestInfo *info, DRM_MediaKeyRequest *mediaKeyRequest)
```

**Description**

Generate media key request.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |
| DRM_MediaKeyRequestInfo *info | Media key request info. |
| DRM_MediaKeyRequest *mediaKeyRequest | Media key request. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_ProcessMediaKeyResponse()

```c
Drm_ErrCode OH_MediaKeySession_ProcessMediaKeyResponse(MediaKeySession *mediaKeySession, uint8_t *response, int32_t responseLen, uint8_t *offlineMediaKeyId, int32_t *offlineMediaKeyIdLen)
```

**Description**

Process media key response.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |
| uint8_t *response | Media Key response. |
| int32_t responseLen | Media Key response len. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t *offlineMediaKeyIdLen | Offline media key identifier len for in buffer and out data. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_CheckMediaKeyStatus()

```c
Drm_ErrCode OH_MediaKeySession_CheckMediaKeyStatus(MediaKeySession *mediaKeySession, DRM_MediaKeyStatus *mediaKeyStatus)
```

**Description**

Check media key status.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |
| DRM_MediaKeyStatus *mediaKeyStatus | Media key status. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_ClearMediaKeys()

```c
Drm_ErrCode OH_MediaKeySession_ClearMediaKeys(MediaKeySession *mediaKeySession)
```

**Description**

Clear media keys of the current session .

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_GenerateOfflineReleaseRequest()

```c
Drm_ErrCode OH_MediaKeySession_GenerateOfflineReleaseRequest(MediaKeySession *mediaKeySession, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen, uint8_t *releaseRequest, int32_t *releaseRequestLen)
```

**Description**

Generate offline media key release request.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t offlineMediaKeyIdLen | Offline media key identifier len. |
| uint8_t *releaseRequest | Media Key release request. |
| int32_t *releaseRequestLen | Media Key release request len for in buffer and out data. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_ProcessOfflineReleaseResponse()

```c
Drm_ErrCode OH_MediaKeySession_ProcessOfflineReleaseResponse(MediaKeySession *mediaKeySession, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen, uint8_t *releaseResponse, int32_t releaseResponseLen)
```

**Description**

Process offline media key release response.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t offlineMediaKeyIdLen | Offline media key identifier len. |
| uint8_t *releaseResponse | Media Key response. |
| int32_t releaseResponseLen | Media Key response len. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_RestoreOfflineMediaKeys()

```c
Drm_ErrCode OH_MediaKeySession_RestoreOfflineMediaKeys(MediaKeySession *mediaKeySession, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen)
```

**Description**

Restore offline media keys by ID.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t offlineMediaKeyIdLen | Offline media key identifier len. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_GetContentProtectionLevel()

```c
Drm_ErrCode OH_MediaKeySession_GetContentProtectionLevel(MediaKeySession *mediaKeySession, DRM_ContentProtectionLevel *contentProtectionLevel)
```

**Description**

Get content protection level of the session.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |
| DRM_ContentProtectionLevel *contentProtectionLevel | Content protection level. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_RequireSecureDecoderModule()

```c
Drm_ErrCode OH_MediaKeySession_RequireSecureDecoderModule(MediaKeySession *mediaKeySession, const char *mimeType, bool *status)
```

**Description**

Whether the encrypted content require a secure decoder or not.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |
| const char *mimeType | The media type. |
| bool *status | Whether secure decoder is required. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_SetMediaKeySessionCallback()

```c
Drm_ErrCode OH_MediaKeySession_SetMediaKeySessionCallback(MediaKeySession *mediaKeySession, MediaKeySession_Callback *callback)
```

**Description**

Set media key session event callback.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |
| [MediaKeySession_Callback](capi-drm-mediakeysession-callback.md) *callback | Callback to be set to the media key session. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid. |

### OH_MediaKeySession_SetCallback()

```c
Drm_ErrCode OH_MediaKeySession_SetCallback(MediaKeySession *mediaKeySession, OH_MediaKeySession_Callback *callback)
```

**Description**

Set media key session event callback.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |
| [OH_MediaKeySession_Callback](capi-drm-oh-mediakeysession-callback.md) *callback | Callback to be set to the media key session. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid. |

### OH_MediaKeySession_Destroy()

```c
Drm_ErrCode OH_MediaKeySession_Destroy(MediaKeySession *mediaKeySession)
```

**Description**

Release the resource before the session going to be unused.

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| MediaKeySession *mediaKeySession | Media key session instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Drm_ErrCode | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |


