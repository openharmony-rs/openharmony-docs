# FileSizeFilter

可选择媒体文件大小的过滤配置。

**起始版本：** 19

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## extraFileSize

```TypeScript
extraFileSize?: number
```

针对FilterOperator.BETWEEN情况下，配置文件大小的上限值。默认值为-1。单位为字节（Byte）。

**类型：** number

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## fileSize

```TypeScript
fileSize: number
```

指定进行过滤的文件大小。单位为字节（Byte）。

**类型：** number

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## filterOperator

```TypeScript
filterOperator: FilterOperator
```

过滤操作符。例如：按照大于/小于某个fileSize的方式过滤文件。

**类型：** [FilterOperator](arkts-medialibrary-photoaccesshelper-filteroperator-e.md)

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
