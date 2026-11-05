# @ohos.file.PhotoPickerComponent(PhotoPickerComponent)

The **PhotoPickerComponent** can be embedded in the UI of an app. This component allows the app to select media files
 without requesting any permissions. The photo picker component supports two view modes: grid view and large image
 preview. It provides both single and multiple selection modes. Users can take new photos using the camera entry, and
 preview and select moving photos. Once the users have made their selection, your application gets read-only access to
 the chosen images or videos.

Note that the photo picker component does not support nesting. Additionally, prevent overlaying components with the
 **overlay** attribute or of higher levels on top the component, as this will prevent it from receiving gesture
 events.

The user can directly tap this component to select images or videos.

> **NOTE**
 >
 > - This component is supported since API version 12. Newly added APIs will be marked with a superscript to indicate
 > their
 >
 > - This component does not support [same-layer rendering](../../../web/web-same-layer.md).

## Attributes

The universal attributes are supported.

## Modules to Import

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AnimatorParams](arkts-medialibrary-file-photopickercomponent-animatorparams-c.md) | Defines animation parameters for entering or exiting the photo browser page. |
| [BadgeConfig](arkts-medialibrary-file-photopickercomponent-badgeconfig-c.md) | Describes the badge configuration. |
| [BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md) | Represents basic image and video information. |
| [ClickResult](arkts-medialibrary-file-photopickercomponent-clickresult-c.md) | Sets whether the asset with the specified URI is selected. |
| [CompletedResult](arkts-medialibrary-file-photopickercomponent-completedresult-c.md) | Defines the information about the Picker's state from the last exit. |
| [ItemInfo](arkts-medialibrary-file-photopickercomponent-iteminfo-c.md) | It inherits from [BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md), adding the parameter **itemType**. |
| [MaxSelected](arkts-medialibrary-file-photopickercomponent-maxselected-c.md) | Represents the maximum number of media assets that can be selected at a time. |
| [PhotoBrowserInfo](arkts-medialibrary-file-photopickercomponent-photobrowserinfo-c.md) | Represents information about the photo browser page. |
| [PickerController](arkts-medialibrary-file-photopickercomponent-pickercontroller-c.md) | Defines an instance used to send data to the **PhotoPickerComponent**. |
| [PickerError](arkts-medialibrary-file-photopickercomponent-pickererror-c.md) | Describes the function name, error code, and message of the error returned when an error occurs during the use of the photo picker component. |
| [PickerOptions](arkts-medialibrary-file-photopickercomponent-pickeroptions-c.md) | Describes the configuration of a Picker. It inherits from [photoAccessHelper.BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md). |
| [PreselectedInfo](arkts-medialibrary-file-photopickercomponent-preselectedinfo-c.md) | Describes the information about the preselected files and their corresponding **PhotoPickerComponent** index. |
| [RecommendedLabel](arkts-medialibrary-file-photopickercomponent-recommendedlabel-c.md) | Indicates the recommendation label clicked by the user on the search page. A recommendation label is either a pure text label (only `text` is provided) or a smart entity label (`smartEntity` is provided). The two cases are mutually exclusive. |
| [RecoveryResult](arkts-medialibrary-file-photopickercomponent-recoveryresult-c.md) | RecoveryResult |
| [SearchInfo](arkts-medialibrary-file-photopickercomponent-searchinfo-c.md) | Indicates the search information used to invoke the picker search capability. At least one of `text` and `smartEntityIds` must be non-empty; otherwise an error is thrown. |
| [SingleLineConfig](arkts-medialibrary-file-photopickercomponent-singlelineconfig-c.md) | Represents the single-line display mode. In single-line mode, the component does not provide functions for viewing a larger image. The component does not support callbacks related to large images, and the PickerController does not support APIs related to large images, making API calls ineffective. |
| [SmartEntity](arkts-medialibrary-file-photopickercomponent-smartentity-c.md) | Indicates a smart entity in the recommendation label. |
| [UnselectableItemInfo](arkts-medialibrary-file-photopickercomponent-unselectableiteminfo-c.md) | Details about the image that is tapped but cannot be selected. |
| [UpdatablePickerConfigs](arkts-medialibrary-file-photopickercomponent-updatablepickerconfigs-c.md) | New attributes, which are a subset of [PickerOptions](arkts-medialibrary-file-photopickercomponent-pickeroptions-c.md). |

### Structs

| Name | Description |
| --- | --- |
| [PhotoPickerComponent](arkts-medialibrary-file-photopickercomponent-photopickercomponent-s.md) | PhotoPickerComponent({ pickerOptions?: PickerOptions, onSelect?: (uri: string) =&gt; void, onDeselect?: (uri: string) =&gt; void, onItemClicked?: (itemInfo: ItemInfo, clickType: ClickType) =&gt; boolean, onItemClickedNotify?: ItemClickedNotifyCallback, onEnterPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) =&gt; boolean, onExitPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) =&gt; boolean, onPickerControllerReady?: () =&gt; void, onPhotoBrowserChanged?: (browserItemInfo: BaseItemInfo) =&gt; boolean, onSelectedItemsDeleted?: ItemsDeletedCallback, onExceedMaxSelected?: ExceedMaxSelectedCallback, onCurrentAlbumDeleted?: CurrentAlbumDeletedCallback, onVideoPlayStateChanged?: videoPlayStateChangedCallback, pickerController: PickerController }) |

