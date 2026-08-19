# MediaKeySystemInfo(Defines the DRM capability.)

加密媒体内容的DRM信息。

**起始版本：** 23

<!--Device-drm-interface MediaKeySystemInfo--><!--Device-drm-interface MediaKeySystemInfo-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## pssh

```TypeScript
pssh: Uint8Array
```

PSSH(protection scheme specific header) contain drm info.

**类型：** Uint8Array

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystemInfo-pssh: Uint8Array--><!--Device-MediaKeySystemInfo-pssh: Uint8Array-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

## uuid

```TypeScript
uuid: string
```

Drm system ID.

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystemInfo-uuid: string--><!--Device-MediaKeySystemInfo-uuid: string-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

