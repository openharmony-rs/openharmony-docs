# PickerOptions

Describes the configuration of a Picker. It inherits from [photoAccessHelper.BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md).

**Inheritance/Implementation:** PickerOptions extends [photoAccessHelper.BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md)

**Since:** 12

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

## backgroundColor

```TypeScript
backgroundColor?: string
```

Background color of the Picker grid page. The value is an 8-digit hexadecimal color code.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

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

## badgeConfig

```TypeScript
badgeConfig?: BadgeConfig
```

Badge configuration. Currently, the **PhotoPickerComponent** supports only one type of badge. For details, see [BadgeType](arkts-medialibrary-file-photopickercomponent-badgetype-e.md).

**Type:** [BadgeConfig](arkts-medialibrary-file-photopickercomponent-badgeconfig-c.md)

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## checkBoxColor

```TypeScript
checkBoxColor?: string
```

Background color of the check box.

The value is an 8-digit hexadecimal color code. The first two digits indicate the transparency, and the last six digits indicate the RGB color value.

For example, '#FFFFFFFF' indicates a white opaque background, and '#80FF0000' indicates a semi-transparent red background.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## checkboxTextColor

```TypeScript
checkboxTextColor?: string
```

Text color in the check box. The value is an 8-digit hexadecimal color code. (This parameter is supported since API version 19. In earlier versions, the system defaults to white.)

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## contextRecoveryInfo

```TypeScript
contextRecoveryInfo?: photoAccessHelper.ContextRecoveryInfo
```

Information for restoring the PhotoPicker's state from the last exit.

**Type:** [photoAccessHelper.ContextRecoveryInfo](arkts-medialibrary-photoaccesshelper-contextrecoveryinfo-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

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

## gridEndOffset

```TypeScript
gridEndOffset?: number
```

Space between the bottom of the component and the last row of the grid thumbnail. The default value is **0**, in vp.

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridMargin

```TypeScript
gridMargin?: Margin
```

Margin of the component on a grid page.

**Type:** [Margin](../../apis-arkui/arkts-apis/arkts-arkui-margin-t.md)

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridStartOffset

```TypeScript
gridStartOffset?: number
```

Space between the top of the component and the first row of the grid thumbnail. The default value is **0**, in vp.

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isRepeatSelectSupported

```TypeScript
isRepeatSelectSupported?: boolean
```

Whether a single image can be repeatedly selected. **true** if supported, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSlidingSelectionSupported

```TypeScript
isSlidingSelectionSupported?: boolean
```

Whether to support multiple selections by sliding. **true**: yes; **false**: no. The default value is **false**. This parameter is not available for repeat selection.

**Type:** boolean

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

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

Maximum number of images that can be selected. The maximum value is **500**, which is limited by **MaxSelected**. The default value is **500**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxSelectedReminderMode

```TypeScript
maxSelectedReminderMode?: ReminderMode
```

Mode of the reminder when the number of selected items reaches the maximum. The options are **NONE**, **TOAST**, and **MASK**. The default value **TOAST**.

**Type:** [ReminderMode](arkts-medialibrary-file-photopickercomponent-remindermode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxVideoSelectNumber

```TypeScript
maxVideoSelectNumber?: number
```

Maximum number of videos that can be selected. The maximum value is **500**, and it is restricted by the maximum number of media files that can be selected in the system. The default value is **500**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## orientation

```TypeScript
orientation?: PickerOrientation
```

Sliding preview direction of the grid page. The options are **HORIZONTAL** and **VERTICAL**. The default value is **VERTICAL**. (This parameter is supported since API version 20. In earlier versions, the system defaults to vertical.)

**Type:** [PickerOrientation](arkts-medialibrary-file-photopickercomponent-pickerorientation-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserBackgroundColorMode

```TypeScript
photoBrowserBackgroundColorMode?: PickerColorMode
```

Background color of the photo browser page. The options are **AUTO**, **LIGHT**, and **DARK**. The default value is **AUTO**.

**Type:** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserCheckboxPosition

```TypeScript
photoBrowserCheckboxPosition?: [number, number]
```

Position of the check box on the photo browser page. The first parameter specifies the offset in the X direction, and the second parameter specifies the offset in the Y direction. The value range is [0, 1], which indicates the offset (from 0% to 100%) to the upper-left corner of the component. The default value is [0, 0].

**Type:** [number, number]

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserMargin

```TypeScript
photoBrowserMargin?: Margin
```

Margin of the component on a photo browser page.

**Type:** [Margin](../../apis-arkui/arkts-apis/arkts-arkui-margin-t.md)

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## pickerIndex

```TypeScript
pickerIndex?: number
```

Unique serial number used to distinguish different picker components. The default value is **-1**, indicating that no distinction is made.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## preselectedInfos

```TypeScript
preselectedInfos?: Array<PreselectedInfo>
```

Array of information previously selected by the user, so that the PhotoPickerComponent identified by **pickerIndex** can display the information.

**Type:** Array&lt;[PreselectedInfo](arkts-medialibrary-file-photopickercomponent-preselectedinfo-c.md)&gt;

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## selectMode

```TypeScript
selectMode?: SelectMode
```

Select mode, which can be **SINGLE_SELECT** or **MULTI_SELECT**. The default value is **MULTI_SELECT**.

**Type:** [SelectMode](arkts-medialibrary-file-photopickercomponent-selectmode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## singleLineConfig

```TypeScript
singleLineConfig?: SingleLineConfig
```

Single-line display mode of a grid page. In single-line mode, the component does not provide functions for viewing a larger image. The component does not support callbacks related to large images, and the PickerController does not support APIs related to large images, making API calls ineffective.

**Type:** [SingleLineConfig](arkts-medialibrary-file-photopickercomponent-singlelineconfig-c.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uiComponentColorMode

```TypeScript
uiComponentColorMode?: PickerColorMode
```

Picker color mode. Dark/Light color mode (excluding the background color) of other components on the Picker grid page, including the search box, camera entry, safety tips for using Gallery, and recommendation bubble. This attribute is usually used together with **backgroundColor**. The default value is **PickerColorMode.AUTO**, which follows the system's dark/light color mode.

When setting this attribute, avoid using **PickerColorMode.LIGHT** with a dark backgroundColor, as it may make components or text hard to see. Avoid using **PickerColorMode.DARK** with a light backgroundColor for the same reason.

**Type:** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
