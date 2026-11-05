# SearchInfo

```TypeScript
export declare class SearchInfo
```

Indicates the search information used to invoke the picker search capability. At least one of `text` and `smartEntityIds` must be non-empty; otherwise an error is thrown.

**Since:** 26.1.0

<!--Device-unnamed-export declare class SearchInfo--><!--Device-unnamed-export declare class SearchInfo-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## smartEntityIds

```TypeScript
smartEntityIds?: Array<number>
```

Smart entity id list obtained from the recommendation label callback. Each id is valid only within the current picker session lifecycle.

**Type:** Array&lt;number&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SearchInfo-smartEntityIds?: Array<int>--><!--Device-SearchInfo-smartEntityIds?: Array<int>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## text

```TypeScript
text?: string
```

Search text typed by the user. If both `text` and `smartEntityIds` are provided, the picker searches using the combined condition.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SearchInfo-text?: string--><!--Device-SearchInfo-text?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
