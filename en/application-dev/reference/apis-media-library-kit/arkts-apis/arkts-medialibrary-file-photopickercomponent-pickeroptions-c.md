# PickerOptions

```TypeScript
export declare class PickerOptions extends photoAccessHelper.BaseSelectOptions
```

Describes the configuration of a Picker. It inherits from [photoAccessHelper.BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md).

**Inheritance/Implementation:** PickerOptions extends [photoAccessHelper.BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md)

**Since:** 12

<!--Device-unnamed-export declare class PickerOptions extends photoAccessHelper.BaseSelectOptions--><!--Device-unnamed-export declare class PickerOptions extends photoAccessHelper.BaseSelectOptions-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## appAlbumFilters

```TypeScript
appAlbumFilters?: Array<string>
```

Used to display only the album content corresponding to the specified bundle name. Pass a complete array of bundle name strings, which must exactly match the app package name.

**Type:** Array&lt;string&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-PickerOptions-appAlbumFilters?: Array<string>--><!--Device-PickerOptions-appAlbumFilters?: Array<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## backgroundColor

```TypeScript
backgroundColor?: string
```

Background color of the Picker grid page.

The value is an 8-digit hexadecimal color code (#AARRGGBB). The first two digits indicate the transparency, and the last six digits indicate the RGB color value.

Note: This format is different from the #RRGGBBAA format used in the CSS standard, where alpha is in the last two digits.

For example, '#FFFFFFFF' indicates a white opaque background, and '#80FF0000' indicates a semi-transparent red background.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerOptions-backgroundColor?: string--><!--Device-PickerOptions-backgroundColor?: string-End-->

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

<!--Device-PickerOptions-backgroundOpacity?: number--><!--Device-PickerOptions-backgroundOpacity?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## badgeConfig

```TypeScript
badgeConfig?: BadgeConfig
```

Badge configuration. Currently, the **PhotoPickerComponent** supports only one type of badge. For details, see [BadgeType](arkts-medialibrary-file-photopickercomponent-badgetype-e.md).

**Type:** [BadgeConfig](arkts-medialibrary-file-photopickercomponent-badgeconfig-c.md)

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-PickerOptions-badgeConfig?: BadgeConfig--><!--Device-PickerOptions-badgeConfig?: BadgeConfig-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## checkBoxColor

```TypeScript
checkBoxColor?: string
```

Background color of the check box.

The value is an 8-digit hexadecimal color code (#AARRGGBB). The first two digits indicate the transparency, and the last six digits indicate the RGB color value.

Note: This format is different from the #RRGGBBAA format used in the CSS standard, where alpha is in the last two digits.

For example, '#FFFFFFFF' indicates a white opaque background, and '#80FF0000' indicates a semi-transparent red background.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerOptions-checkBoxColor?: string--><!--Device-PickerOptions-checkBoxColor?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## checkboxTextColor

```TypeScript
checkboxTextColor?: string
```

Text color in the check box.

The value is an 8-digit hexadecimal color code (#AARRGGBB). The first two digits indicate the transparency, and the last six digits indicate the RGB color value.

Note: This format is different from the #RRGGBBAA format used in the CSS standard, where alpha is in the last two digits.

For example, '#FFFFFFFF' indicates a white opaque background, and '#80FF0000' indicates a semi-transparent red background. (This parameter is supported since API version 19. In earlier versions, the system defaults to white.)

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerOptions-checkboxTextColor?: string--><!--Device-PickerOptions-checkboxTextColor?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## contextRecoveryInfo

```TypeScript
contextRecoveryInfo?: photoAccessHelper.ContextRecoveryInfo
```

Information for restoring the photo picker component's state from the last exit. By default, this parameter is left empty, indicating that the state from the last exit is not restored.

Note: This parameter must be used together with the [completed](arkts-medialibrary-file-photopickercomponent-pickercontroller-c.md#completed) method of **PickerController**. The **contextRecoveryInfo** in the [CompletedResult](arkts-medialibrary-file-photopickercomponent-completedresult-c.md) returned by this method can be used to restore the state.

**Type:** [photoAccessHelper.ContextRecoveryInfo](arkts-medialibrary-photoaccesshelper-contextrecoveryinfo-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PickerOptions-contextRecoveryInfo?: photoAccessHelper.ContextRecoveryInfo--><!--Device-PickerOptions-contextRecoveryInfo?: photoAccessHelper.ContextRecoveryInfo-End-->

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

<!--Device-PickerOptions-edgeEffect?: EdgeEffect--><!--Device-PickerOptions-edgeEffect?: EdgeEffect-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridEndOffset

```TypeScript
gridEndOffset?: number
```

Space between the bottom of the component and the last row of the grid thumbnail. The default value is **0**, in vp.

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-PickerOptions-gridEndOffset?: number--><!--Device-PickerOptions-gridEndOffset?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridMargin

```TypeScript
gridMargin?: Margin
```

Margin of the component on a grid page.

**Type:** [Margin](../../apis-arkui/arkts-apis/arkts-arkui-margin-t.md)

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-PickerOptions-gridMargin?: Margin--><!--Device-PickerOptions-gridMargin?: Margin-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridStartOffset

```TypeScript
gridStartOffset?: number
```

Space between the top of the component and the first row of the grid thumbnail. If this parameter is not set, the default value **0** is used, in vp.

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-PickerOptions-gridStartOffset?: number--><!--Device-PickerOptions-gridStartOffset?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isRepeatSelectSupported

```TypeScript
isRepeatSelectSupported?: boolean
```

Whether a single image can be repeatedly selected. **true** if supported, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerOptions-isRepeatSelectSupported?: boolean--><!--Device-PickerOptions-isRepeatSelectSupported?: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSlidingSelectionSupported

```TypeScript
isSlidingSelectionSupported?: boolean
```

Whether to support multiple selections by sliding. **true**: yes; **false**: no. If this parameter is not set, the default value **false** is used. This parameter is not available for repeat selection.

Since API version 26.0.0, the **select** method is supported on cars, but the **isSlidingSelectionSupported** attribute is not. Therefore, this attribute does not take effect on cars.

**Type:** boolean

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-PickerOptions-isSlidingSelectionSupported?: boolean--><!--Device-PickerOptions-isSlidingSelectionSupported?: boolean-End-->

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

<!--Device-PickerOptions-isSlidingSupported?: boolean--><!--Device-PickerOptions-isSlidingSupported?: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxPhotoSelectNumber

```TypeScript
maxPhotoSelectNumber?: number
```

Maximum number of images that can be selected. The value range is [1, 500]. The default value is **500**.

The value is subject to the maximum number of available items specified by [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md).maxSelectNumber.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerOptions-maxPhotoSelectNumber?: number--><!--Device-PickerOptions-maxPhotoSelectNumber?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxSelectedReminderMode

```TypeScript
maxSelectedReminderMode?: ReminderMode
```

Mode of the reminder when the number of selected items reaches the maximum. The options are **NONE**, **TOAST**, and **MASK**. If this parameter is not set, the default value is **TOAST**.

**Type:** [ReminderMode](arkts-medialibrary-file-photopickercomponent-remindermode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerOptions-maxSelectedReminderMode?: ReminderMode--><!--Device-PickerOptions-maxSelectedReminderMode?: ReminderMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxVideoSelectNumber

```TypeScript
maxVideoSelectNumber?: number
```

Maximum number of videos that can be selected. The value range is [1, 500]. The default value is **500**.

The value is subject to the maximum number of available items specified by [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md).maxSelectNumber.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerOptions-maxVideoSelectNumber?: number--><!--Device-PickerOptions-maxVideoSelectNumber?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## orientation

```TypeScript
orientation?: PickerOrientation
```

Sliding preview direction of the grid page. The options are **HORIZONTAL** and **VERTICAL**.

If this parameter is not set, the default value is **VERTICAL**.

Set this parameter to **HORIZONTAL** if you want to browse media files horizontally.

Set this parameter to **VERTICAL** if you want to browse media files vertically, or leave this parameter empty.

This capability is supported since API version 20. In versions earlier than API version 20, the default value is **VERTICAL**.

**Type:** [PickerOrientation](arkts-medialibrary-file-photopickercomponent-pickerorientation-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerOptions-orientation?: PickerOrientation--><!--Device-PickerOptions-orientation?: PickerOrientation-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserBackgroundColorMode

```TypeScript
photoBrowserBackgroundColorMode?: PickerColorMode
```

Background color of the photo browser page. The options are **AUTO**, **LIGHT**, and **DARK**. If this parameter is not set, the default value is **AUTO**.

**Type:** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerOptions-photoBrowserBackgroundColorMode?: PickerColorMode--><!--Device-PickerOptions-photoBrowserBackgroundColorMode?: PickerColorMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserCheckboxPosition

```TypeScript
photoBrowserCheckboxPosition?: [number, number]
```

Position of the check box on the photo browser page. The first parameter specifies the offset in the X direction, and the second parameter specifies the offset in the Y direction. The value range is [0, 1], which indicates the offset (from 0% to 100%) to the upper-left corner of the component. If this parameter is not set, the default value **[0, 0]** is used.

**Type:** [number, number]

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-PickerOptions-photoBrowserCheckboxPosition?: [number, number]--><!--Device-PickerOptions-photoBrowserCheckboxPosition?: [number, number]-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserMargin

```TypeScript
photoBrowserMargin?: Margin
```

Margin of the component on a photo browser page.

**Type:** [Margin](../../apis-arkui/arkts-apis/arkts-arkui-margin-t.md)

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-PickerOptions-photoBrowserMargin?: Margin--><!--Device-PickerOptions-photoBrowserMargin?: Margin-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## pickerIndex

```TypeScript
pickerIndex?: number
```

Unique serial number used to distinguish different picker components. The value range is [–1, +∞). The default value is **–1**, indicating that the picker component is not distinguished. If multiple phone picker components are used in an app and different components need to be distinguished, set different unique IDs for the components.

When using the **preselectedInfos** attribute to display data, you need to set **pickerIndex** and match it with **preselectablePickerIndex** in [PreselectedInfo](arkts-medialibrary-file-photopickercomponent-preselectedinfo-c.md) to display the data in the specified component.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-PickerOptions-pickerIndex?: number--><!--Device-PickerOptions-pickerIndex?: number-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## preselectedInfos

```TypeScript
preselectedInfos?: Array<PreselectedInfo>
```

Displaying the pre-selected data in the image chip selector component with the specified **pickerIndex**.

**Type:** Array&lt;[PreselectedInfo](arkts-medialibrary-file-photopickercomponent-preselectedinfo-c.md)&gt;

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-PickerOptions-preselectedInfos?: Array<PreselectedInfo>--><!--Device-PickerOptions-preselectedInfos?: Array<PreselectedInfo>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## selectMode

```TypeScript
selectMode?: SelectMode
```

Selection mode of the photo picker component, including **MULTI_SELECT** and **SINGLE_SELECT**.

If this parameter is not set, **MULTI_SELECT** is used by default.

Set this parameter to **SINGLE_SELECT** if only one file needs to be selected.

Set this parameter to **MULTI_SELECT** if multiple files need to be selected, or leave this parameter empty.

**Type:** [SelectMode](arkts-medialibrary-file-photopickercomponent-selectmode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PickerOptions-selectMode?: SelectMode--><!--Device-PickerOptions-selectMode?: SelectMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## singleLineConfig

```TypeScript
singleLineConfig?: SingleLineConfig
```

Single-line display mode of a grid page. In single-line mode, the component does not provide functions for viewing a larger image. The component does not support callbacks related to large image browsing, such as **onEnterPhotoBrowser** and **onExitPhotoBrowser**. The **PickerController** does not support APIs related to large image browsing, such as **setPhotoBrowserItem** and **exitPhotoBrowser**. As a result, API calls will be ineffective.

**Type:** [SingleLineConfig](arkts-medialibrary-file-photopickercomponent-singlelineconfig-c.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-PickerOptions-singleLineConfig?: SingleLineConfig--><!--Device-PickerOptions-singleLineConfig?: SingleLineConfig-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uiComponentColorMode

```TypeScript
uiComponentColorMode?: PickerColorMode
```

Picker color mode. Dark/Light color mode (excluding the background color) of other components on the Picker grid page, including the search box, camera entry, safety tips for using Gallery, and recommendation bubble. This attribute is usually used together with **backgroundColor**. If this parameter is not set, the default value **PickerColorMode.AUTO** is used, which means that the color mode changes with the system dark/light color mode.

When setting this attribute, avoid using **PickerColorMode.LIGHT** with a dark backgroundColor, as it may make components or text hard to see. Avoid using **PickerColorMode.DARK** with a light backgroundColor for the same reason.

**Type:** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-PickerOptions-uiComponentColorMode?: PickerColorMode--><!--Device-PickerOptions-uiComponentColorMode?: PickerColorMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
