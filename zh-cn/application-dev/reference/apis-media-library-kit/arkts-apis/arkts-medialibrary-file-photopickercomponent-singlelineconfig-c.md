# SingleLineConfig

```TypeScript
export declare class SingleLineConfig
```

单行显示模式配置项。单行模式下，组件不提供打开大图浏览相关功能。组件不支持大图相关回调，PickerController不支持大图相关的接口，接口调用将无效。

**起始版本：** 20

<!--Device-unnamed-export declare class SingleLineConfig--><!--Device-unnamed-export declare class SingleLineConfig-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## itemBorderRadius

```TypeScript
itemBorderRadius?: Length | BorderRadiuses | LocalizedBorderRadiuses
```

宫格圆角属性。

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) &#124; [BorderRadiuses](../../apis-arkui/arkts-apis/arkts-arkui-borderradiuses-t.md) &#124; [LocalizedBorderRadiuses](../../apis-arkui/arkts-apis/arkts-arkui-localizedborderradiuses-i.md)

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-SingleLineConfig-itemBorderRadius?: Length | BorderRadiuses | LocalizedBorderRadiuses--><!--Device-SingleLineConfig-itemBorderRadius?: Length | BorderRadiuses | LocalizedBorderRadiuses-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## itemDisplayRatio

```TypeScript
itemDisplayRatio?: ItemDisplayRatio
```

宫格显示宽高比，支持1:1，原图宽高比两种模式，默认为宽高比1:1显示。

**类型：** [ItemDisplayRatio](arkts-medialibrary-file-photopickercomponent-itemdisplayratio-e.md)

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-SingleLineConfig-itemDisplayRatio?: ItemDisplayRatio--><!--Device-SingleLineConfig-itemDisplayRatio?: ItemDisplayRatio-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## itemGap

```TypeScript
itemGap?: Length
```

宫格间距。

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-SingleLineConfig-itemGap?: Length--><!--Device-SingleLineConfig-itemGap?: Length-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
