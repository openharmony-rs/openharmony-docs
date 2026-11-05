# RecentPhotoComponent

```TypeScript
export declare struct RecentPhotoComponent
```

RecentPhotoComponent({ recentPhotoOptions?: RecentPhotoOptions, onRecentPhotoCheckResult?: RecentPhotoCheckResultCallback, onRecentPhotoClick: RecentPhotoClickCallback, onRecentPhotoCheckInfo?: RecentPhotoCheckInfoCallback, })

应用可以在布局中嵌入最近图片组件，用于访问按创建时间排序的公共目录下最新的一个照片或视频文件。应用无需申请媒体访问权限，即可根据配置项访问。

**起始版本：** 12

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct RecentPhotoComponent--><!--Device-unnamed-export declare struct RecentPhotoComponent-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { RecentPhotoComponent, RecentPhotoCheckResultCallback, RecentPhotoInfo, RecentPhotoCheckInfoCallback, RecentPhotoClickCallback, RecentPhotoOptions, PhotoSource } from '@kit.MediaLibraryKit';
```

## onRecentPhotoCheckInfo

```TypeScript
onRecentPhotoCheckInfo?: RecentPhotoCheckInfoCallback
```

最近图片查询结果回调函数，并且返回该照片的相关信息。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoComponent-onRecentPhotoCheckInfo?: RecentPhotoCheckInfoCallback--><!--Device-RecentPhotoComponent-onRecentPhotoCheckInfo?: RecentPhotoCheckInfoCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onRecentPhotoCheckResult

```TypeScript
onRecentPhotoCheckResult?: RecentPhotoCheckResultCallback
```

最近图片查询结果回调函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoComponent-onRecentPhotoCheckResult?: RecentPhotoCheckResultCallback--><!--Device-RecentPhotoComponent-onRecentPhotoCheckResult?: RecentPhotoCheckResultCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onRecentPhotoClick

```TypeScript
onRecentPhotoClick: RecentPhotoClickCallback
```

选择最近图片回调函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoComponent-onRecentPhotoClick: RecentPhotoClickCallback--><!--Device-RecentPhotoComponent-onRecentPhotoClick: RecentPhotoClickCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onError

```TypeScript
onError?: ErrorCallback
```

当最近的图片组件发生错误时的回调。

**类型：** [ErrorCallback](arkts-medialibrary-errorcallback-t.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoComponent-onError?: ErrorCallback--><!--Device-RecentPhotoComponent-onError?: ErrorCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## recentPhotoOptions

```TypeScript
recentPhotoOptions?: RecentPhotoOptions
```

最近图片配置参数信息。

**类型：** [RecentPhotoOptions](arkts-medialibrary-file-recentphotocomponent-recentphotooptions-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoComponent-recentPhotoOptions?: RecentPhotoOptions--><!--Device-RecentPhotoComponent-recentPhotoOptions?: RecentPhotoOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
