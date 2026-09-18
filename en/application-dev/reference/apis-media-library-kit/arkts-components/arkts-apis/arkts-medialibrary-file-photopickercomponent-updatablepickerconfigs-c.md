# UpdatablePickerConfigs

Describes the updatable attributes of the **PhotoPickerComponent**. These attributes are a subset of [PickerOptions](arkts-medialibrary-file-photopickercomponent-pickeroptions-c.md).

**Since:** 22

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

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## autoPlayScenes

```TypeScript
autoPlayScenes?: Array<photoAccessHelper.AutoPlayScene>
```

Playback mode of the moving photo. The maximum array length is 2. If this limit is exceeded, the first two elements are used, and the extra ones are automatically ignored.

**Type:** Array&lt;[photoAccessHelper.AutoPlayScene](arkts-medialibrary-photoaccesshelper-autoplayscene-c.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## backgroundColor

```TypeScript
backgroundColor?: string
```

Background color of the Picker grid page.

The value is an 8-digit hexadecimal color code.

**Type:** string

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## backgroundOpacity

```TypeScript
backgroundOpacity?: number
```

Background opacity of the picker. The value range is [0, 1]. **0** indicates completely transparent, and **1** indicates completely opaque.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

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

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## edgeEffect

```TypeScript
edgeEffect?: EdgeEffect
```

Scrolling effect when the Picker grid page reaches the edge.

The default value is [EdgeEffect.Spring](../../apis-arkui/arkts-apis/arkts-arkui-edgeeffect-e.md).

**Type:** [EdgeEffect](../../apis-arkui/arkts-apis/arkts-arkui-edgeeffect-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

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

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isRepeatSelectSupported

```TypeScript
isRepeatSelectSupported?: boolean
```

Whether a single image can be repeatedly selected.

**true** if supported, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSlidingSupported

```TypeScript
isSlidingSupported?: boolean
```

Whether scrolling in the **PhotoPickerComponent** is enabled. The value **true** means that scrolling is not blocked and the component responds to user scroll gestures. The value **false** means that scrolling is blocked and the component does not respond to user scroll gestures.

The default value is **true**.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxPhotoSelectNumber

```TypeScript
maxPhotoSelectNumber?: number
```

Maximum number of images that can be selected (unit: number).

The maximum value is **500**, which is limited by **MaxSelected**. The default value is **500**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxSelectNumber

```TypeScript
maxSelectNumber?: number
```

Maximum number of media files that can be selected.

The maximum value is 500, and the default value is 50.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxVideoSelectNumber

```TypeScript
maxVideoSelectNumber?: number
```

Maximum number of videos that can be selected (unit: number).

The maximum value is **500**, and it is restricted by the maximum number of media files that can be selected in the system. The default value is **500**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mimeType

```TypeScript
mimeType?: photoAccessHelper.PhotoViewMIMETypes
```

MIME types.

If this parameter is not specified, **IMAGE_VIDEO_TYPE** is used by default.

**Type:** [photoAccessHelper.PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

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

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## preselectedUris

```TypeScript
preselectedUris?: Array<string>
```

URIs of the selected images.

**Type:** Array&lt;string&gt;

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## selectMode

```TypeScript
selectMode?: SelectMode
```

Picker selection mode.

**SINGLE_SELECT** or **MULTI_SELECT**. The default value is **MULTI_SELECT**.

**Type:** [SelectMode](arkts-medialibrary-file-photopickercomponent-selectmode-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## singleSelectionMode

```TypeScript
singleSelectionMode?: photoAccessHelper.SingleSelectionMode
```

Single selection mode. The default value is **SingleSelectionMode.BROWSER_MODE**.

**Type:** [photoAccessHelper.SingleSelectionMode](arkts-medialibrary-photoaccesshelper-singleselectionmode-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uiComponentColorMode

```TypeScript
uiComponentColorMode?: PickerColorMode
```

Color mode of the Picker UI component.

Dark/Light color mode (excluding the background color) of other components on the Picker grid page, including the search box, camera entry, safety tips for using Gallery, and recommendation bubble. This attribute is usually used together with **backgroundColor**. The default value is **PickerColorMode.AUTO**, which follows the system's dark/ light color mode.

When setting this attribute, avoid using **PickerColorMode.LIGHT** with a dark background color, as it may make components or text hard to see. Avoid using **PickerColorMode.DARK** with a light background color for the same reason.

**Type:** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
