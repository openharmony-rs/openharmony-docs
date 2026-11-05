# AnimatorParams

```TypeScript
export declare class AnimatorParams
```

进退大图动效参数。

**起始版本：** 12

<!--Device-unnamed-export declare class AnimatorParams--><!--Device-unnamed-export declare class AnimatorParams-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## curve

```TypeScript
curve?: Curve | ICurve | string
```

动效曲线。

**类型：** Curve &#124; ICurve &#124; string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AnimatorParams-curve?: Curve | ICurve | string--><!--Device-AnimatorParams-curve?: Curve | ICurve | string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## duration

```TypeScript
duration?: number
```

动效时长，单位为毫秒（ms），取值范围[0, +∞)。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AnimatorParams-duration?: number--><!--Device-AnimatorParams-duration?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
