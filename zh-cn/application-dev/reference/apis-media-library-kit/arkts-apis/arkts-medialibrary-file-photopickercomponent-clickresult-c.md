# ClickResult

```TypeScript
export declare class ClickResult
```

设置指定URI的资产是否被选中。

**起始版本：** 23

<!--Device-unnamed-export declare class ClickResult--><!--Device-unnamed-export declare class ClickResult-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## isSelected

```TypeScript
isSelected: boolean
```

设置指定的媒体文件资产是否被选中，true表示选中，false表示不选中。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-ClickResult-isSelected: boolean--><!--Device-ClickResult-isSelected: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uri

```TypeScript
uri: string
```

媒体文件资产的URI。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-ClickResult-uri: string--><!--Device-ClickResult-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
