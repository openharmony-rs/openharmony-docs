# RecentPhotoOptions

最近图片配置选项。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-export class RecentPhotoOptions--><!--Device-photoAccessHelper-export class RecentPhotoOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## MIMEType

```TypeScript
MIMEType?: photoAccessHelper.PhotoViewMIMETypes
```

最近图片控件显示的文件类型，默认为PhotoViewMIMETypes.IMAGE_VIDEO_TYPE。

**类型：** [photoAccessHelper.PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RecentPhotoOptions-MIMEType?: photoAccessHelper.PhotoViewMIMETypes--><!--Device-RecentPhotoOptions-MIMEType?: photoAccessHelper.PhotoViewMIMETypes-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## period

```TypeScript
period?: int
```

配置最近图片显示的时间范围，单位为秒（s）。配置后，系统将显示距离当前时间点指定时长内的图片。最长可配置时长为1天（86400s）。 当值小于等于0、大于86400或者未配置时，默认按最长时间段（1天）显示最近图片。当配置时间段内无符合的图片或视频时，组件不显示。

**类型：** int

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RecentPhotoOptions-period?: int--><!--Device-RecentPhotoOptions-period?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoSource

```TypeScript
photoSource?: PhotoSource
```

配置最近图片视频显示内容的来源，比如拍照、截屏等。默认不限制来源。

**类型：** [PhotoSource](arkts-medialibrary-photoaccesshelper-photosource-e.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RecentPhotoOptions-photoSource?: PhotoSource--><!--Device-RecentPhotoOptions-photoSource?: PhotoSource-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

