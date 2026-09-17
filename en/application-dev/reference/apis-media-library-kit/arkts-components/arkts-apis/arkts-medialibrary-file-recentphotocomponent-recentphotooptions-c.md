# RecentPhotoOptions

Represents the configuration of the recent image or video.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { RecentPhotoComponent, RecentPhotoCheckResultCallback, RecentPhotoInfo, RecentPhotoCheckInfoCallback, RecentPhotoClickCallback, RecentPhotoOptions, PhotoSource } from '@kit.MediaLibraryKit';
```

## colorMode

```TypeScript
colorMode?: PickerColorMode
```

Color mode of the placeholder.

This setting is used when **isAutoRefreshSupported** is set to **true** and no recent image or video meets the requirements, showing a placeholder instead.

By default, it follows the system's dark/light color mode.

**Type:** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isAutoRefreshSupported

```TypeScript
isAutoRefreshSupported?: boolean
```

Whether the **RecentPhotoComponent** automatically refreshes when there are changes (including additions, deletions, or modifications) to the recent images or videos that meet the requirements.

If the component's originally displayed image or video is deleted and there are no other images or videos that meet the requirements, a placeholder is displayed and the component does not automatically close.

The default value is **false**, indicating that the component does not automatically refresh. If this parameter is set to **true**, all images are displayed, and the **period** parameter is invalid.

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## MIMEType

```TypeScript
MIMEType?: photoAccessHelper.PhotoViewMIMETypes
```

Types of the file displayed. The default value is **PhotoViewMIMETypes.IMAGE_VIDEO_TYPE**.

**Type:** [photoAccessHelper.PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## period

```TypeScript
period?: number
```

Time period for displaying the latest image sorted by creation time, in seconds. The longest duration you can set is 1 day (86400s).

If the value is less than or equal to 0, greater than 86400, or not set, the most recent photos over the longest period of up to one day is displayed by default. If there is no image or video in the specified period, the component is not displayed.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoSource

```TypeScript
photoSource?: PhotoSource
```

Source of the recent image or video, for example, image or video taken by the camera or screenshot. By default, the source is not restricted.

**Type:** [PhotoSource](arkts-medialibrary-file-recentphotocomponent-photosource-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
