# RecentPhotoOptions

```TypeScript
export declare class RecentPhotoOptions
```

Represents the configuration of the recent image or video.

**Since:** 12

<!--Device-unnamed-export declare class RecentPhotoOptions--><!--Device-unnamed-export declare class RecentPhotoOptions-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { RecentPhotoComponent, RecentPhotoCheckResultCallback, RecentPhotoInfo, RecentPhotoCheckInfoCallback, RecentPhotoClickCallback, RecentPhotoOptions, PhotoSource } from '@kit.MediaLibraryKit';
```

## assetFilter

```TypeScript
assetFilter?: Array<photoAccessHelper.OperationItem>
```

Media asset filter, with a maximum length of 50 items. If the limit is exceeded, only the first 50 items are used. **NOTE:** 
1. When this filter is applied, other filters become invalid.
2. When setting multiple conditions, enclose the filter conditions in parentheses to prevent conflicts with
internal filter items.

**Type:** Array&lt;[photoAccessHelper.OperationItem](arkts-medialibrary-photoaccesshelper-operationitem-c.md)&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-RecentPhotoOptions-assetFilter?: Array<photoAccessHelper.OperationItem>--><!--Device-RecentPhotoOptions-assetFilter?: Array<photoAccessHelper.OperationItem>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

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

<!--Device-RecentPhotoOptions-colorMode?: PickerColorMode--><!--Device-RecentPhotoOptions-colorMode?: PickerColorMode-End-->

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

<!--Device-RecentPhotoOptions-isAutoRefreshSupported?: boolean--><!--Device-RecentPhotoOptions-isAutoRefreshSupported?: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isPersistAfterClick

```TypeScript
isPersistAfterClick?: boolean
```

Whether to keep the component alive after click. true: component will not be destroyed after click. false: component will be destroyed after click (default).

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-RecentPhotoOptions-isPersistAfterClick?: boolean--><!--Device-RecentPhotoOptions-isPersistAfterClick?: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isShowBadge

```TypeScript
isShowBadge?: boolean
```

Whether to show the badge on the displayed photo. true: show the badge info, such as moving photo badge and video duration (default). false: do not show any badge; only the photo thumbnail is displayed.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-RecentPhotoOptions-isShowBadge?: boolean--><!--Device-RecentPhotoOptions-isShowBadge?: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## MIMEType

```TypeScript
MIMEType?: photoAccessHelper.PhotoViewMIMETypes
```

Types of the file displayed. The default value is **PhotoViewMIMETypes.IMAGE_VIDEO_TYPE**.

**Type:** [photoAccessHelper.PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RecentPhotoOptions-MIMEType?: photoAccessHelper.PhotoViewMIMETypes--><!--Device-RecentPhotoOptions-MIMEType?: photoAccessHelper.PhotoViewMIMETypes-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## period

```TypeScript
period?: number
```

Time range for displaying the recent images or videos, measured in seconds. After setting, the system shows the latest image sorted by creation time taken within the specified time from the current moment. The longest duration you can set is 2147483647 (INT_MAX) seconds.

If the value is set to Number.POSITIVE_INFINITY, the system shows the latest one within the INT_MAX range. If the value is less than or equal to 0, greater than INT_MAX, or not set, the system uses 1 day by default. If there are no images or videos within the set time range, the component does not show anything.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RecentPhotoOptions-period?: number--><!--Device-RecentPhotoOptions-period?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoSource

```TypeScript
photoSource?: PhotoSource
```

Source of the recent image or video, for example, image or video taken by the camera or screenshot. By default, the source is not restricted.

**Type:** [PhotoSource](arkts-medialibrary-file-recentphotocomponent-photosource-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RecentPhotoOptions-photoSource?: PhotoSource--><!--Device-RecentPhotoOptions-photoSource?: PhotoSource-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
