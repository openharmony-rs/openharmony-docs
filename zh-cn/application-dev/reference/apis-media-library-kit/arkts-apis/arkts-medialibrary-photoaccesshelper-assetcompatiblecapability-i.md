# AssetCompatibleCapability

资产兼容能力。

**起始版本：** 24

<!--Device-photoAccessHelper-interface AssetCompatibleCapability--><!--Device-photoAccessHelper-interface AssetCompatibleCapability-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## supportedHighResolution

```TypeScript
supportedHighResolution: boolean
```

是否支持启用高分辨率资产。true表示支持，false表示不支持。 **原子化服务API:** 从API version 24开始，该接口支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AssetCompatibleCapability-supportedHighResolution: boolean--><!--Device-AssetCompatibleCapability-supportedHighResolution: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## supportedMimeType

```TypeScript
supportedMimeType?: Array<string>
```

支持MIME types的类型。 - 配置image/heic表示应用支持heif格式。 - 配置image/jpeg表示应用仅支持jpeg格式不支持heif格式。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AssetCompatibleCapability-supportedMimeType?: Array<string>--><!--Device-AssetCompatibleCapability-supportedMimeType?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

