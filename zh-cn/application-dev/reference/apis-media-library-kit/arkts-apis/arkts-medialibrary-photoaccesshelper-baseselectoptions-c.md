# BaseSelectOptions

图库选择选项基类。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-export class BaseSelectOptions--><!--Device-photoAccessHelper-export class BaseSelectOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## MIMEType

```TypeScript
MIMEType?: PhotoViewMIMETypes
```

可选择的媒体文件类型，若无此参数，则默认为图片和视频类型。

**类型：** PhotoViewMIMETypes

**起始版本：** 26.0.0

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-MIMEType?: PhotoViewMIMETypes--><!--Device-BaseSelectOptions-MIMEType?: PhotoViewMIMETypes-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## assetCompatibleCapability

```TypeScript
assetCompatibleCapability?: AssetCompatibleCapability
```

资产兼容性能力配置。

**类型：** [AssetCompatibleCapability](arkts-medialibrary-photoaccesshelper-assetcompatiblecapability-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-assetCompatibleCapability?: AssetCompatibleCapability--><!--Device-BaseSelectOptions-assetCompatibleCapability?: AssetCompatibleCapability-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## assetFilter

```TypeScript
assetFilter?: Array<OperationItem>
```

媒体资产过滤器，长度限制为50个，超出取前50个。 **注意：** 1. 当使用该过滤器时，其他过滤器会失效。 2. 当配置多个条件时，过滤条件前后需要配置英文括号，否则可能和内部过滤项冲突。

**类型：** Array&lt;[OperationItem](arkts-medialibrary-photoaccesshelper-operationitem-c.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-assetFilter?: Array<OperationItem>--><!--Device-BaseSelectOptions-assetFilter?: Array<OperationItem>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## autoPlayScenes

```TypeScript
autoPlayScenes?: Array<AutoPlayScene>
```

设置动态照片播放模式。长度限制为2个，超出取前2个，多余的会自动忽略。

**类型：** Array&lt;[AutoPlayScene](arkts-medialibrary-photoaccesshelper-autoplayscene-c.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-autoPlayScenes?: Array<AutoPlayScene>--><!--Device-BaseSelectOptions-autoPlayScenes?: Array<AutoPlayScene>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## combinedMediaTypeFilter

```TypeScript
combinedMediaTypeFilter?: Array<string>
```

将过滤条件配置为字符串数组，支持多种类型组合。 字符串格式如下：`photoType | photoSubType1,photoSubType2, … | mimeType1,mimeType2, …`。 - 第1段指定1个photoType，固定为image（图片）或video（视频）。 - 第2段指定1~N个photoSubType，多个photoSubType之间使用逗号隔开，之间为“或（OR）”的逻辑取并集；N目前支持最大为1；可选的PhotoSubType包括movingPhoto或“*”（忽略）。 - 第3段指定1~N个mimeType，多个mimeType之间使用逗号隔开，之间为“或（OR）”的逻辑取并集；N最大为10，格式类似于 [MimeTypeFilter](arkts-medialibrary-photoaccesshelper-mimetypefilter-c.md)。 三段过滤的组合取交集处理。 支持“非”的逻辑。对于需要排除的类型，进行加括号的方式进行标识；一个string最多可使用1个括号。 当应用配置的过滤条件string不满足上述规格时，过滤结果为空。 配置该参数时，仅取数组前三个参数进行处理，MIMEType、mimeTypeFilter参数自动失效。 **原子化服务API：** 从API version 20开始支持在原子化服务中使用。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-combinedMediaTypeFilter?: Array<string>--><!--Device-BaseSelectOptions-combinedMediaTypeFilter?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## fileSizeFilter

```TypeScript
fileSizeFilter?: FileSizeFilter
```

可选择媒体文件大小的过滤配置。 配置该参数时，仅显示配置文件大小范围的媒体文件，建议提示用户仅支持选择指定大小的图片/视频。

**类型：** [FileSizeFilter](arkts-medialibrary-photoaccesshelper-filesizefilter-c.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-fileSizeFilter?: FileSizeFilter--><!--Device-BaseSelectOptions-fileSizeFilter?: FileSizeFilter-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## globalMovingPhotoState

```TypeScript
globalMovingPhotoState?: MovingPhotoBadgeStateType
```

设置全局动态照片的效果，当前仅支持MOVING_PHOTO_ENABLED和MOVING_PHOTO_DISABLED。默认为MOVING_PHOTO_ENABLED。

**类型：** [MovingPhotoBadgeStateType](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-globalMovingPhotoState?: MovingPhotoBadgeStateType--><!--Device-BaseSelectOptions-globalMovingPhotoState?: MovingPhotoBadgeStateType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridPinchMode

```TypeScript
gridPinchMode?: GridPinchMode
```

picker内宫格捏合模式。

**类型：** [GridPinchMode](arkts-medialibrary-photoaccesshelper-gridpinchmode-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-gridPinchMode?: GridPinchMode--><!--Device-BaseSelectOptions-gridPinchMode?: GridPinchMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isMovingPhotoBadgeShown

```TypeScript
isMovingPhotoBadgeShown?: boolean
```

是否在大图浏览模式下展示动态照片图标，true表示展示，false表示不展示，默认为false。 若设置为true，[Photoselectresult](arkts-medialibrary-photoaccesshelper-photoselectresult-c.md)返回movingPhotoBadgeStates数组，动态照片默认返回状态为 [MOVING_PHOTO_ENABLED](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md)。 **注意：** 必须同时使用isMovingPhotoBadgeShown和MovingPhotoBadgeStateType判断照片是否是动态照片。

**类型：** boolean

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-isMovingPhotoBadgeShown?: boolean--><!--Device-BaseSelectOptions-isMovingPhotoBadgeShown?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isPhotoTakingSupported

```TypeScript
isPhotoTakingSupported?: boolean
```

是否支持拍照，true表示支持，false表示不支持，默认为true。

**类型：** boolean

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-isPhotoTakingSupported?: boolean--><!--Device-BaseSelectOptions-isPhotoTakingSupported?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isPreviewForSingleSelectionSupported

```TypeScript
isPreviewForSingleSelectionSupported?: boolean
```

单选模式下是否需要进大图预览，true表示需要，false表示不需要，默认为true。

**类型：** boolean

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-isPreviewForSingleSelectionSupported?: boolean--><!--Device-BaseSelectOptions-isPreviewForSingleSelectionSupported?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isSearchSupported

```TypeScript
isSearchSupported?: boolean
```

是否支持搜索，true表示支持，false表示不支持，默认为true。

**类型：** boolean

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-isSearchSupported?: boolean--><!--Device-BaseSelectOptions-isSearchSupported?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## maxSelectNumber

```TypeScript
maxSelectNumber?: int
```

选择媒体文件数量的最大值（最大可设置的值为500，若不设置则默认为50）。

**类型：** int

**起始版本：** 26.0.0

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-maxSelectNumber?: int--><!--Device-BaseSelectOptions-maxSelectNumber?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mimeTypeFilter

```TypeScript
mimeTypeFilter?: MimeTypeFilter
```

文件类型的过滤配置，支持指定多个类型过滤。 当配置mimeTypeFilter参数时，MIMEType的配置自动失效。 配置该参数时，仅显示配置过滤类型对应的媒体文件，建议提示用户仅支持选择指定类型的图片/视频。

**类型：** [MimeTypeFilter](arkts-medialibrary-photoaccesshelper-mimetypefilter-c.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-mimeTypeFilter?: MimeTypeFilter--><!--Device-BaseSelectOptions-mimeTypeFilter?: MimeTypeFilter-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoViewMimeTypeFileSizeFilters

```TypeScript
photoViewMimeTypeFileSizeFilters?: Array<PhotoViewMimeTypeFileSizeFilter>
```

指定媒体文件类型和文件大小进行过滤。 配置该参数时，仅取数组前三个参数进行处理，MIMETypes和fileSizeFilter自动失效。

**类型：** Array&lt;[PhotoViewMimeTypeFileSizeFilter](arkts-medialibrary-photoaccesshelper-photoviewmimetypefilesizefilter-c.md)&gt;

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-photoViewMimeTypeFileSizeFilters?: Array<PhotoViewMimeTypeFileSizeFilter>--><!--Device-BaseSelectOptions-photoViewMimeTypeFileSizeFilters?: Array<PhotoViewMimeTypeFileSizeFilter>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## preferredCompatibleMode

```TypeScript
preferredCompatibleMode?: PreferredCompatibleMode
```

资产兼容性模式配置。

**类型：** [PreferredCompatibleMode](arkts-medialibrary-photoaccesshelper-preferredcompatiblemode-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-preferredCompatibleMode?: PreferredCompatibleMode--><!--Device-BaseSelectOptions-preferredCompatibleMode?: PreferredCompatibleMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## preselectedUris

```TypeScript
preselectedUris?: Array<string>
```

预选择图片的uri数据。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-preselectedUris?: Array<string>--><!--Device-BaseSelectOptions-preselectedUris?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## recommendationOptions

```TypeScript
recommendationOptions?: RecommendationOptions
```

图片推荐相关配置参数。

**类型：** [RecommendationOptions](arkts-medialibrary-photoaccesshelper-recommendationoptions-c.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-recommendationOptions?: RecommendationOptions--><!--Device-BaseSelectOptions-recommendationOptions?: RecommendationOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## showDateOnScrollbar

```TypeScript
showDateOnScrollbar?: boolean
```

是否在拖动滚动条时展示日期分组信息，true表示展示，false表示不展示，默认为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-showDateOnScrollbar?: boolean--><!--Device-BaseSelectOptions-showDateOnScrollbar?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## singleSelectionMode

```TypeScript
singleSelectionMode?: SingleSelectionMode
```

单选模式类型。默认为大图预览模式（SingleSelectionMode.BROWSER_MODE）。

**类型：** [SingleSelectionMode](arkts-medialibrary-photoaccesshelper-singleselectionmode-e.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-singleSelectionMode?: SingleSelectionMode--><!--Device-BaseSelectOptions-singleSelectionMode?: SingleSelectionMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## videoDurationFilter

```TypeScript
videoDurationFilter?: VideoDurationFilter
```

可选择媒体文件视频时长的过滤配置。 配置该参数时，仅显示配置视频时长范围的媒体文件，建议提示用户仅支持选择指定时长视频。

**类型：** [VideoDurationFilter](arkts-medialibrary-photoaccesshelper-videodurationfilter-c.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSelectOptions-videoDurationFilter?: VideoDurationFilter--><!--Device-BaseSelectOptions-videoDurationFilter?: VideoDurationFilter-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

