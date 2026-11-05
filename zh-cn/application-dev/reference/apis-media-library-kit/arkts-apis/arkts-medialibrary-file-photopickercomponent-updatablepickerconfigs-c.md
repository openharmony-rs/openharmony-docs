# UpdatablePickerConfigs

```TypeScript
export declare class UpdatablePickerConfigs
```

支持更新的图片选择器组件属性，为[PickerOptions](arkts-medialibrary-file-photopickercomponent-pickeroptions-c.md)的子集。

**起始版本：** 22

<!--Device-unnamed-export declare class UpdatablePickerConfigs--><!--Device-unnamed-export declare class UpdatablePickerConfigs-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## appAlbumFilters

```TypeScript
appAlbumFilters?: Array<string>
```

仅显示与指定bundle name对应的相册内容。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-appAlbumFilters?: Array<string>--><!--Device-UpdatablePickerConfigs-appAlbumFilters?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## autoPlayScenes

```TypeScript
autoPlayScenes?: Array<photoAccessHelper.AutoPlayScene>
```

设置动态照片自动播放场景。最多支持配置2个自动播放场景，超出时仅取前2个，多余的会自动忽略。

**类型：** Array&lt;[photoAccessHelper.AutoPlayScene](arkts-medialibrary-photoaccesshelper-autoplayscene-c.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-autoPlayScenes?: Array<photoAccessHelper.AutoPlayScene>--><!--Device-UpdatablePickerConfigs-autoPlayScenes?: Array<photoAccessHelper.AutoPlayScene>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## backgroundColor

```TypeScript
backgroundColor?: string
```

图片选择器组件宫格页面背景色。格式为8位十六进制颜色代码。前2位表示透明度，后6位表示RGB颜色值。

示例：'#FFFFFFFF'表示白色不透明背景。

**类型：** string

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-backgroundColor?: string--><!--Device-UpdatablePickerConfigs-backgroundColor?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## backgroundOpacity

```TypeScript
backgroundOpacity?: number
```

支持配置图片选择器组件背景透明度。取值范围为[0, 1]，0表示完全透明，1表示完全不透明。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-backgroundOpacity?: number--><!--Device-UpdatablePickerConfigs-backgroundOpacity?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## checkBoxColor

```TypeScript
checkBoxColor?: string
```

勾选框的背景色。

格式为8位十六进制颜色代码。

**类型：** string

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-checkBoxColor?: string--><!--Device-UpdatablePickerConfigs-checkBoxColor?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## checkboxTextColor

```TypeScript
checkboxTextColor?: string
```

勾选框内文本颜色。

格式为8位十六进制颜色代码。

**类型：** string

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-checkboxTextColor?: string--><!--Device-UpdatablePickerConfigs-checkboxTextColor?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## edgeEffect

```TypeScript
edgeEffect?: EdgeEffect
```

图片选择器组件宫格页滑动到边缘处的滑动效果。

默认为[EdgeEffect.Spring](../../apis-arkui/arkts-apis/arkts-arkui-edgeeffect-e.md)。

**类型：** [EdgeEffect](../../apis-arkui/arkts-apis/arkts-arkui-edgeeffect-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-edgeEffect?: EdgeEffect--><!--Device-UpdatablePickerConfigs-edgeEffect?: EdgeEffect-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridMargin

```TypeScript
gridMargin?: Margin
```

设置组件宫格页边距。

**类型：** [Margin](../../apis-arkui/arkts-apis/arkts-arkui-margin-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-gridMargin?: Margin--><!--Device-UpdatablePickerConfigs-gridMargin?: Margin-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isRepeatSelectSupported

```TypeScript
isRepeatSelectSupported?: boolean
```

是否支持单张图片重复选择。

true表示支持，false表示不支持。当不设置该参数时，默认为false。

**类型：** boolean

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-isRepeatSelectSupported?: boolean--><!--Device-UpdatablePickerConfigs-isRepeatSelectSupported?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSlidingSupported

```TypeScript
isSlidingSupported?: boolean
```

是否屏蔽图片选择器组件的滚动。true表示不屏蔽滚动事件，响应用户滚动。false表示屏蔽滚动事件，不响应用户滚动。

默认为true。

**注意：**

当isSlidingSupported设为false时，宫格缩略图将不响应用户点击查看大图的操作，onEnterPhotoBrowser等大图浏览相关回调将不会触发。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-isSlidingSupported?: boolean--><!--Device-UpdatablePickerConfigs-isSlidingSupported?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxPhotoSelectNumber

```TypeScript
maxPhotoSelectNumber?: number
```

图片最大的选择数量（单位：个），取值范围[0, 500]，受到最大选择总数的限制。默认为500。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-maxPhotoSelectNumber?: number--><!--Device-UpdatablePickerConfigs-maxPhotoSelectNumber?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxSelectNumber

```TypeScript
maxSelectNumber?: number
```

选择媒体文件数量的最大值（单位：个），取值范围[0, 500]，若不设置则默认为50。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-maxSelectNumber?: number--><!--Device-UpdatablePickerConfigs-maxSelectNumber?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxVideoSelectNumber

```TypeScript
maxVideoSelectNumber?: number
```

视频最大的选择数量（单位：个），取值范围[0, 500]，受到系统中所有媒体文件最大选择总数的限制。默认为500。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-maxVideoSelectNumber?: number--><!--Device-UpdatablePickerConfigs-maxVideoSelectNumber?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mimeType

```TypeScript
mimeType?: photoAccessHelper.PhotoViewMIMETypes
```

可选择的媒体文件类型。

若无此参数，则默认为图片和视频类型。

**注意：**

当配置mimeTypeFilter参数时，mimeType的配置自动失效。

**类型：** [photoAccessHelper.PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-mimeType?: photoAccessHelper.PhotoViewMIMETypes--><!--Device-UpdatablePickerConfigs-mimeType?: photoAccessHelper.PhotoViewMIMETypes-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mimeTypeFilter

```TypeScript
mimeTypeFilter?: photoAccessHelper.MimeTypeFilter
```

文件类型的过滤配置，支持指定多个类型过滤。

- 当配置mimeTypeFilter参数时，mimeType的配置自动失效。  
- 当配置该参数时，仅显示配置过滤类型对应的媒体文件，建议提示用户仅支持选择指定类型的图片/视频。

**类型：** [photoAccessHelper.MimeTypeFilter](arkts-medialibrary-photoaccesshelper-mimetypefilter-c.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-mimeTypeFilter?: photoAccessHelper.MimeTypeFilter--><!--Device-UpdatablePickerConfigs-mimeTypeFilter?: photoAccessHelper.MimeTypeFilter-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserBackgroundColorMode

```TypeScript
photoBrowserBackgroundColorMode?: PickerColorMode
```

大图背景颜色。

包括跟随系统、浅色模式以及深色模式，默认为跟随系统。

**类型：** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-photoBrowserBackgroundColorMode?: PickerColorMode--><!--Device-UpdatablePickerConfigs-photoBrowserBackgroundColorMode?: PickerColorMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserMargin

```TypeScript
photoBrowserMargin?: Margin
```

设置组件大图页边距。

**类型：** [Margin](../../apis-arkui/arkts-apis/arkts-arkui-margin-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-photoBrowserMargin?: Margin--><!--Device-UpdatablePickerConfigs-photoBrowserMargin?: Margin-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## preselectedUris

```TypeScript
preselectedUris?: Array<string>
```

预选择图片的URI列表。数组长度受[BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md). maxSelectNumber、[BaseSelectOptions](arkts-medialibrary-photoaccesshelper-photoselectoptions-c.md). maxPhotoSelectNumber和[BaseSelectOptions](arkts-medialibrary-photoaccesshelper-photoselectoptions-c.md). maxVideoSelectNumber共同限制，取值范围[0, 500]，默认50，否则超出部分不生效。若不配置，则默认不预选择任何图片。

**类型：** Array&lt;string&gt;

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-preselectedUris?: Array<string>--><!--Device-UpdatablePickerConfigs-preselectedUris?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## selectMode

```TypeScript
selectMode?: SelectMode
```

图片选择器组件选择模式。

包括多选和单选，默认为多选。

**类型：** [SelectMode](arkts-medialibrary-file-photopickercomponent-selectmode-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-selectMode?: SelectMode--><!--Device-UpdatablePickerConfigs-selectMode?: SelectMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## singleSelectionMode

```TypeScript
singleSelectionMode?: photoAccessHelper.SingleSelectionMode
```

单选模式类型。默认为大图预览模式（SingleSelectionMode.BROWSER_MODE）。

**类型：** [photoAccessHelper.SingleSelectionMode](arkts-medialibrary-photoaccesshelper-singleselectionmode-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-singleSelectionMode?: photoAccessHelper.SingleSelectionMode--><!--Device-UpdatablePickerConfigs-singleSelectionMode?: photoAccessHelper.SingleSelectionMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uiComponentColorMode

```TypeScript
uiComponentColorMode?: PickerColorMode
```

Picker UI组件的颜色模式。

图片选择器组件宫格界面除背景色之外其他组件的深浅色风格，包括搜索框、相机入口、安全使用图库提示组件、推荐气泡等组件，一般与backgroundColor配合使用。默认为PickerColorMode.AUTO，跟随系统深浅色切换。

该属性设置为PickerColorMode.LIGHT时，一般不与深颜色的backgroundColor搭配；设置为PickerColorMode.DARK时，不与浅颜色的backgroundColor搭配，避免出现组件背景或文字无法看清楚的问题。

**类型：** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-UpdatablePickerConfigs-uiComponentColorMode?: PickerColorMode--><!--Device-UpdatablePickerConfigs-uiComponentColorMode?: PickerColorMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
