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

This setting is used when **isAutoRefreshSupported** is set to **true** and no recent photo or video meets the requirements, showing a placeholder instead. The **colorMode** field takes effect.

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

Whether the **RecentPhotoComponent** automatically refreshes when there are changes (including additions, deletions, or modifications) to the recent photos or videos that meet the requirements.

If the component's originally displayed photo or video is deleted and there are no other photos or videos that meet the requirements, a placeholder is displayed and the component does not automatically close. The placeholder color mode can be configured using **colorMode**.

The default value is **false**, indicating that automatic refresh is not supported.

If this parameter is set to **true**, all photos or videos that meet the filter criteria are displayed. This parameters is still specified by **photoSource** and **MIMEType**, but not by **period**.

The **period** field becomes invalid.

**Note:** If automatic refresh is enabled, media library changes are listened for. It is recommended that this function be used in scenarios where real-time updates are required to avoid frequent refreshes that may affect performance.

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

Types of the file displayed. The options include **IMAGE_TYPE** (only images are displayed), **VIDEO_TYPE** (only videos are displayed), and **IMAGE_VIDEO_TYPE** (both images and videos are displayed). The default value is **IMAGE_VIDEO_TYPE**.

**Type:** [photoAccessHelper.PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RecentPhotoOptions-MIMEType?: photoAccessHelper.PhotoViewMIMETypes--><!--Device-RecentPhotoOptions-MIMEType?: photoAccessHelper.PhotoViewMIMETypes-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## period

```TypeScript
period?: number
```

Time period for displaying the latest photo or video sorted by creation time, in seconds. The value range is (0, 86400]. The longest duration you can set is 1 day (86400s).

If the value is less than or equal to 0, greater than 86400, or not set, the latest photos or videos within one day are displayed by default. If there is no photo or video in the specified period, the component is not displayed.

**Note:** 

When **isAutoRefreshSupported** is set to **true**, the **period** field becomes invalid.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RecentPhotoOptions-period?: number--><!--Device-RecentPhotoOptions-period?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoSource

```TypeScript
photoSource?: PhotoSource
```

Source of the recent photo or video, for example, image or video taken by the camera or screenshot. By default, the source is not restricted.

**Note:** This field is still valid when **isAutoRefreshSupported** is set to **true**.

**Type:** [PhotoSource](arkts-medialibrary-file-recentphotocomponent-photosource-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RecentPhotoOptions-photoSource?: PhotoSource--><!--Device-RecentPhotoOptions-photoSource?: PhotoSource-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
