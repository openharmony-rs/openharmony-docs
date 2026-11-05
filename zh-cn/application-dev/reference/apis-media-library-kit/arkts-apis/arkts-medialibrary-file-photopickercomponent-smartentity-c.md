# SmartEntity

```TypeScript
export declare class SmartEntity
```

推荐标签中的智能实体。

**起始版本：** 26.1.0

<!--Device-unnamed-export declare class SmartEntity--><!--Device-unnamed-export declare class SmartEntity-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## id

```TypeScript
id: number
```

实体的唯一id，在当前picker会话生命周期内有效。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-SmartEntity-id: int--><!--Device-SmartEntity-id: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## name

```TypeScript
name?: string
```

实体名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-SmartEntity-name?: string--><!--Device-SmartEntity-name?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## thumbnail

```TypeScript
thumbnail?: image.PixelMap
```

要为实体显示的缩略图，例如肖像头像。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-SmartEntity-thumbnail?: image.PixelMap--><!--Device-SmartEntity-thumbnail?: image.PixelMap-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
