# DRM_MediaKeySystemDescription

```c
typedef struct DRM_MediaKeySystemDescription {...} DRM_MediaKeySystemDescription
```

## 概述

DRM解决方案名称及其UUID的列表。

**起始版本：** 12

**相关模块：** [Drm](capi-drm.md)

**所在头文件：** [native_drm_common.h](capi-native-drm-common-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char name[MAX_MEDIA_KEY_SYSTEM_NAME_LEN] | Name of DRM plugin. |
| uint8_t uuid[DRM_UUID_LEN] | uuid. |


