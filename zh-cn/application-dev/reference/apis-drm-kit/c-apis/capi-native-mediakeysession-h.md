# native_mediakeysession.h

## 概述

定义Drm MediaKeySession API。提供以下功能：生成媒体密钥请求、处理媒体密钥响应、事件监听、获取内容保护级别、检查媒体密钥状态、删除媒体密钥等。

**库：** libnative_drm.z.so

**系统能力：** SystemCapability.Multimedia.Drm.Core

**起始版本：** 11

**相关模块：** [Drm](capi-drm.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [MediaKeySession_Callback](capi-drm-mediakeysession-callback.md) | MediaKeySession_Callback | MediaKeySession_Callback结构体，用于监听密钥过期、密钥更改等事件，不返回媒体密钥会话实例，适用于单媒体密钥会话解密场景。 |
| [OH_MediaKeySession_Callback](capi-drm-oh-mediakeysession-callback.md) | OH_MediaKeySession_Callback | OH_MediaKeySession_Callback结构体，用于监听密钥过期、密钥更改等事件，返回媒体密钥会话实例，适用于多个媒体密钥会话的解密场景。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef Drm_ErrCode (\*MediaKeySession_EventCallback)(DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)](#mediakeysession_eventcallback) | MediaKeySession_EventCallback | MediaKeySession事件触发时将调用的回调函数，如密钥过期事件。 |
| [typedef Drm_ErrCode (\*MediaKeySession_KeyChangeCallback)(DRM_KeysInfo *keysInfo, bool newKeysAvailable)](#mediakeysession_keychangecallback) | MediaKeySession_KeyChangeCallback | 密钥变更时将调用回调。 |
| [typedef Drm_ErrCode (\*OH_MediaKeySession_EventCallback)(MediaKeySession *mediaKeySession, DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)](#oh_mediakeysession_eventcallback) | OH_MediaKeySession_EventCallback | 事件触发时将调用的回调函数。事件信息来源于媒体播放过程中的DRM事件，通过MediaKeySession实例触发。 |
| [typedef Drm_ErrCode (\*OH_MediaKeySession_KeyChangeCallback)(MediaKeySession *mediaKeySession, DRM_KeysInfo *keysInfo, bool newKeysAvailable)](#oh_mediakeysession_keychangecallback) | OH_MediaKeySession_KeyChangeCallback | 密钥变更时将调用的回调。 |
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

## 函数说明

### MediaKeySession_EventCallback()

```c
typedef Drm_ErrCode (*MediaKeySession_EventCallback)(DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)
```

**描述**

MediaKeySession事件触发时将调用的回调函数，如密钥过期事件。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [DRM_EventType](capi-native-drm-common-h.md#drm_eventtype) eventType | 输入参数，事件类型。 |
| uint8_t \*info | 输出参数，从媒体密钥会话获取的事件信息。 |
| int32_t infoLen | 输出参数，事件信息长度。 |
| char \*extra | 输出参数，从媒体密钥会话中获得的额外信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | 错误码。 |

### MediaKeySession_KeyChangeCallback()

```c
typedef Drm_ErrCode (*MediaKeySession_KeyChangeCallback)(DRM_KeysInfo *keysInfo, bool newKeysAvailable)
```

**描述**

密钥变更时将调用回调。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [DRM_KeysInfo](capi-drm-drm-keysinfo.md) \*keysInfo | 密钥信息。 |
| bool newKeysAvailable | 新密钥是否可用，true表示可用，false表示不可用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | DRM_ERR_OK：执行成功。  DRM_ERR_INVALID_VAL：参数检查失败。 |

### OH_MediaKeySession_EventCallback()

```c
typedef Drm_ErrCode (*OH_MediaKeySession_EventCallback)(MediaKeySession *mediaKeySession, DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)
```

**描述**

事件触发时将调用的回调函数。事件信息来源于媒体播放过程中的DRM事件，通过MediaKeySession实例触发。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) \*mediaKeySession | 输入参数，会话实例，用于标识事件来源。 |
| [DRM_EventType](capi-native-drm-common-h.md#drm_eventtype) eventType | 输入参数，事件类型。 |
| uint8_t \*info | 输出参数，事件信息，来源于DRM事件。 |
| int32_t infoLen | 输出参数，事件信息长度。 |
| char \*extra | 输出参数，增量信息，来源于DRM事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | 错误码。 |

### OH_MediaKeySession_KeyChangeCallback()

```c
typedef Drm_ErrCode (*OH_MediaKeySession_KeyChangeCallback)(MediaKeySession *mediaKeySession, DRM_KeysInfo *keysInfo, bool newKeysAvailable)
```

**描述**

密钥变更时将调用的回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) \*mediaKeySession | 媒体密钥会话实例。 |
| [DRM_KeysInfo](capi-drm-drm-keysinfo.md) \*keysInfo | 密钥信息。 |
| bool newKeysAvailable | 新密钥是否可用，true表示可用，false表示不可用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | DRM_ERR_OK：执行成功。  DRM_ERR_INVALID_VAL：参数检查失败。 |

### OH_MediaKeySession_GenerateMediaKeyRequest()

```c
Drm_ErrCode OH_MediaKeySession_GenerateMediaKeyRequest(MediaKeySession *mediaKeySession, DRM_MediaKeyRequestInfo *info, DRM_MediaKeyRequest *mediaKeyRequest)
```

**描述**

Generate media key request.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |
| [DRM_MediaKeyRequestInfo](capi-drm-drm-mediakeyrequestinfo.md) *info | Media key request info. |
| [DRM_MediaKeyRequest](capi-drm-drm-mediakeyrequest.md) *mediaKeyRequest | Media key request. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_ProcessMediaKeyResponse()

```c
Drm_ErrCode OH_MediaKeySession_ProcessMediaKeyResponse(MediaKeySession *mediaKeySession, uint8_t *response, int32_t responseLen, uint8_t *offlineMediaKeyId, int32_t *offlineMediaKeyIdLen)
```

**描述**

Process media key response.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |
| uint8_t *response | Media Key response. |
| int32_t responseLen | Media Key response len. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t *offlineMediaKeyIdLen | Offline media key identifier len for in buffer and out data. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_CheckMediaKeyStatus()

```c
Drm_ErrCode OH_MediaKeySession_CheckMediaKeyStatus(MediaKeySession *mediaKeySession, DRM_MediaKeyStatus *mediaKeyStatus)
```

**描述**

Check media key status.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |
| [DRM_MediaKeyStatus](capi-drm-drm-mediakeystatus.md) *mediaKeyStatus | Media key status. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_ClearMediaKeys()

```c
Drm_ErrCode OH_MediaKeySession_ClearMediaKeys(MediaKeySession *mediaKeySession)
```

**描述**

Clear media keys of the current session .

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_GenerateOfflineReleaseRequest()

```c
Drm_ErrCode OH_MediaKeySession_GenerateOfflineReleaseRequest(MediaKeySession *mediaKeySession, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen, uint8_t *releaseRequest, int32_t *releaseRequestLen)
```

**描述**

Generate offline media key release request.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t offlineMediaKeyIdLen | Offline media key identifier len. |
| uint8_t *releaseRequest | Media Key release request. |
| int32_t *releaseRequestLen | Media Key release request len for in buffer and out data. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_ProcessOfflineReleaseResponse()

```c
Drm_ErrCode OH_MediaKeySession_ProcessOfflineReleaseResponse(MediaKeySession *mediaKeySession, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen, uint8_t *releaseResponse, int32_t releaseResponseLen)
```

**描述**

Process offline media key release response.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t offlineMediaKeyIdLen | Offline media key identifier len. |
| uint8_t *releaseResponse | Media Key response. |
| int32_t releaseResponseLen | Media Key response len. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_RestoreOfflineMediaKeys()

```c
Drm_ErrCode OH_MediaKeySession_RestoreOfflineMediaKeys(MediaKeySession *mediaKeySession, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen)
```

**描述**

Restore offline media keys by ID.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t offlineMediaKeyIdLen | Offline media key identifier len. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_GetContentProtectionLevel()

```c
Drm_ErrCode OH_MediaKeySession_GetContentProtectionLevel(MediaKeySession *mediaKeySession, DRM_ContentProtectionLevel *contentProtectionLevel)
```

**描述**

Get content protection level of the session.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |
| [DRM_ContentProtectionLevel](capi-native-drm-common-h.md#drm_contentprotectionlevel) *contentProtectionLevel | Content protection level. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_RequireSecureDecoderModule()

```c
Drm_ErrCode OH_MediaKeySession_RequireSecureDecoderModule(MediaKeySession *mediaKeySession, const char *mimeType, bool *status)
```

**描述**

Whether the encrypted content require a secure decoder or not.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |
| const char *mimeType | The media type. |
| bool *status | Whether secure decoder is required. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySession_SetMediaKeySessionCallback()

```c
Drm_ErrCode OH_MediaKeySession_SetMediaKeySessionCallback(MediaKeySession *mediaKeySession, MediaKeySession_Callback *callback)
```

**描述**

Set media key session event callback.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |
| [MediaKeySession_Callback](capi-drm-mediakeysession-callback.md) *callback | Callback to be set to the media key session. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid. |

### OH_MediaKeySession_SetCallback()

```c
Drm_ErrCode OH_MediaKeySession_SetCallback(MediaKeySession *mediaKeySession, OH_MediaKeySession_Callback *callback)
```

**描述**

Set media key session event callback.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |
| [OH_MediaKeySession_Callback](capi-drm-oh-mediakeysession-callback.md) *callback | Callback to be set to the media key session. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid. |

### OH_MediaKeySession_Destroy()

```c
Drm_ErrCode OH_MediaKeySession_Destroy(MediaKeySession *mediaKeySession)
```

**描述**

Release the resource before the session going to be unused.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySession](capi-drm-mediakeysession.md) *mediaKeySession | Media key session instance. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |


