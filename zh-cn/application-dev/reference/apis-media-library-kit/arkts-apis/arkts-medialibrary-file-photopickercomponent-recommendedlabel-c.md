# RecommendedLabel

```TypeScript
export declare class RecommendedLabel
```

用户在搜索页面点击的推荐标签。推荐标签要么是纯文本标签（只提供`text`）或智能实体标签（提供了`smartEntity`）。这两种情况是互斥的。

**起始版本：** 26.1.0

<!--Device-unnamed-export declare class RecommendedLabel--><!--Device-unnamed-export declare class RecommendedLabel-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## smartEntity

```TypeScript
smartEntity?: SmartEntity
```

智能实体，关联搜索生成标签时应用。

**类型：** [SmartEntity](arkts-medialibrary-file-photopickercomponent-smartentity-c.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecommendedLabel-smartEntity?: SmartEntity--><!--Device-RecommendedLabel-smartEntity?: SmartEntity-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
