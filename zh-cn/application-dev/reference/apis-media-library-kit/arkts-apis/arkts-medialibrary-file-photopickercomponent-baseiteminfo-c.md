# BaseItemInfo

```TypeScript
export declare class BaseItemInfo
```

图片、视频相关信息。

**起始版本：** 12

<!--Device-unnamed-export declare class BaseItemInfo--><!--Device-unnamed-export declare class BaseItemInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## duration

```TypeScript
duration?: number
```

视频的持续时间，单位为毫秒（ms）。在API version 23之前，动态照片的duration将返回0；在API version 23及之后，返回动态照片附带视频片段的时长，异常场景返回-1。

当[ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md)为THUMBNAIL时支持，否则为空。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-BaseItemInfo-duration?: number--><!--Device-BaseItemInfo-duration?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## dynamicRangeType

```TypeScript
dynamicRangeType?: photoAccessHelper.DynamicRangeType
```

媒体文件动态范围模型，包括HDR和SDR。

对于movingPhoto专指封面图片的动态范围类型。

**类型：** [photoAccessHelper.DynamicRangeType](arkts-medialibrary-photoaccesshelper-dynamicrangetype-e.md)

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-BaseItemInfo-dynamicRangeType?: photoAccessHelper.DynamicRangeType--><!--Device-BaseItemInfo-dynamicRangeType?: photoAccessHelper.DynamicRangeType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## height

```TypeScript
height?: number
```

图片、视频的高，单位为像素（px）。

当[ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md)为THUMBNAIL时支持，否则为空。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-BaseItemInfo-height?: number--><!--Device-BaseItemInfo-height?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mimeType

```TypeScript
mimeType?: string
```

图片、视频的mimeType。

当[ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md)为THUMBNAIL时支持，否则为空。

开发者可以通过mimeType的字符串前缀判断媒体类型：以'image/'开头表示图片，以'video/'开头表示视频。具体判断方式请参考[使用mimeType字段来判断资源类型](../../../media/medialibrary/medialibrary-faqs/medialibrary-asset-judgment-faq.md#使用mimetype字段来判断资源类型)。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-BaseItemInfo-mimeType?: string--><!--Device-BaseItemInfo-mimeType?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## movingPhotoBadgeState

```TypeScript
movingPhotoBadgeState?: photoAccessHelper.MovingPhotoBadgeStateType
```

动态照片的状态。

当[ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md)为THUMBNAIL时支持，否则为空。

**类型：** [photoAccessHelper.MovingPhotoBadgeStateType](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-BaseItemInfo-movingPhotoBadgeState?: photoAccessHelper.MovingPhotoBadgeStateType--><!--Device-BaseItemInfo-movingPhotoBadgeState?: photoAccessHelper.MovingPhotoBadgeStateType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## orientation

```TypeScript
orientation?: number
```

图片/视频方向信息。

1.“TOP-left”，图像未旋转。

2.“TOP-right”，镜像水平翻转。

3.“Bottom-right”，图像旋转180°。

4.“Bottom-left”，镜像垂直翻转。

5.“Left-top”，先镜像水平翻转，再顺时针旋转270°。

6.“Right-top”，顺时针旋转90°。

7.“Right-bottom”，先镜像水平翻转，再顺时针旋转90°。

8.“Left-bottom”，顺时针旋转270°。

携带镜像信息的图片无论旋转与否其宽高属性都与原图保持一致，无镜像信息的图片其宽高属性会更新为旋转后的结果。

**类型：** number

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-BaseItemInfo-orientation?: number--><!--Device-BaseItemInfo-orientation?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoSubType

```TypeScript
photoSubType?: photoAccessHelper.PhotoSubtype
```

图片类型，包括DEFAULT、MOVING_PHOTO和BURST。

非特殊类型图片默认为DEFAULT（0）。

**类型：** [photoAccessHelper.PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e.md)

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-BaseItemInfo-photoSubType?: photoAccessHelper.PhotoSubtype--><!--Device-BaseItemInfo-photoSubType?: photoAccessHelper.PhotoSubtype-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## size

```TypeScript
size?: number
```

图片、视频的大小，单位为字节（Byte）。

当[ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md)为THUMBNAIL时支持，否则为空。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-BaseItemInfo-size?: number--><!--Device-BaseItemInfo-size?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uri

```TypeScript
uri?: string
```

图片、视频的URI。

当[ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md)为THUMBNAIL时支持，否则为空。

**注意：**

当资源为连拍照片类型时，仅返回该连拍组的封面资源。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-BaseItemInfo-uri?: string--><!--Device-BaseItemInfo-uri?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## videoMode

```TypeScript
videoMode?: photoAccessHelper.VideoMode
```

视频文件的log模式。

**类型：** [photoAccessHelper.VideoMode](arkts-medialibrary-photoaccesshelper-videomode-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-BaseItemInfo-videoMode?: photoAccessHelper.VideoMode--><!--Device-BaseItemInfo-videoMode?: photoAccessHelper.VideoMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## width

```TypeScript
width?: number
```

图片、视频的宽，单位为像素（px）。

当[ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md)为THUMBNAIL时支持，否则为空。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-BaseItemInfo-width?: number--><!--Device-BaseItemInfo-width?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
