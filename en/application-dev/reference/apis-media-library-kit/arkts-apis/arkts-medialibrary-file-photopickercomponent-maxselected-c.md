# MaxSelected

```TypeScript
export declare class MaxSelected
```

Represents the maximum number of media assets that can be selected at a time.

**Since:** 12

<!--Device-unnamed-export declare class MaxSelected--><!--Device-unnamed-export declare class MaxSelected-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## data

```TypeScript
data?: Map<MaxCountType, number>
```

Maximum number of media assets (images, videos, or both) that can be selected at a time.

**Type:** Map&lt;[MaxCountType](arkts-medialibrary-file-photopickercomponent-maxcounttype-e.md), number&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MaxSelected-data?: Map<MaxCountType, number>--><!--Device-MaxSelected-data?: Map<MaxCountType, number>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
