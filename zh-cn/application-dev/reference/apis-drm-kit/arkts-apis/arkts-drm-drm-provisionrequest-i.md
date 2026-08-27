# ProvisionRequest

设备证书请求。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Drm.Core

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## data

```TypeScript
data: Uint8Array
```

设备证书请求数据。

**类型：** Uint8Array

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

## defaultURL

```TypeScript
defaultURL: string
```

Provision服务（设备证书请求服务）URL。需符合URL格式规范，建议使用HTTPS协议。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core
