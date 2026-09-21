# BaseItemInfo

```TypeScript
export declare class BaseItemInfo
```

Represents basic image and video information.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## duration

```TypeScript
duration?: number
```

Video duration, in milliseconds. In versions earlier than API version 23, the value of **duration** is **0** for moving photos. In API version 23 and later versions, the value of **duration** is the duration of the video clip attached to moving photos. If an exception occurs, **-1** is returned.

This parameter is supported only when [ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md) is set to **THUMBNAIL**. Otherwise, it is left empty.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## dynamicRangeType

```TypeScript
dynamicRangeType?: photoAccessHelper.DynamicRangeType
```

Dynamic range type of the media file. The options are **HDR** and **SDR**.

For moving photos, this parameter specifies the dynamic range type of the cover image.

**Type:** [photoAccessHelper.DynamicRangeType](arkts-medialibrary-photoaccesshelper-dynamicrangetype-e.md)

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## height

```TypeScript
height?: number
```

Height of the image or video, in px.

This parameter is supported only when [ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md) is set to **THUMBNAIL**. Otherwise, it is left empty.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mimeType

```TypeScript
mimeType?: string
```

MIME type of the image or video.

This parameter is supported only when [ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md) is set to **THUMBNAIL**. Otherwise, it is left empty.

You can determine the media type based on the prefix of the **mimeType** string. If the string starts with "image/", it indicates an image. If the string starts with "video/", it indicates a video. For details, see [Identifying Asset Types Using the mimeType Field](../../../media/medialibrary/medialibrary-faqs/medialibrary-asset-judgment-faq.md#identifying-asset-types-using-the-mimetype-field).

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## movingPhotoBadgeState

```TypeScript
movingPhotoBadgeState?: photoAccessHelper.MovingPhotoBadgeStateType
```

State of the moving photo badge.

This parameter is supported only when [ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md) is set to **THUMBNAIL**. Otherwise, it is left empty.

**Type:** [photoAccessHelper.MovingPhotoBadgeStateType](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## orientation

```TypeScript
orientation?: number
```

Image or video direction information.

1: **TOP-left**: The image is not rotated.

2: **TOP-right**: The image is flipped horizontally.

3: **Bottom-right**: The image is rotated by 180°.

4: **Bottom-left**: The image is flipped vertically.

5: **Left-top**: The image is flipped horizontally and then rotated clockwise by 270°.

6: **Right-top**: The image is rotated clockwise by 90°.

7: **Right-bottom**: The image is vertically flipped and then rotated clockwise by 90°.

8: **Left-bottom**: The image is rotated clockwise by 270°.

Images with mirroring information retain their original width and height attributes regardless of rotation, whereas images without such information have these attributes updated to reflect the post-rotation dimensions.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoSubType

```TypeScript
photoSubType?: photoAccessHelper.PhotoSubtype
```

Subtype of the photo. The options are **DEFAULT**, **MOVING_PHOTO**, and **BURST**.

The default value is **DEFAULT (0)**.

**Type:** [photoAccessHelper.PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e.md)

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## size

```TypeScript
size?: number
```

Size of the image or video, in bytes.

This parameter is supported only when [ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md) is set to **THUMBNAIL**. Otherwise, it is left empty.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uri

```TypeScript
uri?: string
```

URI of the image or video.

This parameter is supported only when [ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md) is set to **THUMBNAIL**. Otherwise, it is left empty.

**NOTE:** 

If the resource is a burst shot photo, only the cover image of the burst shot photo group is returned.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## videoMode

```TypeScript
videoMode?: photoAccessHelper.VideoMode
```

Log mode of a video file.

**Type:** [photoAccessHelper.VideoMode](arkts-medialibrary-photoaccesshelper-videomode-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## width

```TypeScript
width?: number
```

Width of the image or video, in px.

This parameter is supported only when [ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md) is set to **THUMBNAIL**. Otherwise, it is left empty.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
