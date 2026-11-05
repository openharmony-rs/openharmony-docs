# PickerOptions

```TypeScript
export declare class PickerOptions extends photoAccessHelper.BaseSelectOptions
```

Picker配置选项，继承自[photoAccessHelper.BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md)。

**继承/实现关系：** PickerOptions extends [photoAccessHelper.BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md)

**起始版本：** 12

<!--Device-unnamed-export declare class PickerOptions extends photoAccessHelper.BaseSelectOptions--><!--Device-unnamed-export declare class PickerOptions extends photoAccessHelper.BaseSelectOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## appAlbumFilters

```TypeScript
appAlbumFilters?: Array<string>
```

仅显示与指定bundle name对应的相册内容。传入完整的bundle name字符串数组，需精确匹配应用包名。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-appAlbumFilters?: Array<string>--><!--Device-PickerOptions-appAlbumFilters?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## backgroundColor

```TypeScript
backgroundColor?: string
```

picker宫格页面背景色。

格式为8位十六进制颜色代码（#AARRGGBB）。前2位表示透明度，后6位表示RGB颜色值。

**注意：** 此格式与CSS标准的#RRGGBBAA格式不同，CSS标准中alpha在最后两位。

示例：'#FFFFFFFF'表示白色不透明背景；'#80FF0000'表示半透明红色背景。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-backgroundColor?: string--><!--Device-PickerOptions-backgroundColor?: string-End-->

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

<!--Device-PickerOptions-backgroundOpacity?: number--><!--Device-PickerOptions-backgroundOpacity?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## badgeConfig

```TypeScript
badgeConfig?: BadgeConfig
```

支持配置特殊角标显示。Picker目前仅支持一种类型的角标，详见[BadgeType](arkts-medialibrary-file-photopickercomponent-badgetype-e.md)。

**类型：** [BadgeConfig](arkts-medialibrary-file-photopickercomponent-badgeconfig-c.md)

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-badgeConfig?: BadgeConfig--><!--Device-PickerOptions-badgeConfig?: BadgeConfig-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## checkBoxColor

```TypeScript
checkBoxColor?: string
```

勾选框的背景色。

格式为8位十六进制颜色代码（#AARRGGBB）。前2位表示透明度，后6位表示RGB颜色值。

**注意：** 此格式与CSS标准的#RRGGBBAA格式不同，CSS标准中alpha在最后两位。

示例：'#FFFFFFFF'表示白色不透明背景；'#80FF0000'表示半透明红色背景。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-checkBoxColor?: string--><!--Device-PickerOptions-checkBoxColor?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## checkboxTextColor

```TypeScript
checkboxTextColor?: string
```

勾选框内文本颜色。

格式为8位十六进制颜色代码（#AARRGGBB）。前2位表示透明度，后6位表示RGB颜色值。

**注意：** 此格式与CSS标准的#RRGGBBAA格式不同，CSS标准中alpha在最后两位。

示例：'#FFFFFFFF'表示白色不透明背景；'#80FF0000'表示半透明红色背景。（该能力从API version 19开始支持，API version 19之前系统默认为白色）。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-checkboxTextColor?: string--><!--Device-PickerOptions-checkboxTextColor?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## contextRecoveryInfo

```TypeScript
contextRecoveryInfo?: photoAccessHelper.ContextRecoveryInfo
```

用于恢复上次退出时图片选择器组件现场的信息。默认为空，即不恢复上次现场。

