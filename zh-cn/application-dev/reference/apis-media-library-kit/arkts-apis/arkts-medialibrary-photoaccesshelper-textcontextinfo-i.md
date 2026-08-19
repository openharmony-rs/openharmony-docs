# TextContextInfo

文本信息，用于推荐图片的文本信息。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-interface TextContextInfo--><!--Device-photoAccessHelper-interface TextContextInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## text

```TypeScript
text?: string
```

如果需要根据文本（支持250字以内的简体中文）推荐相应的图片，则配置此参数。text默认是空字符串。

**类型：** string

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextContextInfo-text?: string--><!--Device-TextContextInfo-text?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

