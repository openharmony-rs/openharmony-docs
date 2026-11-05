# MaxSelected

```TypeScript
export declare class MaxSelected
```

最大选择数量。

**起始版本：** 12

<!--Device-unnamed-export declare class MaxSelected--><!--Device-unnamed-export declare class MaxSelected-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## data

```TypeScript
data?: Map<MaxCountType, number>
```

最大选择数量（包含图片的最大选择数量、视频的最大选择数量以及总的最大选择数量）。

**类型：** Map&lt;[MaxCountType](arkts-medialibrary-file-photopickercomponent-maxcounttype-e.md), number&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-MaxSelected-data?: Map<MaxCountType, number>--><!--Device-MaxSelected-data?: Map<MaxCountType, number>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
