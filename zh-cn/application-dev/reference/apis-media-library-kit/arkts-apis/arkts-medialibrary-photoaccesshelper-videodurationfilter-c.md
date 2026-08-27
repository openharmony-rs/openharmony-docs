# VideoDurationFilter

可选择媒体文件视频时长的过滤配置。

**起始版本：** 19

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## extraVideoDuration

```TypeScript
extraVideoDuration?: number
```

针对FilterOperator.BETWEEN情况下，配置视频时长的上限值。默认值为-1。单位为毫秒（ms）。

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

## videoDuration

```TypeScript
videoDuration: number
```

指定过滤视频的时长。单位为毫秒（ms）。

**类型：** number

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