**说明：** 需配合PickerController的[completed](arkts-medialibrary-file-photopickercomponent-pickercontroller-c.md#completed)方法使用，该方法返回的[CompletedResult](arkts-medialibrary-file-photopickercomponent-completedresult-c.md)中的contextRecoveryInfo可传入本参数实现现场恢复。

**类型：** [photoAccessHelper.ContextRecoveryInfo](arkts-medialibrary-photoaccesshelper-contextrecoveryinfo-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-contextRecoveryInfo?: photoAccessHelper.ContextRecoveryInfo--><!--Device-PickerOptions-contextRecoveryInfo?: photoAccessHelper.ContextRecoveryInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## edgeEffect

```TypeScript
edgeEffect?: EdgeEffect
```

Picker宫格页滑动到边缘处的滑动效果。

默认为[EdgeEffect.Spring](../../apis-arkui/arkts-apis/arkts-arkui-edgeeffect-e.md)。

**类型：** [EdgeEffect](../../apis-arkui/arkts-apis/arkts-arkui-edgeeffect-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-edgeEffect?: EdgeEffect--><!--Device-PickerOptions-edgeEffect?: EdgeEffect-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridEndOffset

```TypeScript
gridEndOffset?: number
```

组件宫格缩略图最后一行与组件底部的预留空间。默认值0，单位vp。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-gridEndOffset?: number--><!--Device-PickerOptions-gridEndOffset?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridMargin

```TypeScript
gridMargin?: Margin
```

设置组件宫格页margin。

**类型：** [Margin](../../apis-arkui/arkts-apis/arkts-arkui-margin-t.md)

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-gridMargin?: Margin--><!--Device-PickerOptions-gridMargin?: Margin-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridStartOffset

```TypeScript
gridStartOffset?: number
```

组件宫格缩略图第一行与组件顶部的预留空间。当不设置该参数时，默认值0，单位vp。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-gridStartOffset?: number--><!--Device-PickerOptions-gridStartOffset?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isRepeatSelectSupported

```TypeScript
isRepeatSelectSupported?: boolean
```

是否支持单张图片重复选择。true表示支持，false表示不支持。默认值为false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-isRepeatSelectSupported?: boolean--><!--Device-PickerOptions-isRepeatSelectSupported?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSlidingSelectionSupported

```TypeScript
isSlidingSelectionSupported?: boolean
```

是否支持滑动多选，true表示支持，false表示不支持。当不设置该参数时，默认值为false。重复选择场景不支持滑动多选。

从API版本26.0.0开始，select方法支持Car设备，但isSlidingSelectionSupported属性不支持Car设备，所以在Car设备上配置本属性不会生效。

**类型：** boolean

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-isSlidingSelectionSupported?: boolean--><!--Device-PickerOptions-isSlidingSelectionSupported?: boolean-End-->

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

<!--Device-PickerOptions-isSlidingSupported?: boolean--><!--Device-PickerOptions-isSlidingSupported?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxPhotoSelectNumber

```TypeScript
maxPhotoSelectNumber?: number
```

图片最大的选择数量。取值范围[1, 500]，默认为500。单位：个。

受到最大选择总数[BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md).maxSelectNumber的限制。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-maxPhotoSelectNumber?: number--><!--Device-PickerOptions-maxPhotoSelectNumber?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxSelectedReminderMode

```TypeScript
maxSelectedReminderMode?: ReminderMode
```

选择数量达到最大时的提示方式。包括弹toast提示、不提示以及蒙层提示。当不设置该参数时，默认为弹toast提示。

**类型：** [ReminderMode](arkts-medialibrary-file-photopickercomponent-remindermode-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-maxSelectedReminderMode?: ReminderMode--><!--Device-PickerOptions-maxSelectedReminderMode?: ReminderMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxVideoSelectNumber

```TypeScript
maxVideoSelectNumber?: number
```

视频最大的选择数量。取值范围[1, 500]，默认为500。单位：个。

受到最大选择总数[BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md).maxSelectNumber的限制。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-maxVideoSelectNumber?: number--><!--Device-PickerOptions-maxVideoSelectNumber?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## orientation

```TypeScript
orientation?: PickerOrientation
```

宫格页面滑动预览方向，包括水平和竖直两个方向。

当不设置该参数时，默认为竖直方向。

当需要横向滑动浏览媒体文件时应设置为HORIZONTAL（水平方向）。

当需要纵向滑动浏览时使用VERTICAL（竖直方向）或不填写此参数。

该能力从API version 20开始支持，API version 20之前系统默认为竖直方向。

**类型：** [PickerOrientation](arkts-medialibrary-file-photopickercomponent-pickerorientation-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-orientation?: PickerOrientation--><!--Device-PickerOptions-orientation?: PickerOrientation-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserBackgroundColorMode

```TypeScript
photoBrowserBackgroundColorMode?: PickerColorMode
```

大图背景颜色。包括跟随系统、浅色模式以及深色模式。当不设置该参数时，默认为跟随系统。

**类型：** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-photoBrowserBackgroundColorMode?: PickerColorMode--><!--Device-PickerOptions-photoBrowserBackgroundColorMode?: PickerColorMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserCheckboxPosition

```TypeScript
photoBrowserCheckboxPosition?: [number, number]
```

设置大图页checkbox的位置。第一个参数为X方向偏移量，第二个参数为Y方向偏移量。传参范围[0, 1]，代表距离组件左上角0%-100%的偏移量。当不设置该参数时，默认值为[0, 0]。

**类型：** [number, number]

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-photoBrowserCheckboxPosition?: [number, number]--><!--Device-PickerOptions-photoBrowserCheckboxPosition?: [number, number]-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoBrowserMargin

```TypeScript
photoBrowserMargin?: Margin
```

设置组件大图页margin。

**类型：** [Margin](../../apis-arkui/arkts-apis/arkts-arkui-margin-t.md)

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-photoBrowserMargin?: Margin--><!--Device-PickerOptions-photoBrowserMargin?: Margin-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## pickerIndex

```TypeScript
pickerIndex?: number
```

通过设置唯一序号来区分不同的pickerComponent。取值范围[-1, +∞)，默认值为-1，不做区分。当应用中同时使用多个图片选择器组件且需要区分不同组件时应设置不同的唯一序号。

配合preselectedInfos进行数据回显时，需设置pickerIndex并在[PreselectedInfo](arkts-medialibrary-file-photopickercomponent-preselectedinfo-c.md)中的preselectablePickerIndex进行匹配，以实现回显到指定组件。

**类型：** number

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-pickerIndex?: number--><!--Device-PickerOptions-pickerIndex?: number-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## preselectedInfos

```TypeScript
preselectedInfos?: Array<PreselectedInfo>
```

支持在指定pickerIndex的图片选择器组件中回显用户预选择的数据。

**类型：** Array&lt;[PreselectedInfo](arkts-medialibrary-file-photopickercomponent-preselectedinfo-c.md)&gt;

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-preselectedInfos?: Array<PreselectedInfo>--><!--Device-PickerOptions-preselectedInfos?: Array<PreselectedInfo>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## selectMode

```TypeScript
selectMode?: SelectMode
```

图片选择器组件选择模式，包括多选和单选。

当不设置该参数时，默认为多选。

当仅需要用户选择单个文件时应设置为SINGLE_SELECT（单选模式）。

当需要用户选择多个文件时使用MULTI_SELECT（多选模式）或不填写此参数。

**类型：** [SelectMode](arkts-medialibrary-file-photopickercomponent-selectmode-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-selectMode?: SelectMode--><!--Device-PickerOptions-selectMode?: SelectMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## singleLineConfig

```TypeScript
singleLineConfig?: SingleLineConfig
```

设置组件宫格页单行显示模式。单行模式下，组件不提供打开大图浏览相关功能。组件不支持onEnterPhotoBrowser、onExitPhotoBrowser等大图浏览回调，PickerController不支持setPhotoBrowserItem、exitPhotoBrowser等大图浏览接口，接口调用将无效。

**类型：** [SingleLineConfig](arkts-medialibrary-file-photopickercomponent-singlelineconfig-c.md)

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-singleLineConfig?: SingleLineConfig--><!--Device-PickerOptions-singleLineConfig?: SingleLineConfig-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uiComponentColorMode

```TypeScript
uiComponentColorMode?: PickerColorMode
```

Picker的颜色模式。Picker宫格界面除背景色之外其他组件的深浅色风格，包括搜索框、相机入口、安全使用图库提示组件、推荐气泡等组件，一般与backgroundColor配合使用。当不设置该参数时，默认为PickerColorMode.AUTO，跟随系统深浅色切换。

该属性一般设置PickerColorMode.LIGHT时不与深颜色的backgroundColor搭配；设置PickerColorMode.DARK时不与浅颜色的backgroundColor搭配，否则会出现组件背景或文字无法看清楚的问题。

**类型：** [PickerColorMode](arkts-medialibrary-file-photopickercomponent-pickercolormode-e.md)

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-PickerOptions-uiComponentColorMode?: PickerColorMode--><!--Device-PickerOptions-uiComponentColorMode?: PickerColorMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
