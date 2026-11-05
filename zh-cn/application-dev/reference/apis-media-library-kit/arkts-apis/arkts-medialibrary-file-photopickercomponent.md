# @ohos.file.PhotoPickerComponent(PhotoPicker组件)

PhotoPickerComponent是图片选择器组件，应用可以在布局中嵌入图片选择器组件，通过此组件，应用无需申请权限，即可实现媒体文件选择功能。图片选择器组件支持宫格浏览和大图预览两种视图模式，提供单选和多选两种选择模式，支持相
 机入口让用户拍摄新照片，并支持动态照片的预览和选择。在用户选择媒体文件后，应用即可访问用户选中的图片或视频文件。仅包含读权限。

图片选择器组件不支持嵌套，且不应在该组件上覆盖设置overlay属性或更高层级组件，以免导致手势事件失效。

应用嵌入组件后，用户可直接在图片选择器组件中选择图片或视频文件。

> **说明：**
 >
 > - 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
 >
 > - 该组件不支持[同层渲染](../../../web/web-same-layer.md)。

## 属性

支持通用属性。

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AnimatorParams](arkts-medialibrary-file-photopickercomponent-animatorparams-c.md) | 进退大图动效参数。 |
| [BadgeConfig](arkts-medialibrary-file-photopickercomponent-badgeconfig-c.md) | 特殊角标配置项。 |
| [BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md) | 图片、视频相关信息。 |
| [ClickResult](arkts-medialibrary-file-photopickercomponent-clickresult-c.md) | 设置指定URI的资产是否被选中。 |
| [CompletedResult](arkts-medialibrary-file-photopickercomponent-completedresult-c.md) | Picker上次退出时现场的信息。 |
| [ItemInfo](arkts-medialibrary-file-photopickercomponent-iteminfo-c.md) | 继承自[BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md)，增加私有参数itemType。 |
| [MaxSelected](arkts-medialibrary-file-photopickercomponent-maxselected-c.md) | 最大选择数量。 |
| [PhotoBrowserInfo](arkts-medialibrary-file-photopickercomponent-photobrowserinfo-c.md) | 大图相关信息。 |
| [PickerController](arkts-medialibrary-file-photopickercomponent-pickercontroller-c.md) | 应用可通过PickerController向picker组件发送数据。 |
| [PickerError](arkts-medialibrary-file-photopickercomponent-pickererror-c.md) | 使用图片选择器组件发生错误时返回的错误的接口名称、错误码和错误描述。 |
| [PickerOptions](arkts-medialibrary-file-photopickercomponent-pickeroptions-c.md) | Picker配置选项，继承自[photoAccessHelper.BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md)。 |
| [PreselectedInfo](arkts-medialibrary-file-photopickercomponent-preselectedinfo-c.md) | 预选中的文件以及文件对应的图片选择器组件序号。 |
| [RecommendedLabel](arkts-medialibrary-file-photopickercomponent-recommendedlabel-c.md) | 用户在搜索页面点击的推荐标签。推荐标签要么是纯文本标签（只提供`text`）或智能实体标签（提供了`smartEntity`）。这两种情况是互斥的。 |
| [RecoveryResult](arkts-medialibrary-file-photopickercomponent-recoveryresult-c.md) | 恢复结果 |
| [SearchInfo](arkts-medialibrary-file-photopickercomponent-searchinfo-c.md) | 用于调用picker搜索能力的搜索信息。`text`和`smartEntityIds`中至少有一个必须为非空，否则将抛出错误。 |
| [SingleLineConfig](arkts-medialibrary-file-photopickercomponent-singlelineconfig-c.md) | 单行显示模式配置项。单行模式下，组件不提供打开大图浏览相关功能。组件不支持大图相关回调，PickerController不支持大图相关的接口，接口调用将无效。 |
| [SmartEntity](arkts-medialibrary-file-photopickercomponent-smartentity-c.md) | 推荐标签中的智能实体。 |
| [UnselectableItemInfo](arkts-medialibrary-file-photopickercomponent-unselectableiteminfo-c.md) | 被点击的不可选中的图片详情。 |
| [UpdatablePickerConfigs](arkts-medialibrary-file-photopickercomponent-updatablepickerconfigs-c.md) | 支持更新的图片选择器组件属性，为[PickerOptions](arkts-medialibrary-file-photopickercomponent-pickeroptions-c.md)的子集。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [PhotoPickerComponent](arkts-medialibrary-file-photopickercomponent-photopickercomponent-s.md) | PhotoPickerComponent({ pickerOptions?: PickerOptions, onSelect?: (uri: string) =&gt; void, onDeselect?: (uri: string) =&gt; void, onItemClicked?: (itemInfo: ItemInfo, clickType: ClickType) =&gt; boolean, onItemClickedNotify?: ItemClickedNotifyCallback, onEnterPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) =&gt; boolean, onExitPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) =&gt; boolean, onPickerControllerReady?: () =&gt; void, onPhotoBrowserChanged?: (browserItemInfo: BaseItemInfo) =&gt; boolean, onSelectedItemsDeleted?: ItemsDeletedCallback, onExceedMaxSelected?: ExceedMaxSelectedCallback, onCurrentAlbumDeleted?: CurrentAlbumDeletedCallback, onVideoPlayStateChanged?: videoPlayStateChangedCallback, pickerController: PickerController }) |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CurrentAlbumDeletedCallback](arkts-medialibrary-currentalbumdeletedcallback-t.md) | 当前相册被删除时的回调事件。 |
| [ErrorCallback](arkts-medialibrary-errorcallback-t.md) | 图片选择器组件产生错误时的回调。 |
| [ExceedMaxSelectedCallback](arkts-medialibrary-exceedmaxselectedcallback-t.md) | 选择达到最大选择数量之后再次点击勾选时的回调事件。 |
| [ItemClickedNotifyCallback](arkts-medialibrary-itemclickednotifycallback-t.md) | 用户在图片选择器组件中点击宫格产生的回调事件。 |
| [ItemsDeletedCallback](arkts-medialibrary-itemsdeletedcallback-t.md) | 已勾选的图片被删除时产生的回调事件。 |
| [MovingPhotoBadgeStateChangedCallback](arkts-medialibrary-movingphotobadgestatechangedcallback-t.md) | 用户在Picker组件中打开/关闭动态效果时的回调事件。 |
| [PhotoBrowserChangeStartCallback](arkts-medialibrary-photobrowserchangestartcallback-t.md) | 宫格视图进入到大图视图、大图浏览切换时产生的回调。 |
| [PhotoBrowserZoomCallback](arkts-medialibrary-photobrowserzoomcallback-t.md) | 图片选择器组件进入大图后，大图放大缩小时的回调。 |
| [PickerRecoveryCallback](arkts-medialibrary-pickerrecoverycallback-t.md) | onPickerRecovery事件的回调 |
| [PickerStateChangedCallback](arkts-medialibrary-pickerstatechangedcallback-t.md) | onPickerStateChanged事件的回调。 |
| [PinchGridSwitchedCallback](arkts-medialibrary-pinchgridswitchedcallback-t.md) | 用户在宫格组件内捏合时产生的回调事件。 |
| [RecommendedLabelClickedCallback](arkts-medialibrary-recommendedlabelclickedcallback-t.md) | onRequestLabelClicked事件的回调。 |
| [ScrollStopAtEndCallback](arkts-medialibrary-scrollstopatendcallback-t.md) | 表示用户滑动picker宫格页，当滚动停止并处于宫格内容结束位置时的回调事件类型。 |
| [ScrollStopAtStartCallback](arkts-medialibrary-scrollstopatstartcallback-t.md) | 表示用户滑动picker宫格页，当滚动停止并处于宫格内容开始位置时的回调事件类型。 |
| [UnselectableItemClickedCallback](arkts-medialibrary-unselectableitemclickedcallback-t.md) | 在picker宫格或大图预览界面，当不可选中的图片被点击时产生的回调。 |
| [videoPlayStateChangedCallback](arkts-medialibrary-videoplaystatechangedcallback-t.md) | 大图页视频播放状态改变时的回调事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BadgeType](arkts-medialibrary-file-photopickercomponent-badgetype-e.md) | 表示特殊角标类型的枚举。 |
| [ClickType](arkts-medialibrary-file-photopickercomponent-clicktype-e.md) | 点击操作的类型。 |
| [DataType](arkts-medialibrary-file-photopickercomponent-datatype-e.md) | 枚举，PickerController向picker组件发送数据的数据类型。 |
| [ItemDisplayRatio](arkts-medialibrary-file-photopickercomponent-itemdisplayratio-e.md) | 单行布局宫格显示宽高比模式，包括1:1和原图宽高比两种模式。 |
| [ItemType](arkts-medialibrary-file-photopickercomponent-itemtype-e.md) | 被点击item的类型。 |
| [MaxCountType](arkts-medialibrary-file-photopickercomponent-maxcounttype-e.md) | 最大选择数量的类型。 |
| [PhotoBrowserRange](arkts-medialibrary-file-photopickercomponent-photobrowserrange-e.md) | 打开大图浏览模式后，左右滑动切换浏览图片的范围。 |
| [PhotoBrowserUIElement](arkts-medialibrary-file-photopickercomponent-photobrowseruielement-e.md) | 大图页大图预览组件外其他UI元素。 |
| [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md) | Picker的颜色模式。 |
| [PickerOrientation](arkts-medialibrary-file-photopickercomponent-pickerorientation-e.md) | Picker宫格页面滑动预览的方向。 |
| [PickerState](arkts-medialibrary-file-photopickercomponent-pickerstate-e.md) | 选择器页面状态。 |
| [ReminderMode](arkts-medialibrary-file-photopickercomponent-remindermode-e.md) | 最大选择数量提示方式。 |
| [SaveMode](arkts-medialibrary-file-photopickercomponent-savemode-e.md) | 图片/视频保存模式。 |
| [SelectMode](arkts-medialibrary-file-photopickercomponent-selectmode-e.md) | 选择模式。 |
| [VideoPlayerState](arkts-medialibrary-file-photopickercomponent-videoplayerstate-e.md) | 视频播放状态。 |
