# RecentPhotoInfo

```TypeScript
export declare class RecentPhotoInfo
```

最近图片相关信息。

**起始版本：** 13

<!--Device-unnamed-export declare class RecentPhotoInfo--><!--Device-unnamed-export declare class RecentPhotoInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { RecentPhotoComponent, RecentPhotoCheckResultCallback, RecentPhotoInfo, RecentPhotoCheckInfoCallback, RecentPhotoClickCallback, RecentPhotoOptions, PhotoSource } from '@kit.MediaLibraryKit';
```

## dateTaken

```TypeScript
dateTaken?: number
```

最近照片/视频的拍摄时间，单位为毫秒（ms）。（距1970年1月1日的毫秒数值）。

**类型：** number

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoInfo-dateTaken?: number--><!--Device-RecentPhotoInfo-dateTaken?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## identifier

```TypeScript
identifier?: string
```

最近照片/视频的名称hash值，用于辅助应用区分最新图片组件将要显示的图片/视频与之前曾显示过的图片/视频是否为同一个。

**类型：** string

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoInfo-identifier?: string--><!--Device-RecentPhotoInfo-identifier?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
