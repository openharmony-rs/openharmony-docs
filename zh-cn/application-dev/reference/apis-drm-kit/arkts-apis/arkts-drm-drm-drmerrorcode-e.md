# DrmErrorCode

枚举，错误码。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Drm.Core

## ERROR_UNKNOWN

```TypeScript
ERROR_UNKNOWN = 24700101
```

未知错误，当发生无法归类的异常时返回。建议检查输入参数是否合法、DRM服务是否正常运行。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

## MAX_SYSTEM_NUM_REACHED

```TypeScript
MAX_SYSTEM_NUM_REACHED = 24700103
```

MediaKeySystem实例数量超过上限（64个）。请调用[destroy](arkts-drm-drm-mediakeysystem-i.md#destroy)方法销毁不需要的MediaKeySystem实例后重试。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

## MAX_SESSION_NUM_REACHED

```TypeScript
MAX_SESSION_NUM_REACHED = 24700104
```

MediaKeySession实例数量超过上限（64个）。请调用[destroy](arkts-drm-drm-mediakeysession-i.md#destroy)方法销毁不需要的MediaKeySession实例后重试。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

## SERVICE_FATAL_ERROR

```TypeScript
SERVICE_FATAL_ERROR = 24700201
```

DRM服务异常，当DRM服务发生致命错误时返回。可能原因：系统资源不足、DRM服务进程崩溃或系统异常。建议重启应用或重启设备后重试。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core
