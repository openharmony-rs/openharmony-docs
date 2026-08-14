# DRM_MediaKeyRequest

```c
typedef struct DRM_MediaKeyRequest {...} DRM_MediaKeyRequest
```

## 概述

媒体密钥请求。

**起始版本：** 11

**相关模块：** [Drm](capi-drm.md)

**所在头文件：** [native_drm_common.h](capi-native-drm-common-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [DRM_MediaKeyRequestType](capi-native-drm-common-h.md#drm_mediakeyrequesttype) type | 媒体密钥请求类型。 |
| int32_t dataLen | 媒体密钥请求数据长度。 |
| uint8_t data[MAX_MEDIA_KEY_REQUEST_DATA_LEN] | Media key request data sent to media key server. |
| char defaultUrl[MAX_DEFAULT_URL_LEN] | Media key server URL. |


