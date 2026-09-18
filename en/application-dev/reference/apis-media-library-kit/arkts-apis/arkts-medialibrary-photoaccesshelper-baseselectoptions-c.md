# BaseSelectOptions

Defines the basic options for selecting media files from Gallery.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## assetCompatibleCapability

```TypeScript
assetCompatibleCapability?: AssetCompatibleCapability
```

Configuration for asset compatibility capabilities.

**Type:** [AssetCompatibleCapability](arkts-medialibrary-photoaccesshelper-assetcompatiblecapability-i.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## assetFilter

```TypeScript
assetFilter?: Array<OperationItem>
```

Media asset filter, with a maximum length of 50 items. If the limit is exceeded, only the first 50 items are used.

**NOTE:** 

1. When this filter is applied, other filters become invalid.
2. When setting multiple conditions, enclose the filter conditions in parentheses to prevent conflicts with
internal filter items.

**Type:** Array&lt;[OperationItem](arkts-medialibrary-photoaccesshelper-operationitem-c.md)&gt;

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## autoPlayScenes

```TypeScript
autoPlayScenes?: Array<AutoPlayScene>
```

Playback mode of the moving photo. The maximum array length is 2. If this limit is exceeded, the first two elements are used, and the extra ones are automatically ignored.

**Type:** Array&lt;[AutoPlayScene](arkts-medialibrary-photoaccesshelper-autoplayscene-c.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## combinedMediaTypeFilter

```TypeScript
combinedMediaTypeFilter?: Array<string>
```

A string array of filter criteria, supporting combinations of various types.

The string format is as follows: **photoType | photoSubType1,photoSubType2, ... | mimeType1,mimeType2, ...**

- The first part specifies a single **photoType**, which is fixed at **image** or **video**.  
- The second part lists 1 to *N* photoSubTypes, separated by commas, with an OR relationship. Currently, the  
maximum value of *N* is **1**. Options include **movingPhoto** or "*" (ignore).  
- The third part lists 1 to *N* mimeTypes, separated by commas, with an OR relationship. Currently, the maximum  
value of *N* is **10**. The format is similar to [MimeTypeFilter](arkts-medialibrary-photoaccesshelper-mimetypefilter-c.md).

Filters are combined using intersection logic.

The NOT logic is supported. To exclude types, use parentheses. Each string can have only one set.

If the filter string does not match the specifications, the result is empty.

Only the first three array elements are used; **MIMETypes** and **mimeTypeFilter** are ignored.

**Type:** Array&lt;string&gt;

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## fileSizeFilter

```TypeScript
fileSizeFilter?: FileSizeFilter
```

Configuration for file size filtering.

When this parameter is set, only media files within the specified size range are displayed. You are advised to notify users that only images or videos of the specified size can be selected.

**Type:** [FileSizeFilter](arkts-medialibrary-photoaccesshelper-filesizefilter-c.md)

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## globalMovingPhotoState

```TypeScript
globalMovingPhotoState?: MovingPhotoBadgeStateType
```

Global effect of the moving photo. Currently, only **MOVING_PHOTO_ENABLED** and **MOVING_PHOTO_DISABLED** are supported. The default value is **MOVING_PHOTO_ENABLED**.

**Type:** [MovingPhotoBadgeStateType](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridPinchMode

```TypeScript
gridPinchMode?: GridPinchMode
```

Pinch mode of the grid in the picker.

**Type:** [GridPinchMode](arkts-medialibrary-photoaccesshelper-gridpinchmode-c.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isMovingPhotoBadgeShown

```TypeScript
isMovingPhotoBadgeShown?: boolean
```

Whether the moving photo badge is displayed in the photo browser page. **true** to display the badge, **false** to hide it. The default is **false**.

If this parameter is set to **true**, [Photoselectresult](arkts-medialibrary-photoaccesshelper-photoselectresult-c.md) returns the **movingPhotoBadgeStates** array. The default status of a moving photo is [MOVING_PHOTO_ENABLED](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md).

Note: Use both **isMovingPhotoBadgeShown** and **MovingPhotoBadgeStateType** to determine whether a photo is a moving photo.

**Type:** boolean

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isPhotoTakingSupported

```TypeScript
isPhotoTakingSupported?: boolean
```

Whether photo taking is supported. **true** if supported, **false** otherwise.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isPreviewForSingleSelectionSupported

```TypeScript
isPreviewForSingleSelectionSupported?: boolean
```

Whether to enable full image preview if a single image is selected. **true** to enable, **false** otherwise. The default value is **true**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSearchSupported

```TypeScript
isSearchSupported?: boolean
```

Whether the image is searchable. **true** if searchable, **false** otherwise.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxSelectNumber

```TypeScript
maxSelectNumber?: number
```

Maximum number of media files that can be selected. The maximum value is **500**, and the default value is **50**.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## MIMEType

```TypeScript
MIMEType?: PhotoViewMIMETypes
```

Available media file types. **IMAGE_VIDEO_TYPE** is used by default.

**Type:** [PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mimeTypeFilter

```TypeScript
mimeTypeFilter?: MimeTypeFilter
```

Configuration for file type filtering. Multiple types can be specified.

When this parameter is set, the **MIMEType** configuration automatically becomes invalid.

When this parameter is set, only media files of the configured filter type are displayed. You are advised to notify users that only images or videos of the specified type can be selected.

**Type:** [MimeTypeFilter](arkts-medialibrary-photoaccesshelper-mimetypefilter-c.md)

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoViewMimeTypeFileSizeFilters

```TypeScript
photoViewMimeTypeFileSizeFilters?: Array<PhotoViewMimeTypeFileSizeFilter>
```

An array used to filter media files by type and size.

Only the first three array elements are used; **MIMETypes** and **fileSizeFilter** are ignored.

**Type:** Array&lt;[PhotoViewMimeTypeFileSizeFilter](arkts-medialibrary-photoaccesshelper-photoviewmimetypefilesizefilter-c.md)&gt;

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## preferredCompatibleMode

```TypeScript
preferredCompatibleMode?: PreferredCompatibleMode
```

Preferred compatibility mode.

**Type:** [PreferredCompatibleMode](arkts-medialibrary-photoaccesshelper-preferredcompatiblemode-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## preselectedUris

```TypeScript
preselectedUris?: Array<string>
```

URI of the preselected image.

**Type:** Array&lt;string&gt;

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## recommendationOptions

```TypeScript
recommendationOptions?: RecommendationOptions
```

Image recommendation parameters.

**Type:** [RecommendationOptions](arkts-medialibrary-photoaccesshelper-recommendationoptions-c.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## showDateOnScrollbar

```TypeScript
showDateOnScrollbar?: boolean
```

Whether to display the date group information when the scroll bar is dragged. **true**: yes; **false**: no. The default value is **false**.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## singleSelectionMode

```TypeScript
singleSelectionMode?: SingleSelectionMode
```

Single selection mode. The default value is **SingleSelectionMode.BROWSER_MODE**.

**Type:** [SingleSelectionMode](arkts-medialibrary-photoaccesshelper-singleselectionmode-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## videoDurationFilter

```TypeScript
videoDurationFilter?: VideoDurationFilter
```

Configuration for video duration filtering.

When this parameter is set, only media files within the specified duration range are displayed. You are advised to notify users that only videos of the specified length can be selected.

**Type:** [VideoDurationFilter](arkts-medialibrary-photoaccesshelper-videodurationfilter-c.md)

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