### Types

| Name | Description |
| --- | --- |
| [CurrentAlbumDeletedCallback](arkts-medialibrary-currentalbumdeletedcallback-t.md) | Called when the current album is deleted. |
| [ErrorCallback](arkts-medialibrary-errorcallback-t.md) | Describes the callback to be invoked when an error occurs during the use of the **PhotoPickerComponent**. |
| [ExceedMaxSelectedCallback](arkts-medialibrary-exceedmaxselectedcallback-t.md) | Called when items are selected after the maximum count has been reached. |
| [ItemClickedNotifyCallback](arkts-medialibrary-itemclickednotifycallback-t.md) | Callback to be invoked when an item in a **PhotoPickerComponent** is clicked. |
| [ItemsDeletedCallback](arkts-medialibrary-itemsdeletedcallback-t.md) | Called when the selected items are deleted. |
| [MovingPhotoBadgeStateChangedCallback](arkts-medialibrary-movingphotobadgestatechangedcallback-t.md) | Callback to be invoked when the moving photo effect of the **PhotoPickerComponent** is enabled or disabled. |
| [PhotoBrowserChangeStartCallback](arkts-medialibrary-photobrowserchangestartcallback-t.md) | Callback to be invoked when a grid view switches to the photo browser page or the photo browser page is switched. |
| [PhotoBrowserZoomCallback](arkts-medialibrary-photobrowserzoomcallback-t.md) | Called when the user zooms in or out on a full image after entering the full image view through **PhotoPickerComponent**. |
| [PickerRecoveryCallback](arkts-medialibrary-pickerrecoverycallback-t.md) | The callback of onPickerRecovery event |
| [PickerStateChangedCallback](arkts-medialibrary-pickerstatechangedcallback-t.md) | The callback of onPickerStateChanged event. |
| [PinchGridSwitchedCallback](arkts-medialibrary-pinchgridswitchedcallback-t.md) | Callback to be invoked when a user pinches a grid component. |
| [RecommendedLabelClickedCallback](arkts-medialibrary-recommendedlabelclickedcallback-t.md) | The callback of onRecommendedLabelClicked event. |
| [ScrollStopAtEndCallback](arkts-medialibrary-scrollstopatendcallback-t.md) | Callback to be invoked when the user stops scrolling and is positioned at the end of the grid content in the **PhotoPickerComponent**. |
| [ScrollStopAtStartCallback](arkts-medialibrary-scrollstopatstartcallback-t.md) | Callback to be invoked when the user stops scrolling and is positioned at the beginning of the grid content in the **PhotoPickerComponent**. |
| [UnselectableItemClickedCallback](arkts-medialibrary-unselectableitemclickedcallback-t.md) | Describes the callback invoked when an unselectable image is tapped on the picker grid or large image preview screen. |
| [videoPlayStateChangedCallback](arkts-medialibrary-videoplaystatechangedcallback-t.md) | Callback to be invoked when the video playback state on a photo browser page changes. |

### Enums

| Name | Description |
| --- | --- |
| [BadgeType](arkts-medialibrary-file-photopickercomponent-badgetype-e.md) | Enumerates the badge types. |
| [ClickType](arkts-medialibrary-file-photopickercomponent-clicktype-e.md) | Enumerates the click operation types. |
| [DataType](arkts-medialibrary-file-photopickercomponent-datatype-e.md) | Enumerates the types of data sent from **PickerController** to the **PhotoPickerComponent**. |
| [ItemDisplayRatio](arkts-medialibrary-file-photopickercomponent-itemdisplayratio-e.md) | Enumerates the aspect ratios for grid display in single-line display mode. |
| [ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md) | Enumerates the types of the item clicked. |
| [MaxCountType](arkts-medialibrary-file-photopickercomponent-maxcounttype-e.md) | Enumerates the types of the maximum count. |
| [PhotoBrowserRange](arkts-medialibrary-file-photopickercomponent-photobrowserrange-e.md) | Enumerates the view range on the photo browser page. |
| [PhotoBrowserUIElement](arkts-medialibrary-file-photopickercomponent-photobrowseruielement-e.md) | Represents other UI elements except the image preview component on the photo browser page. |
| [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md) | Enumerates the Picker color modes. |
| [PickerOrientation](arkts-medialibrary-file-photopickercomponent-pickerorientation-e.md) | Enumerates the sliding preview directions of the Picker grid page. |
| [PickerState](arkts-medialibrary-file-photopickercomponent-pickerstate-e.md) | Indicates the picker page state. |
| [ReminderMode](arkts-medialibrary-file-photopickercomponent-remindermode-e.md) | Enumerates the types of the reminder when the number of selected items reaches the maximum. |
| [SaveMode](arkts-medialibrary-file-photopickercomponent-savemode-e.md) | Enumerates the modes for saving images or videos. |
| [SelectMode](arkts-medialibrary-file-photopickercomponent-selectmode-e.md) | Enumerates the selection modes. |
| [VideoPlayerState](arkts-medialibrary-file-photopickercomponent-videoplayerstate-e.md) | Enumerates the video playback states. |
