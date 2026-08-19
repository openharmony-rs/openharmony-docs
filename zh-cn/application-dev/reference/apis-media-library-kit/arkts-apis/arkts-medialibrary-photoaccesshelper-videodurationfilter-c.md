# VideoDurationFilter

可选择媒体文件视频时长的过滤配置。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-class VideoDurationFilter--><!--Device-photoAccessHelper-class VideoDurationFilter-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## extraVideoDuration

```TypeScript
extraVideoDuration?: int
```

针对FilterOperator.BETWEEN情况下，配置视频时长的上限值。默认值为-1。 单位为毫秒（ms）。

**类型：** int

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoDurationFilter-extraVideoDuration?: int--><!--Device-VideoDurationFilter-extraVideoDuration?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## filterOperator

```TypeScript
filterOperator: FilterOperator
```

过滤操作符。 例如：按照大于/小于某个fileSize的方式过滤文件。

**类型：** [FilterOperator](arkts-medialibrary-photoaccesshelper-filteroperator-e.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoDurationFilter-filterOperator: FilterOperator--><!--Device-VideoDurationFilter-filterOperator: FilterOperator-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## videoDuration

```TypeScript
videoDuration: int
```

指定过滤视频的时长。 单位为毫秒（ms）。

**类型：** int

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoDurationFilter-videoDuration: int--><!--Device-VideoDurationFilter-videoDuration: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

