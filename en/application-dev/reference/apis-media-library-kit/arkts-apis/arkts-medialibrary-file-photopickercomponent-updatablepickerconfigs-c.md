# UpdatablePickerConfigs

```TypeScript
export declare class UpdatablePickerConfigs
```

New attributes, which are a subset of [PickerOptions](arkts-medialibrary-file-photopickercomponent-pickeroptions-c.md).

**Since:** 22

<!--Device-unnamed-export declare class UpdatablePickerConfigs--><!--Device-unnamed-export declare class UpdatablePickerConfigs-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## appAlbumFilters

```TypeScript
appAlbumFilters?: Array<string>
```

Used to display only the album content corresponding to the specified bundle name.

**Type:** Array&lt;string&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-UpdatablePickerConfigs-appAlbumFilters?: Array<string>--><!--Device-UpdatablePickerConfigs-appAlbumFilters?: Array<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## autoPlayScenes

```TypeScript
autoPlayScenes?: Array<photoAccessHelper.AutoPlayScene>
```

Automatic playback scenarios for moving photos. A maximum of two automatic playback scenarios can be configured. If more than two scenarios are configured, only the first two are used, and the extra ones are automatically ignored.

**Type:** Array&lt;[photoAccessHelper.AutoPlayScene](arkts-medialibrary-photoaccesshelper-autoplayscene-c.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-UpdatablePickerConfigs-autoPlayScenes?: Array<photoAccessHelper.AutoPlayScene>--><!--Device-UpdatablePickerConfigs-autoPlayScenes?: Array<photoAccessHelper.AutoPlayScene>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## backgroundColor

```TypeScript
backgroundColor?: string
```

Background color of the grid page of the photo picker component. The value is an 8-digit hexadecimal color code. The first two digits indicate the transparency, and the last six digits indicate the RGB color value.

For example, '#FFFFFFFF' indicates a white opaque background.

**Type:** string

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-backgroundColor?: string--><!--Device-UpdatablePickerConfigs-backgroundColor?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## backgroundOpacity

```TypeScript
backgroundOpacity?: number
```

Background transparency of the photo picker component. The value range is [0, 1]. **0** indicates completely transparent, and **1** indicates completely opaque.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-UpdatablePickerConfigs-backgroundOpacity?: number--><!--Device-UpdatablePickerConfigs-backgroundOpacity?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## checkBoxColor

```TypeScript
checkBoxColor?: string
```

Background color of the check box.

The value is an 8-digit hexadecimal color code.

**Type:** string

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-checkBoxColor?: string--><!--Device-UpdatablePickerConfigs-checkBoxColor?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## checkboxTextColor

```TypeScript
checkboxTextColor?: string
```

Text color in the check box.

The value is an 8-digit hexadecimal color code.

**Type:** string

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-checkboxTextColor?: string--><!--Device-UpdatablePickerConfigs-checkboxTextColor?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## edgeEffect

```TypeScript
edgeEffect?: EdgeEffect
```

Scrolling effect when the grid page of the photo picker component reaches the edge.

The default value is [EdgeEffect.Spring](../../apis-arkui/arkts-apis/arkts-arkui-edgeeffect-e.md).

**Type:** [EdgeEffect](../../apis-arkui/arkts-apis/arkts-arkui-edgeeffect-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-UpdatablePickerConfigs-edgeEffect?: EdgeEffect--><!--Device-UpdatablePickerConfigs-edgeEffect?: EdgeEffect-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridMargin

```TypeScript
gridMargin?: Margin
```

Margin of the component grid.

**Type:** [Margin](../../apis-arkui/arkts-apis/arkts-arkui-margin-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-UpdatablePickerConfigs-gridMargin?: Margin--><!--Device-UpdatablePickerConfigs-gridMargin?: Margin-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isRepeatSelectSupported

```TypeScript
isRepeatSelectSupported?: boolean
```

Whether a single image can be repeatedly selected.

**true** if supported, **false** otherwise. If this parameter is not set, the default value **false** is used.

**Type:** boolean

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-isRepeatSelectSupported?: boolean--><!--Device-UpdatablePickerConfigs-isRepeatSelectSupported?: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSlidingSupported

```TypeScript
isSlidingSupported?: boolean
```

Whether to block scrolling of the photo picker component. The value **true** means that scrolling is not blocked and the component responds to user scroll gestures. The value **false** means that scrolling is blocked and the component does not respond to user scroll gestures.

The default value is **true**.

**NOTE:** 

When **isSlidingSupported** is set to **false**, the grid thumbnail does not respond to the user's tap gesture to view the full image. Callbacks related to large image browsing, such as **onEnterPhotoBrowser**, will not be triggered.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-UpdatablePickerConfigs-isSlidingSupported?: boolean--><!--Device-UpdatablePickerConfigs-isSlidingSupported?: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxPhotoSelectNumber

```TypeScript
maxPhotoSelectNumber?: number
```

Maximum number of images that can be selected. The value range is [0, 500], and this parameter is limited by the total number of images that can be selected. The default value is **500**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-maxPhotoSelectNumber?: number--><!--Device-UpdatablePickerConfigs-maxPhotoSelectNumber?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxSelectNumber

```TypeScript
maxSelectNumber?: number
```

Maximum number of media files that can be selected. The value range is [0, 500], and the default value is **50**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-maxSelectNumber?: number--><!--Device-UpdatablePickerConfigs-maxSelectNumber?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxVideoSelectNumber

```TypeScript
maxVideoSelectNumber?: number
```

Maximum number of videos that can be selected. The value range is [0, 500]. The value is limited by the maximum number of media files that can be selected in the system. The default value is **500**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-maxVideoSelectNumber?: number--><!--Device-UpdatablePickerConfigs-maxVideoSelectNumber?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mimeType

```TypeScript
mimeType?: photoAccessHelper.PhotoViewMIMETypes
```

MIME types.

If this parameter is not specified, **IMAGE_VIDEO_TYPE** is used by default.

**NOTE:** 

When this parameter is set, the **mimeType** configuration automatically becomes invalid.

**Type:** [photoAccessHelper.PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-mimeType?: photoAccessHelper.PhotoViewMIMETypes--><!--Device-UpdatablePickerConfigs-mimeType?: photoAccessHelper.PhotoViewMIMETypes-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mimeTypeFilter

```TypeScript
mimeTypeFilter?: photoAccessHelper.MimeTypeFilter
```

Configuration for file type filtering. Multiple types can be specified.

- When this parameter is set, the **mimeType** configuration automatically becomes invalid.  
- When this parameter is set, only media files of the configured filter type are displayed. You are advised to  
notify users that only images or videos of the specified type can be selected.

**Type:** [photoAccessHelper.MimeTypeFilter](arkts-medialibrary-photoaccesshelper-mimetypefilter-c.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-mimeTypeFilter?: photoAccessHelper.MimeTypeFilter--><!--Device-UpdatablePickerConfigs-mimeTypeFilter?: photoAccessHelper.MimeTypeFilter-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserBackgroundColorMode

```TypeScript
photoBrowserBackgroundColorMode?: PickerColorMode
```

Background color of the photo browser page.

The options are **AUTO**, **LIGHT**, and **DARK**. The default value is **AUTO**.

**Type:** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-photoBrowserBackgroundColorMode?: PickerColorMode--><!--Device-UpdatablePickerConfigs-photoBrowserBackgroundColorMode?: PickerColorMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserMargin

```TypeScript
photoBrowserMargin?: Margin
```

Margin of the component large image.

**Type:** [Margin](../../apis-arkui/arkts-apis/arkts-arkui-margin-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-UpdatablePickerConfigs-photoBrowserMargin?: Margin--><!--Device-UpdatablePickerConfigs-photoBrowserMargin?: Margin-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## preselectedUris

```TypeScript
preselectedUris?: Array<string>
```

URIs of the preselected images. The array length is specified by [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md).maxSelectNumber, [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-photoselectoptions-c.md).maxPhotoSelectNumber, and [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-photoselectoptions-c.md). maxVideoSelectNumber. The value range is [0, 500], and the default value is **50**. If the value is out of the range, the excess part does not take effect. If this parameter is not set, no image is preselected by default.

**Type:** Array&lt;string&gt;

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-preselectedUris?: Array<string>--><!--Device-UpdatablePickerConfigs-preselectedUris?: Array<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## selectMode

```TypeScript
selectMode?: SelectMode
```

Selection mode of the photo picker component.

**SINGLE_SELECT** or **MULTI_SELECT**. The default value is **MULTI_SELECT**.

**Type:** [SelectMode](arkts-medialibrary-file-photopickercomponent-selectmode-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-selectMode?: SelectMode--><!--Device-UpdatablePickerConfigs-selectMode?: SelectMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## singleSelectionMode

```TypeScript
singleSelectionMode?: photoAccessHelper.SingleSelectionMode
```

Single selection mode. The default value is **SingleSelectionMode.BROWSER_MODE**.

**Type:** [photoAccessHelper.SingleSelectionMode](arkts-medialibrary-photoaccesshelper-singleselectionmode-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-singleSelectionMode?: photoAccessHelper.SingleSelectionMode--><!--Device-UpdatablePickerConfigs-singleSelectionMode?: photoAccessHelper.SingleSelectionMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uiComponentColorMode

```TypeScript
uiComponentColorMode?: PickerColorMode
```

Color mode of the Picker UI component.

Dark/light color mode of components other than the background color on the grid page of the photo picker component, including the search box, camera entry, safety tips for using Gallery, and recommendation bubble. This attribute is usually used together with **backgroundColor**. The default value is **PickerColorMode.AUTO**, which follows the system's dark/light color mode.

When setting this attribute, avoid using **PickerColorMode.LIGHT** with a dark background color, as it may make components or text hard to see. Avoid using **PickerColorMode.DARK** with a light background color for the same reason.

**Type:** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UpdatablePickerConfigs-uiComponentColorMode?: PickerColorMode--><!--Device-UpdatablePickerConfigs-uiComponentColorMode?: PickerColorMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
