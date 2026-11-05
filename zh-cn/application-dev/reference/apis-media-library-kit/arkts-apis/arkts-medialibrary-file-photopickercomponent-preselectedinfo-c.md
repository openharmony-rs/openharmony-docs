# PreselectedInfo

```TypeScript
export declare class PreselectedInfo
```

预选中的文件以及文件对应的图片选择器组件序号。

**起始版本：** 21

<!--Device-unnamed-export declare class PreselectedInfo--><!--Device-unnamed-export declare class PreselectedInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## preselectablePickerIndex

```TypeScript
preselectablePickerIndex?: number
```

限制仅在指定序号的图片选择器组件中进行自动选中；默认为-1，即可支持在任意序号的图片选择器组件中自动选中。

**类型：** number

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-PreselectedInfo-preselectablePickerIndex?: number--><!--Device-PreselectedInfo-preselectablePickerIndex?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uri

```TypeScript
uri: string
```

选中媒体文件的URI。

**类型：** string

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-PreselectedInfo-uri: string--><!--Device-PreselectedInfo-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
