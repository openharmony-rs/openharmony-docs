# PhotoPickerComponent

```TypeScript
export declare struct PhotoPickerComponent
```

PhotoPickerComponent({ pickerOptions?: PickerOptions, onSelect?: (uri: string) =&gt; void, onDeselect?: (uri: string) =&gt; void, onItemClicked?: (itemInfo: ItemInfo, clickType: ClickType) =&gt; boolean, onItemClickedNotify?: ItemClickedNotifyCallback, onEnterPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) =&gt; boolean, onExitPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) =&gt; boolean, onPickerControllerReady?: () =&gt; void, onPhotoBrowserChanged?: (browserItemInfo: BaseItemInfo) =&gt; boolean, onSelectedItemsDeleted?: ItemsDeletedCallback, onExceedMaxSelected?: ExceedMaxSelectedCallback, onCurrentAlbumDeleted?: CurrentAlbumDeletedCallback, onVideoPlayStateChanged?: videoPlayStateChangedCallback, pickerController: PickerController })

应用可以在布局中嵌入图片选择器组件，通过此组件，应用无需申请权限，即可访问公共目录中的图片或视频文件。

> **说明：** 
> 
> - 如果当前图片选择器组件嵌套在Tabs组件中使用，Tabs组件的左右滑动会与图片选择大图界面的左右滑动切换手势发生冲突。
> 
> -可在进退大图的回调中设置Tabs组件是否支持滑动来规避，该问题将在后续版本修复。

**起始版本：** 12

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct PhotoPickerComponent--><!--Device-unnamed-export declare struct PhotoPickerComponent-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## build

```TypeScript
build(): void
```

**起始版本：** 12

**装饰器类型：** @Builder

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-build(): void--><!--Device-PhotoPickerComponent-build(): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onCurrentAlbumDeleted

```TypeScript
onCurrentAlbumDeleted?: CurrentAlbumDeletedCallback
```

当前相册被删除时产生的回调。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onCurrentAlbumDeleted?: CurrentAlbumDeletedCallback--><!--Device-PhotoPickerComponent-onCurrentAlbumDeleted?: CurrentAlbumDeletedCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onDeselect

```TypeScript
onDeselect?: (uri: string) => void
```

用户在Picker组件中取消勾选图片时产生的回调事件，同时也会将图片uri报给应用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onDeselect?: (uri: string) => void--><!--Device-PhotoPickerComponent-onDeselect?: (uri: string) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 |  |

## onEnterPhotoBrowser

```TypeScript
onEnterPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean
```

点击进入大图时产生的回调事件，将大图相关信息报给应用。不对返回值做特殊处理。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onEnterPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean--><!--Device-PhotoPickerComponent-onEnterPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoBrowserInfo | [PhotoBrowserInfo](arkts-medialibrary-file-photopickercomponent-photobrowserinfo-c.md) | 是 |  |

## onError

```TypeScript
onError?: ErrorCallback
```

使用PhotoPickerComponent组件发生错误时产生的回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onError?: ErrorCallback--><!--Device-PhotoPickerComponent-onError?: ErrorCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onExceedMaxSelected

```TypeScript
onExceedMaxSelected?: ExceedMaxSelectedCallback
```

选择达到最大选择数量（最大图片选择数量或者是最大视频选择数量亦或是总的最大选择数量）之后再次点击勾选时产生的回调

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onExceedMaxSelected?: ExceedMaxSelectedCallback--><!--Device-PhotoPickerComponent-onExceedMaxSelected?: ExceedMaxSelectedCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onExitPhotoBrowser

```TypeScript
onExitPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean
```

退出大图时产生的回调事件，将大图相关信息报给应用。不对返回值做特殊处理。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onExitPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean--><!--Device-PhotoPickerComponent-onExitPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoBrowserInfo | [PhotoBrowserInfo](arkts-medialibrary-file-photopickercomponent-photobrowserinfo-c.md) | 是 |  |

## onItemClicked

