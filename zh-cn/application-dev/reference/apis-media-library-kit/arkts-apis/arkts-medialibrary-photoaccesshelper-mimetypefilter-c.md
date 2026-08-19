# MimeTypeFilter

文件类型的过滤配置。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-class MimeTypeFilter--><!--Device-photoAccessHelper-class MimeTypeFilter-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## mimeTypeArray

```TypeScript
mimeTypeArray: Array<string>
```

PhotoPicker可供用户选择媒体文件的过滤类型。数组长度最大为10，因此支持最多十种指定类型。 过滤类型参考MIME类型定义，例如：“image/jpeg”、“video/mp4”等。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MimeTypeFilter-mimeTypeArray: Array<string>--><!--Device-MimeTypeFilter-mimeTypeArray: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

