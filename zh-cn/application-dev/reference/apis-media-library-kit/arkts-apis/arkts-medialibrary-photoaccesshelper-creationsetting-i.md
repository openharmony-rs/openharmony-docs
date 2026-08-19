# CreationSetting

保存图片或视频到媒体库时的配置项，包括保存的文件名、文件类型和其他相关参数。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-export interface CreationSetting--><!--Device-photoAccessHelper-export interface CreationSetting-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## fileNameExtension

```TypeScript
fileNameExtension: string
```

文件扩展名，例如'jpg'。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CreationSetting-fileNameExtension: string--><!--Device-CreationSetting-fileNameExtension: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoType

```TypeScript
photoType: PhotoType
```

创建的媒体文件类型[PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md)，包含IMAGE或VIDEO。

**类型：** PhotoType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CreationSetting-photoType: PhotoType--><!--Device-CreationSetting-photoType: PhotoType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## title

```TypeScript
title?: string
```

图片或者视频的标题。 不传入时由系统生成，参数规格如下： - 不应包含扩展名。 - 不允许出现的非法英文字符，包括：. \ / : * ? " ' ` &lt; &gt; | { } [ ] - 由于文件名由标题 + 扩展名组成，文件名字符串长度范围为[1, 255]，因此请注意标题长度不宜过长。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CreationSetting-title?: string--><!--Device-CreationSetting-title?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

