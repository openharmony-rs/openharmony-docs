# MediaKeySystemInfo

加密媒体内容的DRM信息。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Drm.Core

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## pssh

```TypeScript
pssh: Uint8Array
```

DRM内容保护系统专用头，包含DRM相关的元数据和初始化数据的字节数组。具体结构由DRM方案定义。

**类型：** Uint8Array

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

## uuid

```TypeScript
uuid: string
```

DRM内容保护系统的唯一标识，必须为有效的UUID格式。传入无效UUID时，接口返回失败。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core
