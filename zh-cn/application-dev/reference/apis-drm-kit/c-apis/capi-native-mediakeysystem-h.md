# native_mediakeysystem.h

## 概述

定义Drm MediaKeySystem API。提供以下功能：查询是否支持特定的drm、创建媒体密钥会话、获取和设置配置、获取统计信息、获取内容保护级别、生成提供请求、处理提供响应、事件监听、获取内容防护级别、管理离线媒体密钥等。

**库：** libnative_drm.z.so

**系统能力：** SystemCapability.Multimedia.Drm.Core

**起始版本：** 11

**相关模块：** [Drm](capi-drm.md)

## 汇总

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef Drm_ErrCode (\*MediaKeySystem_Callback)(DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)](#mediakeysystem_callback) | MediaKeySystem_Callback | MediaKeySystem事件触发时将调用的回调函数，不返回MediaKeySystem实例，适用于单个MediaKeySystem场景。 |
| [typedef Drm_ErrCode (\*OH_MediaKeySystem_Callback)(MediaKeySystem *mediaKeySystem, DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)](#oh_mediakeysystem_callback) | OH_MediaKeySystem_Callback | MediaKeySystem事件触发时将调用的回调函数，返回MediaKeySystem实例，适用于多个MediaKeySystem场景。 |
| [Drm_ErrCode OH_MediaKeySystem_SetCallback(MediaKeySystem *mediaKeySystem, OH_MediaKeySystem_Callback callback)](#oh_mediakeysystem_setcallback) | - | Set media key system event callback. |
| [Drm_ErrCode OH_MediaKeySystem_GetMediaKeySystems(DRM_MediaKeySystemDescription *descs, uint32_t *count)](#oh_mediakeysystem_getmediakeysystems) | - | Acquire supported media key systems' name and uuid. |
| [bool OH_MediaKeySystem_IsSupported(const char *name)](#oh_mediakeysystem_issupported) | - | 查询设备是否支持对应的DRM解决方案。 |
| [bool OH_MediaKeySystem_IsSupported2(const char *name, const char *mimeType)](#oh_mediakeysystem_issupported2) | - | 查询设备是否支持对应的DRM解决方案名称及媒体类型。可通过[OH_MediaKeySystem_IsSupported](capi-native-mediakeysystem-h.md#oh_mediakeysystem_issupported)接口先确认name参数对应的DRM解决方案是否是设备支持的。 |
| [bool OH_MediaKeySystem_IsSupported3(const char *name, const char *mimeType, DRM_ContentProtectionLevel contentProtectionLevel)](#oh_mediakeysystem_issupported3) | - | 查询设备是否支持对应的DRM解决方案、媒体类型、内容保护级别。可通过[OH_MediaKeySystem_IsSupported2](capi-native-mediakeysystem-h.md#oh_mediakeysystem_issupported2)接口先判断mimeType是否支持。 |
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

## 函数说明

### MediaKeySystem_Callback()

```c
typedef Drm_ErrCode (*MediaKeySystem_Callback)(DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)
```

**描述**

MediaKeySystem事件触发时将调用的回调函数，不返回MediaKeySystem实例，适用于单个MediaKeySystem场景。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [DRM_EventType](capi-native-drm-common-h.md#drm_eventtype) eventType | 事件类型。 |
| uint8_t \*info | 事件信息。 |
| int32_t infoLen | 事件信息长度。 |
| char \*extra | 增量信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | DRM_ERR_OK：执行成功。  DRM_ERR_INVALID_VAL：输入参数无效。 |

### OH_MediaKeySystem_Callback()

```c
typedef Drm_ErrCode (*OH_MediaKeySystem_Callback)(MediaKeySystem *mediaKeySystem, DRM_EventType eventType, uint8_t *info, int32_t infoLen, char *extra)
```

**描述**

MediaKeySystem事件触发时将调用的回调函数，返回MediaKeySystem实例，适用于多个MediaKeySystem场景。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) \*mediaKeySystem | MediaKeySystem实例。 |
| [DRM_EventType](capi-native-drm-common-h.md#drm_eventtype) eventType | 事件类型。 |
| uint8_t \*info | 事件信息。 |
| int32_t infoLen | 事件信息长度。 |
| char \*extra | 增量信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | DRM_ERR_OK：执行成功。  DRM_ERR_INVALID_VAL：输入参数无效。 |

### OH_MediaKeySystem_SetCallback()

```c
Drm_ErrCode OH_MediaKeySystem_SetCallback(MediaKeySystem *mediaKeySystem, OH_MediaKeySystem_Callback callback)
```

**描述**

Set media key system event callback.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| [OH_MediaKeySystem_Callback](capi-native-mediakeysystem-h.md#oh_mediakeysystem_callback) callback | Callback to be set to the media key system. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - If the mediaKeySystem instance is nullptr or invalid,          or the mediaKeySession is nullptr or invalid. |

### OH_MediaKeySystem_GetMediaKeySystems()

```c
Drm_ErrCode OH_MediaKeySystem_GetMediaKeySystems(DRM_MediaKeySystemDescription *descs, uint32_t *count)
```

**描述**

Acquire supported media key systems' name and uuid.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [DRM_MediaKeySystemDescription](capi-drm-drm-mediakeysystemdescription.md) *descs | Array used to save media key systems' name and uuid. |
| uint32_t *count | Used to indicate count of struct DRM_MediaKeySystemDescription. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - Probably caused by:          1.the description or the count is nullptr.          2. the size of the description array is smaller than the actual number obtained.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_IsSupported()

```c
bool OH_MediaKeySystem_IsSupported(const char *name)
```

**描述**

查询设备是否支持对应的DRM解决方案。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *name | 输入参数，DRM解决方案名称。可通过[OH_MediaKeySystem_GetMediaKeySystems](capi-native-mediakeysystem-h.md#oh_mediakeysystem_getmediakeysystems)接口获取设备支持的DRM解决方案名称。示例："com.clearplay.drm"。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回是否支持指定的DRM解决方案。true表示支持，false表示不支持。 |

### OH_MediaKeySystem_IsSupported2()

```c
bool OH_MediaKeySystem_IsSupported2(const char *name, const char *mimeType)
```

**描述**

查询设备是否支持对应的DRM解决方案名称及媒体类型。可通过[OH_MediaKeySystem_IsSupported](capi-native-mediakeysystem-h.md#oh_mediakeysystem_issupported)接口先确认name参数对应的DRM解决方案是否是设备支持的。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *name | 输入参数，DRM解决方案名称。可通过[OH_MediaKeySystem_GetMediaKeySystems](capi-native-mediakeysystem-h.md#oh_mediakeysystem_getmediakeysystems)接口获取设备支持的DRM解决方案名称。 |
| const char *mimeType | 输入参数，媒体类型，支持的媒体类型取决于DRM解决方案，如：video/avc、video/hevc。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 表示是否支持指定的DRM解决方案及媒体类型。当name和mimeType都支持时返回true，否则返回false。当name或mimeType参数为空或无效时返回false。 |

### OH_MediaKeySystem_IsSupported3()

```c
bool OH_MediaKeySystem_IsSupported3(const char *name, const char *mimeType, DRM_ContentProtectionLevel contentProtectionLevel)
```

**描述**

查询设备是否支持对应的DRM解决方案、媒体类型、内容保护级别。可通过[OH_MediaKeySystem_IsSupported2](capi-native-mediakeysystem-h.md#oh_mediakeysystem_issupported2)接口先判断mimeType是否支持。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *name | 输入参数，DRM解决方案名称。可通过[OH_MediaKeySystem_GetMediaKeySystems](capi-native-mediakeysystem-h.md#oh_mediakeysystem_getmediakeysystems)接口获取设备支持的DRM解决方案名称。 |
| const char *mimeType | 输入参数，媒体类型，支持的媒体类型取决于DRM解决方案，如：video/avc、video/hevc。 |
| [DRM_ContentProtectionLevel](capi-native-drm-common-h.md#drm_contentprotectionlevel) contentProtectionLevel | 输入参数，内容保护级别。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 表示是否支持指定的DRM解决方案、媒体类型以及内容保护级别。当name、mimeType和contentProtectionLevel都支持时返回true，否则返回false。 |

### OH_MediaKeySystem_Create()

```c
Drm_ErrCode OH_MediaKeySystem_Create(const char *name, MediaKeySystem **mediaKeySystem)
```

**描述**

Creates a media key system instance from the name.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *name | Specifies which drm system will be created by name. |
| [MediaKeySystem](capi-drm-mediakeysystem.md) **mediaKeySystem | Media key system instance. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - Probably caused by:          1. the name is nullptr or the length of name is zero.          2. the mediaKeySystem is nullptr.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs.          [DRM_ERR_SERVICE_DIED](capi-native-drm-err-h.md#drm_errcode) 24700507 - Service died.          [DRM_ERR_MAX_SYSTEM_NUM_REACHED](capi-native-drm-err-h.md#drm_errcode) 24700510 - The maximum number of media key systems is reached. |

### OH_MediaKeySystem_SetConfigurationString()

```c
Drm_ErrCode OH_MediaKeySystem_SetConfigurationString(MediaKeySystem *mediaKeySystem, const char *configName, const char *value)
```

**描述**

Set media key system configuration value by name.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| const char *configName | Configuration name string. |
| const char *value | Configuration value string to be set. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetConfigurationString()

```c
Drm_ErrCode OH_MediaKeySystem_GetConfigurationString(MediaKeySystem *mediaKeySystem, const char *configName, char *value, int32_t valueLen)
```

**描述**

Get media key system configuration value by name.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| const char *configName | Configuration name string. |
| char *value | Configuration value string to be get. |
| int32_t valueLen | Configuration value string len for in buffer. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_SetConfigurationByteArray()

```c
Drm_ErrCode OH_MediaKeySystem_SetConfigurationByteArray(MediaKeySystem *mediaKeySystem, const char *configName, uint8_t *value, int32_t valueLen)
```

**描述**

Set media key system configuration value by name.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| const char *configName | Configuration name string. |
| uint8_t *value | Configuration value in byte array to be set. |
| int32_t valueLen | Value array len. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetConfigurationByteArray()

```c
Drm_ErrCode OH_MediaKeySystem_GetConfigurationByteArray(MediaKeySystem *mediaKeySystem, const char *configName, uint8_t *value, int32_t *valueLen)
```

**描述**

Get media key system configuration value by name.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| const char *configName | Configuration name string. |
| uint8_t *value | Configuration value in byte array to be get. |
| int32_t *valueLen | Configuration value len for in buffer and out data. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetStatistics()

```c
Drm_ErrCode OH_MediaKeySystem_GetStatistics(MediaKeySystem *mediaKeySystem, DRM_Statistics *statistics)
```

**描述**

Get media key system statistics info.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| [DRM_Statistics](capi-drm-drm-statistics.md) *statistics | Statistic info gotten. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetMaxContentProtectionLevel()

```c
Drm_ErrCode OH_MediaKeySystem_GetMaxContentProtectionLevel(MediaKeySystem *mediaKeySystem, DRM_ContentProtectionLevel *contentProtectionLevel)
```

**描述**

Get the max content protection level media key system supported.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| [DRM_ContentProtectionLevel](capi-native-drm-common-h.md#drm_contentprotectionlevel) *contentProtectionLevel | Content protection level. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_SetMediaKeySystemCallback()

```c
Drm_ErrCode OH_MediaKeySystem_SetMediaKeySystemCallback(MediaKeySystem *mediaKeySystem, MediaKeySystem_Callback callback)
```

**描述**

Set media key system event callback.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| [MediaKeySystem_Callback](capi-native-mediakeysystem-h.md#mediakeysystem_callback) callback | Callback to be set to the media key system. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid. |

### OH_MediaKeySystem_CreateMediaKeySession()

```c
Drm_ErrCode OH_MediaKeySystem_CreateMediaKeySession(MediaKeySystem *mediaKeySystem, DRM_ContentProtectionLevel *level, MediaKeySession **mediaKeySession)
```

**描述**

Create a media key session instance.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance which will create the media key session. |
| [DRM_ContentProtectionLevel](capi-native-drm-common-h.md#drm_contentprotectionlevel) *level | Specifies the content protection level. |
| [MediaKeySession](capi-drm-mediakeysession.md) **mediaKeySession | Media key session instance. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - Probably caused by:          1. The parameter passed in is a null pointer or invalid.          2. the level is beyond reasonable range.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs.          [DRM_ERR_SERVICE_DIED](capi-native-drm-err-h.md#drm_errcode) 24700507 - Service died.          [DRM_ERR_MAX_SESSION_NUM_REACHED](capi-native-drm-err-h.md#drm_errcode) 24700511 - The maximum number of media key sessions is reached. |

### OH_MediaKeySystem_GenerateKeySystemRequest()

```c
Drm_ErrCode OH_MediaKeySystem_GenerateKeySystemRequest(MediaKeySystem *mediaKeySystem, uint8_t *request, int32_t *requestLen, char *defaultUrl, int32_t defaultUrlLen)
```

**描述**

Generate a media key system provision request.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| uint8_t *request | Provision request data sent to provision server. |
| int32_t *requestLen | Provision request data len for in buffer and out data. |
| char *defaultUrl | Provision server URL. |
| int32_t defaultUrlLen | Provision server URL len for in buffer. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_ProcessKeySystemResponse()

```c
Drm_ErrCode OH_MediaKeySystem_ProcessKeySystemResponse(MediaKeySystem *mediaKeySystem, uint8_t *response, int32_t responseLen)
```

**描述**

Process a media key system provision response.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| uint8_t *response | The provision response will be processed. |
| int32_t responseLen | The response len. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetOfflineMediaKeyIds()

```c
Drm_ErrCode OH_MediaKeySystem_GetOfflineMediaKeyIds(MediaKeySystem *mediaKeySystem, DRM_OfflineMediakeyIdArray *offlineMediaKeyIds)
```

**描述**

Get offline media key ids .

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| [DRM_OfflineMediakeyIdArray](capi-drm-drm-offlinemediakeyidarray.md) *offlineMediaKeyIds | Media key ids of all offline media keys. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_NO_MEMORY](capi-native-drm-err-h.md#drm_errcode) 24700501 - Memory errors.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetOfflineMediaKeyStatus()

```c
Drm_ErrCode OH_MediaKeySystem_GetOfflineMediaKeyStatus(MediaKeySystem *mediaKeySystem, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen, DRM_OfflineMediaKeyStatus *status)
```

**描述**

Get offline media key status.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t offlineMediaKeyIdLen | Offline media key identifier len. |
| [DRM_OfflineMediaKeyStatus](capi-native-drm-common-h.md#drm_offlinemediakeystatus) *status | The media key status gotten. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_ClearOfflineMediaKeys()

```c
Drm_ErrCode OH_MediaKeySystem_ClearOfflineMediaKeys(MediaKeySystem *mediaKeySystem, uint8_t *offlineMediaKeyId, int32_t offlineMediaKeyIdLen)
```

**描述**

Clear an offline media key by id.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| uint8_t *offlineMediaKeyId | Offline media key identifier. |
| int32_t offlineMediaKeyIdLen | Offline media key identifier len. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_GetCertificateStatus()

```c
Drm_ErrCode OH_MediaKeySystem_GetCertificateStatus(MediaKeySystem *mediaKeySystem, DRM_CertificateStatus *certStatus)
```

**描述**

Get certificate status of media key system.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Media key system instance. |
| [DRM_CertificateStatus](capi-native-drm-common-h.md#drm_certificatestatus) *certStatus | Status will be gotten. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |

### OH_MediaKeySystem_Destroy()

```c
Drm_ErrCode OH_MediaKeySystem_Destroy(MediaKeySystem *mediaKeySystem)
```

**描述**

Destroy a media key system instance.

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [MediaKeySystem](capi-drm-mediakeysystem.md) *mediaKeySystem | Specifies which media key system instance will be destroyed. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Drm_ErrCode](capi-native-drm-err-h.md#drm_errcode) | [DRM_ERR_OK](capi-native-drm-err-h.md#drm_errcode) 0 - Success.          [DRM_ERR_INVALID_VAL](capi-native-drm-err-h.md#drm_errcode) 24700503 - The parameter passed in is a null pointer or invalid.          [DRM_ERR_UNKNOWN](capi-native-drm-err-h.md#drm_errcode) 24700506 - Internal error occurred, it is recommended to check the logs. |


