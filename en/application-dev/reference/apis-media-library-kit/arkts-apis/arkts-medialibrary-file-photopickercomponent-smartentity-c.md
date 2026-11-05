# SmartEntity

```TypeScript
export declare class SmartEntity
```

Indicates a smart entity in the recommendation label.

**Since:** 26.1.0

<!--Device-unnamed-export declare class SmartEntity--><!--Device-unnamed-export declare class SmartEntity-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## id

```TypeScript
id: number
```

Unique id of the entity, valid within the current picker session lifecycle. The value should be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SmartEntity-id: int--><!--Device-SmartEntity-id: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## name

```TypeScript
name?: string
```

Name of the entity.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SmartEntity-name?: string--><!--Device-SmartEntity-name?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## thumbnail

```TypeScript
thumbnail?: image.PixelMap
```

Thumbnail to be displayed for the entity, for example a portrait avatar.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SmartEntity-thumbnail?: image.PixelMap--><!--Device-SmartEntity-thumbnail?: image.PixelMap-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