```TypeScript
onItemClicked?: (itemInfo: ItemInfo, clickType: ClickType) => boolean
```

用户在picker组件中点击宫格产生的回调事件。点击图片（缩略图宫格）时，返回值为true则勾选此图片，否则不响应勾选，URI不授权；点击相机宫格，返回值为true则拉起系统相机，否则不拉起相机，由应用自行处理。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onItemClicked?: (itemInfo: ItemInfo, clickType: ClickType) => boolean--><!--Device-PhotoPickerComponent-onItemClicked?: (itemInfo: ItemInfo, clickType: ClickType) => boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemInfo | [ItemInfo](arkts-medialibrary-file-photopickercomponent-iteminfo-c.md) | 是 |  |
| clickType | [ClickType](arkts-medialibrary-file-photopickercomponent-clicktype-e.md) | 是 |  |

## onItemClickedNotify

```TypeScript
onItemClickedNotify?: ItemClickedNotifyCallback
```

用户在picker组件中点击宫格产生的回调事件。应用可执行自身是否选中逻辑，需要配合addData方法一同使用，通过SET_ITEM_CLICK_RESULT进行选中或不选中。若未设置选中结果，在2秒或PhotoPicker被关闭时取消授权。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onItemClickedNotify?: ItemClickedNotifyCallback--><!--Device-PhotoPickerComponent-onItemClickedNotify?: ItemClickedNotifyCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onMovingPhotoBadgeStateChanged

```TypeScript
onMovingPhotoBadgeStateChanged?: MovingPhotoBadgeStateChangedCallback
```

用户在Picker组件中打开/关闭动态效果时产生的回调。将图片uri和动态照片状态报给应用。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onMovingPhotoBadgeStateChanged?: MovingPhotoBadgeStateChangedCallback--><!--Device-PhotoPickerComponent-onMovingPhotoBadgeStateChanged?: MovingPhotoBadgeStateChangedCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onPhotoBrowserChanged

```TypeScript
onPhotoBrowserChanged?: (browserItemInfo: BaseItemInfo) => boolean
```

大图左右滑动时产生的回调事件，将大图相关信息报给应用。仅在多选模式下生效。不对返回值做特殊处理。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onPhotoBrowserChanged?: (browserItemInfo: BaseItemInfo) => boolean--><!--Device-PhotoPickerComponent-onPhotoBrowserChanged?: (browserItemInfo: BaseItemInfo) => boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| browserItemInfo | [BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md) | 是 |  |

## onPhotoBrowserChangeStart

```TypeScript
onPhotoBrowserChangeStart?: PhotoBrowserChangeStartCallback
```

宫格视图进入到大图视图、大图浏览切换时产生的回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onPhotoBrowserChangeStart?: PhotoBrowserChangeStartCallback--><!--Device-PhotoPickerComponent-onPhotoBrowserChangeStart?: PhotoBrowserChangeStartCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onPhotoBrowserZoom

```TypeScript
onPhotoBrowserZoom?: PhotoBrowserZoomCallback
```

大图浏览时，缩放比例发生变化时的回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onPhotoBrowserZoom?: PhotoBrowserZoomCallback--><!--Device-PhotoPickerComponent-onPhotoBrowserZoom?: PhotoBrowserZoomCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onPickerControllerReady

```TypeScript
onPickerControllerReady?: () => void
```

当pickerController可用时产生的回调事件。调用PickerController相关接口需在该回调后才能生效。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onPickerControllerReady?: () => void--><!--Device-PhotoPickerComponent-onPickerControllerReady?: () => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onPickerRecovery

```TypeScript
onPickerRecovery?: PickerRecoveryCallback
```

当照片拾取器恢复之前的网格状态时的回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onPickerRecovery?: PickerRecoveryCallback--><!--Device-PhotoPickerComponent-onPickerRecovery?: PickerRecoveryCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onPickerStateChanged

```TypeScript
onPickerStateChanged?: PickerStateChangedCallback
```

