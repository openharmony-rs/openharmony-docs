# RecentPhotoOptions

```TypeScript
export declare class RecentPhotoOptions
```

最近图片配置选项。

**起始版本：** 12

<!--Device-unnamed-export declare class RecentPhotoOptions--><!--Device-unnamed-export declare class RecentPhotoOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { RecentPhotoComponent, RecentPhotoCheckResultCallback, RecentPhotoInfo, RecentPhotoCheckInfoCallback, RecentPhotoClickCallback, RecentPhotoOptions, PhotoSource } from '@kit.MediaLibraryKit';
```

## assetFilter

```TypeScript
assetFilter?: Array<photoAccessHelper.OperationItem>
```

媒资过滤器，如果超过限制，则只有前50项使用。**注意** 1.当应用此过滤器时，其他过滤器将失效。2.设置多个条件时，请将过滤条件用括号括起来，以避免与内部筛选项。最大长度为50。

**类型：** Array&lt;[photoAccessHelper.OperationItem](arkts-medialibrary-photoaccesshelper-operationitem-c.md)&gt;

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoOptions-assetFilter?: Array<photoAccessHelper.OperationItem>--><!--Device-RecentPhotoOptions-assetFilter?: Array<photoAccessHelper.OperationItem>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## colorMode

```TypeScript
colorMode?: PickerColorMode
```

支持应用配置占位符的颜色模式。

当isAutoRefreshSupported为true，且无符合要求的最近照片或视频时，显示占位符，colorMode字段生效。

默认为跟随系统深浅色模式。

**类型：** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoOptions-colorMode?: PickerColorMode--><!--Device-RecentPhotoOptions-colorMode?: PickerColorMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isAutoRefreshSupported

```TypeScript
isAutoRefreshSupported?: boolean
```

配置最近图片组件在符合要求的最近照片或视频发生变更（包括新增、删除、修改）时是否进行刷新。

当组件原显示的最近照片或视频被删除，而无符合要求的照片或视频时，则显示占位符（可通过colorMode配置占位符颜色模式），组件不自动退出。

默认为false，不支持自动刷新。

配置为true时显示全部符合筛选条件的照片或视频（不受period限制，仍受photoSource和MIMEType约束）。

period字段失效。

**说明：** 开启自动刷新会监听媒体库变更，建议在需要实时更新场景使用，避免频繁刷新影响性能。

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoOptions-isAutoRefreshSupported?: boolean--><!--Device-RecentPhotoOptions-isAutoRefreshSupported?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isPersistAfterClick

```TypeScript
isPersistAfterClick?: boolean
```

点击后组件是否保活。true：单击后组件不会被销毁。false：点击后组件会被销毁（默认）。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoOptions-isPersistAfterClick?: boolean--><!--Device-RecentPhotoOptions-isPersistAfterClick?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isShowBadge

```TypeScript
isShowBadge?: boolean
```

是否在显示的照片上显示徽章。true：显示徽章信息，如移动照片徽章、视频时长等。false：不显示任何徽章，只显示照片缩略图。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoOptions-isShowBadge?: boolean--><!--Device-RecentPhotoOptions-isShowBadge?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## MIMEType

```TypeScript
MIMEType?: photoAccessHelper.PhotoViewMIMETypes
```

最近图片控件显示的文件类型。可设置为IMAGE_TYPE（仅显示图片）、VIDEO_TYPE（仅显示视频）或IMAGE_VIDEO_TYPE（显示图片和视频）。默认为IMAGE_VIDEO_TYPE。

**类型：** [photoAccessHelper.PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoOptions-MIMEType?: photoAccessHelper.PhotoViewMIMETypes--><!--Device-RecentPhotoOptions-MIMEType?: photoAccessHelper.PhotoViewMIMETypes-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## period

```TypeScript
period?: number
```

配置显示多久时间段内按创建时间排序的最新一个照片或视频，单位为秒（s），取值范围(0, 86400]。最长可配置时长为1天（86400s）。

当值小于等于0、大于86400或者未设置该值时，默认显示1天内最近照片或视频。当配置时间段内无符合的照片或视频时，组件不显示。

**注意：**

当isAutoRefreshSupported为true时，period字段失效。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoOptions-period?: number--><!--Device-RecentPhotoOptions-period?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoSource

```TypeScript
photoSource?: PhotoSource
```

配置最近照片或视频显示内容的来源，比如拍照、截屏等。默认不限制来源。

**说明：** 当isAutoRefreshSupported为true时，仍受此字段约束。

**类型：** [PhotoSource](arkts-medialibrary-file-recentphotocomponent-photosource-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-RecentPhotoOptions-photoSource?: PhotoSource--><!--Device-RecentPhotoOptions-photoSource?: PhotoSource-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
