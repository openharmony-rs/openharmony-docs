# RecentPhotoInfo

最近图片相关信息。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-export class RecentPhotoInfo--><!--Device-photoAccessHelper-export class RecentPhotoInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## dateTaken

```TypeScript
dateTaken?: long
```

最近图片/视频的拍摄时间（距1970年1月1日的毫秒数值），单位为毫秒（ms）。

**类型：** long

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RecentPhotoInfo-dateTaken?: long--><!--Device-RecentPhotoInfo-dateTaken?: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## identifier

```TypeScript
identifier?: string
```

最近图片/视频的名称hash值，用于辅助应用区分最新图片组件将要显示的图片/视频与之前曾显示过的图片/视频是否为同一个。

**类型：** string

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RecentPhotoInfo-identifier?: string--><!--Device-RecentPhotoInfo-identifier?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