当选择器状态在默认状态和搜索状态之间更改时调用。初始状态为PickerState.DEFAULT。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onPickerStateChanged?: PickerStateChangedCallback--><!--Device-PhotoPickerComponent-onPickerStateChanged?: PickerStateChangedCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onPinchGridSwitched

```TypeScript
onPinchGridSwitched?: PinchGridSwitchedCallback
```

宫格捏合时产生的回调事件。仅在GridPinchModeType配置为FULL_FUNCTION_GRID时被触发。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onPinchGridSwitched?: PinchGridSwitchedCallback--><!--Device-PhotoPickerComponent-onPinchGridSwitched?: PinchGridSwitchedCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onRecommendedLabelClicked

```TypeScript
onRecommendedLabelClicked?: RecommendedLabelClickedCallback
```

当用户在搜索页面点击推荐标签时调用。标签可以是纯文本标签，也可以是智能实体标签。第三方应用可以使用回调payload来渲染自己的搜索框。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onRecommendedLabelClicked?: RecommendedLabelClickedCallback--><!--Device-PhotoPickerComponent-onRecommendedLabelClicked?: RecommendedLabelClickedCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onScrollStopAtEnd

```TypeScript
onScrollStopAtEnd?: ScrollStopAtEndCallback
```

用户在Picker组件滑动停止、处于宫格内容结束位置时的回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onScrollStopAtEnd?: ScrollStopAtEndCallback--><!--Device-PhotoPickerComponent-onScrollStopAtEnd?: ScrollStopAtEndCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onScrollStopAtStart

```TypeScript
onScrollStopAtStart?: ScrollStopAtStartCallback
```

用户在Picker组件滑动停止、处于宫格内容起始位置时的回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onScrollStopAtStart?: ScrollStopAtStartCallback--><!--Device-PhotoPickerComponent-onScrollStopAtStart?: ScrollStopAtStartCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onSelect

```TypeScript
onSelect?: (uri: string) => void
```

用户在Picker组件中勾选图片时产生的回调事件，将图片uri报给应用

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onSelect?: (uri: string) => void--><!--Device-PhotoPickerComponent-onSelect?: (uri: string) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 |  |

## onSelectedItemsDeleted

```TypeScript
onSelectedItemsDeleted?: ItemsDeletedCallback
```

已勾选的图片被删除时产生的回调，并将被删除图片的相关信息回调给应用。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onSelectedItemsDeleted?: ItemsDeletedCallback--><!--Device-PhotoPickerComponent-onSelectedItemsDeleted?: ItemsDeletedCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onUnselectableItemClicked

```TypeScript
onUnselectableItemClicked?: UnselectableItemClickedCallback
```

点击不可选项时的回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onUnselectableItemClicked?: UnselectableItemClickedCallback--><!--Device-PhotoPickerComponent-onUnselectableItemClicked?: UnselectableItemClickedCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## onVideoPlayStateChanged

```TypeScript
onVideoPlayStateChanged?: videoPlayStateChangedCallback
```

大图页视频播放状态改变时回调。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-onVideoPlayStateChanged?: videoPlayStateChangedCallback--><!--Device-PhotoPickerComponent-onVideoPlayStateChanged?: videoPlayStateChangedCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## pickerController

```TypeScript
pickerController: PickerController
```

应用可通过PickerController向Picker组件发送数据。

**类型：** [PickerController](arkts-medialibrary-file-photopickercomponent-pickercontroller-c.md)

**起始版本：** 12

**装饰器类型：** @ObjectLink

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-pickerController: PickerController--><!--Device-PhotoPickerComponent-pickerController: PickerController-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## pickerOptions

```TypeScript
pickerOptions?: PickerOptions
```

picker配置参数信息

**类型：** [PickerOptions](arkts-medialibrary-file-photopickercomponent-pickeroptions-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PhotoPickerComponent-pickerOptions?: PickerOptions--><!--Device-PhotoPickerComponent-pickerOptions?: PickerOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
