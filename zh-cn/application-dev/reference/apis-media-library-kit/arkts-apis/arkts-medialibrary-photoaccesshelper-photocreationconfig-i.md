# PhotoCreationConfig

保存图片/视频到媒体库的配置，包括保存的文件名等。

**起始版本：** 23

<!--Device-photoAccessHelper-interface PhotoCreationConfig--><!--Device-photoAccessHelper-interface PhotoCreationConfig-End-->

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

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoCreationConfig-fileNameExtension: string--><!--Device-PhotoCreationConfig-fileNameExtension: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoType

```TypeScript
photoType: PhotoType
```

创建的文件类型[PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md)，IMAGE或者VIDEO。

**类型：** PhotoType

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoCreationConfig-photoType: PhotoType--><!--Device-PhotoCreationConfig-photoType: PhotoType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## subtype

```TypeScript
subtype?: PhotoSubtype
```

图片或者视频的文件子类型[PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e.md)，不传入时默认为DEFAULT。

**类型：** PhotoSubtype

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoCreationConfig-subtype?: PhotoSubtype--><!--Device-PhotoCreationConfig-subtype?: PhotoSubtype-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## title

```TypeScript
title?: string
```

图片或者视频的标题，不传入时由系统生成。参数规格为： - 不应包含扩展名。 - 文件名字符串长度为1~255（资产文件名为标题+扩展名）。 - 不允许出现的非法英文字符，包括：. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoCreationConfig-title?: string--><!--Device-PhotoCreationConfig-title?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

