# BadgeConfig

```TypeScript
export declare class BadgeConfig
```

特殊角标配置项。

**起始版本：** 21

<!--Device-unnamed-export declare class BadgeConfig--><!--Device-unnamed-export declare class BadgeConfig-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## badgeType

```TypeScript
badgeType?: BadgeType
```

特殊角标的类型。

**类型：** [BadgeType](arkts-medialibrary-file-photopickercomponent-badgetype-e.md)

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-BadgeConfig-badgeType?: BadgeType--><!--Device-BadgeConfig-badgeType?: BadgeType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uris

```TypeScript
uris?: Array<string>
```

显示角标的URI数据。

**类型：** Array&lt;string&gt;

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-BadgeConfig-uris?: Array<string>--><!--Device-BadgeConfig-uris?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
