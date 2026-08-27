# CreateOptions

图片或视频的创建选项。title参数的规格如下：  
- 不应包含扩展名。  
- 文件名字符串长度为1~255。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## subtype

```TypeScript
subtype?: PhotoSubtype
```

图片或者视频的文件子类型。

**类型：** PhotoSubtype

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## title

```TypeScript
title?: string
```

图片或者视频的标题。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
