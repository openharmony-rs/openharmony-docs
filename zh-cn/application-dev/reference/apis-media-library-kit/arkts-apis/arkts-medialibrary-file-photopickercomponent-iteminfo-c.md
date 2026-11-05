# ItemInfo

```TypeScript
export declare class ItemInfo extends BaseItemInfo
```

继承自[BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md)，增加私有参数itemType。

图片、视频相关信息。

**继承/实现关系：** ItemInfo extends [BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md)

**起始版本：** 12

<!--Device-unnamed-export declare class ItemInfo extends BaseItemInfo--><!--Device-unnamed-export declare class ItemInfo extends BaseItemInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## itemType

```TypeScript
itemType?: ItemType
```

被点击的item类型。包括缩略图item和相机item。

**类型：** [ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ItemInfo-itemType?: ItemType--><!--Device-ItemInfo-itemType?: ItemType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
