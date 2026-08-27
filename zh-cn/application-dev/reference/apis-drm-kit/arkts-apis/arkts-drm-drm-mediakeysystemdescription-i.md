# MediaKeySystemDescription

插件信息。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Drm.Core

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## name

```TypeScript
name: string
```

插件名称，用于标识DRM插件的名称字符串。通常由DRM方案提供商定义。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

## uuid

```TypeScript
uuid: string
```

插件唯一标识码，必须为有效的UUID格式。传入无效UUID时，接口返回失败。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core
