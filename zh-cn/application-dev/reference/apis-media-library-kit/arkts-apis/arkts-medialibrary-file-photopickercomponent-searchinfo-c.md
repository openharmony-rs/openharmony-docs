# SearchInfo

```TypeScript
export declare class SearchInfo
```

用于调用picker搜索能力的搜索信息。`text`和`smartEntityIds`中至少有一个必须为非空，否则将抛出错误。

**起始版本：** 26.1.0

<!--Device-unnamed-export declare class SearchInfo--><!--Device-unnamed-export declare class SearchInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## smartEntityIds

```TypeScript
smartEntityIds?: Array<number>
```

从推荐标签回调中获取的智能实体id列表。每个id仅在当前picker会话生命周期内有效。

**类型：** Array&lt;number&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-SearchInfo-smartEntityIds?: Array<int>--><!--Device-SearchInfo-smartEntityIds?: Array<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## text

```TypeScript
text?: string
```

用户键入的搜索文本。如果同时提供了`text`和`smartEntityIds`，则选择器将使用组合条件进行搜索。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-SearchInfo-text?: string--><!--Device-SearchInfo-text?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
