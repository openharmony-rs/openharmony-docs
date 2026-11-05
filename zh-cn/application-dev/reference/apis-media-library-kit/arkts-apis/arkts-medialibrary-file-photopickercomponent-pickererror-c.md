# PickerError

```TypeScript
export declare class PickerError
```

使用图片选择器组件发生错误时返回的错误的接口名称、错误码和错误描述。

**起始版本：** 23

<!--Device-unnamed-export declare class PickerError--><!--Device-unnamed-export declare class PickerError-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## errorCode

```TypeScript
errorCode: number
```

错误码。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PickerError-errorCode: number--><!--Device-PickerError-errorCode: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## functionName

```TypeScript
functionName: string
```

产生错误的接口名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PickerError-functionName: string--><!--Device-PickerError-functionName: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## message

```TypeScript
message: string
```

接口返回的具体错误描述信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PickerError-message: string--><!--Device-PickerError-message: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
