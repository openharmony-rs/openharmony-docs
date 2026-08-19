# @ohos.file.photoAccessHelper

该模块提供相册管理能力，包括创建相册、访问和修改相册中的媒体数据。

**起始版本：** 23

<!--Device-unnamed-declare namespace photoAccessHelper--><!--Device-unnamed-declare namespace photoAccessHelper-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getPhotoAccessHelper](arkts-medialibrary-photoaccesshelper-getphotoaccesshelper-f.md) | 获取相册管理模块的实例，用于访问和修改相册中的媒体文件。 |
| [getPhotoAccessHelper](arkts-medialibrary-photoaccesshelper-getphotoaccesshelper-f.md) | 获取相册管理模块的实例，用于访问和修改相册中的媒体文件。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getPhotoAccessHelper](arkts-medialibrary-photoaccesshelper-getphotoaccesshelper-f-sys.md) | 支持跨用户获取相册管理模块的实例，用于访问和修改相册中的媒体文件。 |
| [getPhotoAccessHelper](arkts-medialibrary-photoaccesshelper-getphotoaccesshelper-f-sys.md) | 支持跨用户获取相册管理模块的实例，用于访问和修改相册中的媒体文件。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [AutoPlayScene](arkts-medialibrary-photoaccesshelper-autoplayscene-c.md) | 动态照片在不同场景中的播放模式。 |
| [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md) | 图库选择选项基类。 |
| [ContextRecoveryInfo](arkts-medialibrary-photoaccesshelper-contextrecoveryinfo-c.md) | 介绍退出PhotoPicker的上下文信息。可以在后续的发射中使用 的PhotoPicker，以从上一个出口恢复状态。 |
| [FileSizeFilter](arkts-medialibrary-photoaccesshelper-filesizefilter-c.md) | 可选择媒体文件大小的过滤配置。 |
| [GridPinchMode](arkts-medialibrary-photoaccesshelper-gridpinchmode-c.md) | picker内宫格的捏合模式。 |
| [MediaAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md) | MediaAlbumChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md). 相册变更请求。 |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | MediaAssetChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md). 资产变更请求。 |
| [MediaAssetManager](arkts-medialibrary-photoaccesshelper-mediaassetmanager-c.md) | 媒体资产管理类，管理媒体资源读取。 |
| [MimeTypeFilter](arkts-medialibrary-photoaccesshelper-mimetypefilter-c.md) | 文件类型的过滤配置。 |
| [OperationItem](arkts-medialibrary-photoaccesshelper-operationitem-c.md) | 选择媒体文件的过滤配置。 |
| [PhotoSelectOptions](arkts-medialibrary-photoaccesshelper-photoselectoptions-c.md) | 图库选择选项子类，继承于BaseSelectOptions。用于拉起对应userId空间的picker。 |
| [PhotoSelectResult](arkts-medialibrary-photoaccesshelper-photoselectresult-c.md) | 返回图库选择后的结果集。 |
| [PhotoViewMimeTypeFileSizeFilter](arkts-medialibrary-photoaccesshelper-photoviewmimetypefilesizefilter-c.md) | 指定媒体文件类型和文件大小进行过滤。 |
| [PhotoViewPicker](arkts-medialibrary-photoaccesshelper-photoviewpicker-c.md) | 图库选择器对象用于支持选择图片、视频等用户场景。使用前，需先创建PhotoViewPicker实例。 |
| [RecentPhotoInfo](arkts-medialibrary-photoaccesshelper-recentphotoinfo-c.md) | 最近图片相关信息。 |
| [RecentPhotoOptions](arkts-medialibrary-photoaccesshelper-recentphotooptions-c.md) | 最近图片配置选项。 |
| [RecommendationOptions](arkts-medialibrary-photoaccesshelper-recommendationoptions-c.md) | 图片推荐选项(基于图片数据分析结果，依赖设备适配)。 |
| [RequestReadPermissionResult](arkts-medialibrary-photoaccesshelper-requestreadpermissionresult-c.md) | 包含已授权的uri列表和无效的uri列表。 |
| [VideoDurationFilter](arkts-medialibrary-photoaccesshelper-videodurationfilter-c.md) | 可选择媒体文件视频时长的过滤配置。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AnalysisAlbum](arkts-medialibrary-photoaccesshelper-analysisalbum-c-sys.md) | 智慧相册。 |
| [CloudEnhancement](arkts-medialibrary-photoaccesshelper-cloudenhancement-c-sys.md) | 云增强管理类，该类用于生成AI云增强照片任务的管理、获取原照片与AI云增强照片的关联关系。 |
| [CloudMediaAssetManager](arkts-medialibrary-photoaccesshelper-cloudmediaassetmanager-c-sys.md) | 云端媒体资产管理类，该类用于管理云端资产的下载任务，以及删除云端资产在本地的数据和文件。 |
| [DefaultCoverOrderInfo](arkts-medialibrary-photoaccesshelper-defaultcoverorderinfo-c-sys.md) | 相册默认封面选择规则信息。 |
| [HighlightAlbum](arkts-medialibrary-photoaccesshelper-highlightalbum-c-sys.md) | 时刻相册。 |
| [KnowledgeContent](arkts-medialibrary-photoaccesshelper-knowledgecontent-c-sys.md) | 支持的MIME类型。 |
| [MediaAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md) | MediaAlbumChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md). 相册变更请求。 |
| [MediaAnalysisAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaanalysisalbumchangerequest-c-sys.md) | 智慧相册变更请求。 |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md) | MediaAssetChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md). 资产变更请求。 |
| [MediaAssetEditData](arkts-medialibrary-photoaccesshelper-mediaasseteditdata-c-sys.md) | 资产编辑数据。 |
| [MediaAssetsChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetschangerequest-c-sys.md) | 批量资产变更请求。 |
| [MediaHighlightAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediahighlightalbumchangerequest-c-sys.md) | 时刻相册变更请求，MediaHighlightAlbumChangeRequest继承自 [MediaAnalysisAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaanalysisalbumchangerequest-c-sys.md)。 |
| [PhotoAssetCustomRecordManager](arkts-medialibrary-photoaccesshelper-photoassetcustomrecordmanager-c-sys.md) | 媒体库支持图库自定义用户统计行为。 |
| [PhotoSelectOptions](arkts-medialibrary-photoaccesshelper-photoselectoptions-c-sys.md) | 图库选择选项子类，继承于BaseSelectOptions。用于拉起对应userId空间的picker。 |
| [RecommendationOptions](arkts-medialibrary-photoaccesshelper-recommendationoptions-c-sys.md) | 图片推荐选项(基于图片数据分析结果，依赖设备适配)。 |
| [ResultSet](arkts-medialibrary-photoaccesshelper-resultset-c-sys.md) | 提供通过查询数据库生成的数据库结果集的访问方法。 下列API示例中，需先使用[query](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md#query)方法获取ResultSet实例，再调用对应方法。 |
| [TaskSignal](arkts-medialibrary-photoaccesshelper-tasksignal-c-sys.md) | 用于中断复制操作的信号。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AbsAlbum](arkts-medialibrary-photoaccesshelper-absalbum-i.md) | 定义相册的抽象接口。 |
| [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | 实体相册。 |
| [AlbumChangeData](arkts-medialibrary-photoaccesshelper-albumchangedata-i.md) | 相册的具体变更数据。 |
| [AlbumChangeInfo](arkts-medialibrary-photoaccesshelper-albumchangeinfo-i.md) | 相册信息。 |
| [AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md) | 相册的变更通知信息。 |
| [AssetCompatibleCapability](arkts-medialibrary-photoaccesshelper-assetcompatiblecapability-i.md) | 资产兼容能力。 |
| [ChangeData](arkts-medialibrary-photoaccesshelper-changedata-i.md) | 监听器回调函数的返回值。 |
| [CreateOptions](arkts-medialibrary-photoaccesshelper-createoptions-i.md) | 图片或视频的创建选项。 title参数的规格如下： - 不应包含扩展名。 - 文件名字符串长度为1~255。 |
| [CreationSetting](arkts-medialibrary-photoaccesshelper-creationsetting-i.md) | 保存图片或视频到媒体库时的配置项，包括保存的文件名、文件类型和其他相关参数。 |
| [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 检索条件。 |
| [FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md) | 文件检索结果集。 |
| [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md) | 媒体资源处理器，应用在onDataPrepared方法中可自定义媒体资源处理逻辑。 |
| [MediaAssetProgressHandler](arkts-medialibrary-photoaccesshelper-mediaassetprogresshandler-i.md) | 媒体资产进度处理器，应用于onProgress方法中获取媒体资产进度。 |
| [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md) | 媒体变更请求，资产变更请求和相册变更请求的父类型。 > **注意**： > > 媒体变更请求需要在调用[applyChanges](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#applychanges)后才会 > 提交生效。 |
| [MediaLibraryAvailability](arkts-medialibrary-photoaccesshelper-medialibraryavailability-i.md) | 媒体库可用性信息。 |
| [MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i.md) | 动态照片对象。 |
| [PhotoAccessHelper](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md) | 提供访问照片和相册的功能。 |
| [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | 提供封装文件属性的方法。 |
| [PhotoAssetChangeData](arkts-medialibrary-photoaccesshelper-photoassetchangedata-i.md) | 媒体资产（图片/视频）的具体变更数据。 |
| [PhotoAssetChangeInfo](arkts-medialibrary-photoaccesshelper-photoassetchangeinfo-i.md) | 媒体资产（图片/视频）信息。 |
| [PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md) | 媒体资产（图片/视频）的变更通知信息。 |
| [PhotoCreationConfig](arkts-medialibrary-photoaccesshelper-photocreationconfig-i.md) | 保存图片/视频到媒体库的配置，包括保存的文件名等。 |
| [PhotoProxy](arkts-medialibrary-photoaccesshelper-photoproxy-i.md) | 照片代理，相机应用通过该对象写入图片数据。 |
| [QuickImageDataHandler](arkts-medialibrary-photoaccesshelper-quickimagedatahandler-i.md) | 媒体资源处理器，应用在onDataPrepared方法中可自定义媒体资源处理逻辑。 |
| [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | 请求策略。 |
| [TextContextInfo](arkts-medialibrary-photoaccesshelper-textcontextinfo-i.md) | 文本信息，用于推荐图片的文本信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AbsAlbum](arkts-medialibrary-photoaccesshelper-absalbum-i-sys.md) | 定义相册的抽象接口。 |
| [Album](arkts-medialibrary-photoaccesshelper-album-i-sys.md) | 实体相册。 |
| [AlbumAttributeInfo](arkts-medialibrary-photoaccesshelper-albumattributeinfo-i-sys.md) | 相册属性信息。 |
| [AlbumChangeData](arkts-medialibrary-photoaccesshelper-albumchangedata-i-sys.md) | 相册的具体变更数据。 |
| [AlbumChangeInfo](arkts-medialibrary-photoaccesshelper-albumchangeinfo-i-sys.md) | 相册信息。 |
| [AlbumOperation](arkts-medialibrary-photoaccesshelper-albumoperation-i-sys.md) | 相册操作信息。 |
| [AlbumOrder](arkts-medialibrary-photoaccesshelper-albumorder-i-sys.md) | 相册排序信息。 |
| [AnalysisConfig](arkts-medialibrary-photoaccesshelper-analysisconfig-i-sys.md) | 资产分析配置。 |
| [AnalysisResult](arkts-medialibrary-photoaccesshelper-analysisresult-i-sys.md) | 资产分析结果信息。 |
| [AnalysisToolResult](arkts-medialibrary-photoaccesshelper-analysistoolresult-i-sys.md) | 分析工具执行的结果。 |
| [BatchOperationOptions](arkts-medialibrary-photoaccesshelper-batchoperationoptions-i-sys.md) | 批量复制操作选项。 |
| [ChangeData](arkts-medialibrary-photoaccesshelper-changedata-i-sys.md) | 监听器回调函数的返回值。 |
| [CloudAssetDownloadProgressInfo](arkts-medialibrary-photoaccesshelper-cloudassetdownloadprogressinfo-i-sys.md) | 批量下载进度信息。 |
| [CloudAssetDownloadStatus](arkts-medialibrary-photoaccesshelper-cloudassetdownloadstatus-i-sys.md) | 批量下载任务信息。 |
| [CloudEnhancementTaskState](arkts-medialibrary-photoaccesshelper-cloudenhancementtaskstate-i-sys.md) | 云增强任务状态，应用调用云增强任务查询接口的返回类型，包含云增强任务状态及部分状态下的额外信息。 |
| [CloudMediaAssetStatus](arkts-medialibrary-photoaccesshelper-cloudmediaassetstatus-i-sys.md) | 云端媒体资产下载任务的详细信息，应用调用云端资产下载任务查询接口的返回类型。 |
| [ContextMap](arkts-medialibrary-photoaccesshelper-contextmap-i-sys.md) | 用户输入的字段类型 |
| [DeepOptimizeSpaceProgress](arkts-medialibrary-photoaccesshelper-deepoptimizespaceprogress-i-sys.md) | 深度优化存储空间的进度信息。 |
| [Entity](arkts-medialibrary-photoaccesshelper-entity-i-sys.md) | 标签返回结构 |
| [FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i-sys.md) | 文件检索结果集。 |
| [FormInfo](arkts-medialibrary-photoaccesshelper-forminfo-i-sys.md) | 图库卡片相关信息。 |
| [FusionAssetsInfo](arkts-medialibrary-photoaccesshelper-fusionassetsinfo-i-sys.md) | 融合资产信息。 |
| [GalleryFormInfo](arkts-medialibrary-photoaccesshelper-galleryforminfo-i-sys.md) | 图库卡片相关信息。 |
| [MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i-sys.md) | 动态照片对象。 |
| [Options](arkts-medialibrary-photoaccesshelper-options-i-sys.md) | 可选参数 |
| [PhotoAccessHelper](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md) | 提供访问照片和相册的功能。 |
| [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i-sys.md) | 提供封装文件属性的方法。 |
| [PhotoAssetChangeData](arkts-medialibrary-photoaccesshelper-photoassetchangedata-i-sys.md) | 媒体资产（图片/视频）的具体变更数据。 |
| [PhotoAssetChangeInfo](arkts-medialibrary-photoaccesshelper-photoassetchangeinfo-i-sys.md) | 媒体资产（图片/视频）信息。 |
| [PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md) | 媒体库支持图库自定义用户统计行为。 |
| [PhotoCreateOptions](arkts-medialibrary-photoaccesshelper-photocreateoptions-i-sys.md) | 图片或视频的创建选项。 |
| [PhotoCreationSource](arkts-medialibrary-photoaccesshelper-photocreationsource-i-sys.md) | 代替应用创建资产传入的应用信息。 |
| [Progress](arkts-medialibrary-photoaccesshelper-progress-i-sys.md) | 复制操作的进度信息。 |
| [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i-sys.md) | 请求策略。 |
| [RequestPhotoOptions](arkts-medialibrary-photoaccesshelper-requestphotooptions-i-sys.md) | 获取图片或视频缩略图的选项。 |
| [ResultInfo](arkts-medialibrary-photoaccesshelper-resultinfo-i-sys.md) | 复制操作的结果信息。 |
| [SearchQuery](arkts-medialibrary-photoaccesshelper-searchquery-i-sys.md) | 搜索资产的查询配置。 |
| [SearchResult](arkts-medialibrary-photoaccesshelper-searchresult-i-sys.md) | 搜索查询的结果。 |
| [SearchSuggestionResult](arkts-medialibrary-photoaccesshelper-searchsuggestionresult-i-sys.md) | 搜索推荐词结果 |
| [SharedAlbumAsset](arkts-medialibrary-photoaccesshelper-sharedalbumasset-i-sys.md) | Defines the shared album asset |
| [SharedPhotoAsset](arkts-medialibrary-photoaccesshelper-sharedphotoasset-i-sys.md) | 共享图片资产。 |
| [ToolCancelConfig](arkts-medialibrary-photoaccesshelper-toolcancelconfig-i-sys.md) | 取消分析工具的配置。 |
| [ToolInvokeConfig](arkts-medialibrary-photoaccesshelper-toolinvokeconfig-i-sys.md) | 调用分析工具的配置。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AlbumKeys](arkts-medialibrary-photoaccesshelper-albumkeys-e.md) | 枚举，相册关键信息。 |
| [AlbumSubtype](arkts-medialibrary-photoaccesshelper-albumsubtype-e.md) | 枚举，相册子类型，表示具体的相册类型。 |
| [AlbumType](arkts-medialibrary-photoaccesshelper-albumtype-e.md) | 枚举，相册类型。例如，用户相册、系统预置相册或由应用创建的相册。 |
| [AvailabilityStatus](arkts-medialibrary-photoaccesshelper-availabilitystatus-e.md) | 枚举，媒体库可用性状态。 |
| [CompatibleMode](arkts-medialibrary-photoaccesshelper-compatiblemode-e.md) | 配置转码模式。 |
| [CompleteButtonText](arkts-medialibrary-photoaccesshelper-completebuttontext-e.md) | 配置完成按钮显示内容。 |
| [DefaultChangeUri](arkts-medialibrary-photoaccesshelper-defaultchangeuri-e.md) | 枚举，DefaultChangeUri子类型。 |
| [DeliveryMode](arkts-medialibrary-photoaccesshelper-deliverymode-e.md) | 枚举，资源分发模式。 该模式适用于分段式拍照或分段式视频。如果当前设备不具备分段式能力，则以下三种分发模式无区别，直接返回请求的图片或视频资源。 请求的结果通过 [onDataPrepared](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md#ondataprepared) 回调返回。 |
| [DynamicRangeType](arkts-medialibrary-photoaccesshelper-dynamicrangetype-e.md) | 枚举，媒体文件的动态范围类型。 |
| [FilterOperator](arkts-medialibrary-photoaccesshelper-filteroperator-e.md) | 枚举，支持进行过滤的操作符。 |
| [GridLevel](arkts-medialibrary-photoaccesshelper-gridlevel-e.md) | 枚举类型，用于设置拉起picker后的宫格列数档位。 |
| [GridPinchModeType](arkts-medialibrary-photoaccesshelper-gridpinchmodetype-e.md) | 枚举，宫格捏合模式类型。 |
| [ImageFileType](arkts-medialibrary-photoaccesshelper-imagefiletype-e.md) | 枚举，图片保存类型。 |
| [MediaAssetPermissionState](arkts-medialibrary-photoaccesshelper-mediaassetpermissionstate-e.md) | 枚举，媒体库资产读权限状态。 |
| [MovingPhotoBadgeStateType](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md) | 枚举，动态照片状态。 |
| [NotifyChangeType](arkts-medialibrary-photoaccesshelper-notifychangetype-e.md) | 枚举，媒体资产（图片/视频）或相册变更事件的通知类型。 |
| [NotifyType](arkts-medialibrary-photoaccesshelper-notifytype-e.md) | 枚举，通知事件的类型。 |
| [OperationType](arkts-medialibrary-photoaccesshelper-operationtype-e.md) | 表示各类谓词的枚举。 |
| [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md) | 枚举，图片和视频文件关键信息。 |
| [PhotoSource](arkts-medialibrary-photoaccesshelper-photosource-e.md) | 枚举，图片或者视频数据的来源类型。 |
| [PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e.md) | PhotoSubtype是不同[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)类型的枚举。 |
| [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md) | 枚举，媒体文件类型。 |
| [PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md) | 枚举，可选择的媒体文件类型。 |
| [PickerColorMode](arkts-medialibrary-photoaccesshelper-pickercolormode-e.md) | 枚举选择器颜色模式。 |
| [PlayMode](arkts-medialibrary-photoaccesshelper-playmode-e.md) | 枚举，是否支持动态照片自动播放。 |
| [PositionType](arkts-medialibrary-photoaccesshelper-positiontype-e.md) | 枚举，文件位置，表示文件在本地或云端。 |
| [PreferredCompatibleMode](arkts-medialibrary-photoaccesshelper-preferredcompatiblemode-e.md) | 枚举，根据配置的资产兼容性执行转码。 |
| [RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md) | 枚举，推荐的图片类型。 |
| [ResourceType](arkts-medialibrary-photoaccesshelper-resourcetype-e.md) | 枚举，写入资源的类型。 |
| [SceneType](arkts-medialibrary-photoaccesshelper-scenetype-e.md) | 枚举，动态照片播放的场景。 |
| [SingleSelectionMode](arkts-medialibrary-photoaccesshelper-singleselectionmode-e.md) | 枚举，单选模式类型。 |
| [VideoMode](arkts-medialibrary-photoaccesshelper-videomode-e.md) | 枚举，视频文件的log模式。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AlbumAttribute](arkts-medialibrary-photoaccesshelper-albumattribute-e-sys.md) | 枚举，相册的属性类型。 |
| [AlbumKeys](arkts-medialibrary-photoaccesshelper-albumkeys-e-sys.md) | 枚举，相册关键信息。 |
| [AlbumOperationType](arkts-medialibrary-photoaccesshelper-albumoperationtype-e-sys.md) | 枚举，设置相册属性的操作类型。 |
| [AlbumSubtype](arkts-medialibrary-photoaccesshelper-albumsubtype-e-sys.md) | 枚举，相册子类型，表示具体的相册类型。 |
| [AlbumType](arkts-medialibrary-photoaccesshelper-albumtype-e-sys.md) | 枚举，相册类型。例如，用户相册、系统预置相册或由应用创建的相册。 |
| [AnalysisToolType](arkts-medialibrary-photoaccesshelper-analysistooltype-e-sys.md) | 枚举智慧分析工具类型。 |
| [AnalysisType](arkts-medialibrary-photoaccesshelper-analysistype-e-sys.md) | 枚举，智慧分析类型。 |
| [AppLinkState](arkts-medialibrary-photoaccesshelper-applinkstate-e-sys.md) | 枚举，用于标识文件记忆链接的状态信息。 |
| [AssetSourceType](arkts-medialibrary-photoaccesshelper-assetsourcetype-e-sys.md) | 资产的来源 |
| [AuthorizationMode](arkts-medialibrary-photoaccesshelper-authorizationmode-e-sys.md) | 枚举，授权模式。 |
| [CloudAssetDownloadCode](arkts-medialibrary-photoaccesshelper-cloudassetdownloadcode-e-sys.md) | 枚举，批量下载添加返回值类型。 |
| [CloudAssetDownloadNotifyType](arkts-medialibrary-photoaccesshelper-cloudassetdownloadnotifytype-e-sys.md) | 枚举，下载进度通知事件类型。 |
| [CloudEnhancementState](arkts-medialibrary-photoaccesshelper-cloudenhancementstate-e-sys.md) | 枚举，表示云增强状态。 |
| [CloudEnhancementTaskStage](arkts-medialibrary-photoaccesshelper-cloudenhancementtaskstage-e-sys.md) | 枚举，应用查询云增强任务状态时，在[CloudEnhancementTaskState](arkts-medialibrary-photoaccesshelper-cloudenhancement-c-sys.md)接口中返回，表示云增强任务状态。 |
| [CloudMediaAssetTaskStatus](arkts-medialibrary-photoaccesshelper-cloudmediaassettaskstatus-e-sys.md) | 枚举，表示云端媒体资产的下载任务状态。 |
| [CloudMediaDownloadType](arkts-medialibrary-photoaccesshelper-cloudmediadownloadtype-e-sys.md) | 枚举，表示云端媒体资产的下载方式。 |
| [CloudMediaRetainType](arkts-medialibrary-photoaccesshelper-cloudmediaretaintype-e-sys.md) | 枚举，表示云端媒体资产的删除方式。 |
| [CloudMediaTaskPauseCause](arkts-medialibrary-photoaccesshelper-cloudmediataskpausecause-e-sys.md) | 枚举，表示云端媒体资产下载任务暂停的类型。 |
| [CompositeDisplayMode](arkts-medialibrary-photoaccesshelper-compositedisplaymode-e-sys.md) | 枚举，表示复合图显示模式。 |
| [CoverUriSource](arkts-medialibrary-photoaccesshelper-coverurisource-e-sys.md) | 枚举，表示相册封面的来源。 |
| [DeepOptimizeState](arkts-medialibrary-photoaccesshelper-deepoptimizestate-e-sys.md) | 表示深度优化存储空间的状态类型的枚举。 |
| [DefaultChangeUri](arkts-medialibrary-photoaccesshelper-defaultchangeuri-e-sys.md) | 枚举，DefaultChangeUri子类型。 |
| [FieldType](arkts-medialibrary-photoaccesshelper-fieldtype-e-sys.md) | Smartlabel类型字段名 |
| [FusionAssetType](arkts-medialibrary-photoaccesshelper-fusionassettype-e-sys.md) | 融合资产类型枚举表。 |
| [HdrMode](arkts-medialibrary-photoaccesshelper-hdrmode-e-sys.md) | 枚举，媒体资产的HDR模式。 |
| [HiddenPhotosDisplayMode](arkts-medialibrary-photoaccesshelper-hiddenphotosdisplaymode-e-sys.md) | 枚举，系统中隐藏文件显示模式。 |
| [HideSensitiveType](arkts-medialibrary-photoaccesshelper-hidesensitivetype-e-sys.md) | 枚举，应用访问媒体资源时，对媒体资源进行信息脱敏的类型。 |
| [HighlightAlbumChangeAttribute](arkts-medialibrary-photoaccesshelper-highlightalbumchangeattribute-e-sys.md) | 枚举，时刻相册属性。 |
| [HighlightAlbumInfoType](arkts-medialibrary-photoaccesshelper-highlightalbuminfotype-e-sys.md) | 枚举，时刻相册信息类型。 |
| [HighlightUserActionType](arkts-medialibrary-photoaccesshelper-highlightuseractiontype-e-sys.md) | 枚举，时刻用户行为类型。 |
| [LivePhoto4dStatus](arkts-medialibrary-photoaccesshelper-livephoto4dstatus-e-sys.md) | 子弹时间状态枚举 |
| [MovingPhotoEffectMode](arkts-medialibrary-photoaccesshelper-movingphotoeffectmode-e-sys.md) | 枚举，动态照片效果模式。 |
| [NotifyChangeType](arkts-medialibrary-photoaccesshelper-notifychangetype-e-sys.md) | 枚举，媒体资产（图片/视频）或相册变更事件的通知类型。 |
| [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e-sys.md) | 枚举，图片和视频文件关键信息。 |
| [PhotoPermissionType](arkts-medialibrary-photoaccesshelper-photopermissiontype-e-sys.md) | 枚举，应用对媒体资源不同访问权限的类型。 包括临时读权限和永久读权限，临时读权限会随着应用的死亡而删除，永久读权限不会。 同一个应用对同一个媒体资源的权限覆盖规则：永久读会覆盖临时读，而临时读不会覆盖永久读。 |
| [PhotoRiskStatus](arkts-medialibrary-photoaccesshelper-photoriskstatus-e-sys.md) | 枚举，用于标识图片是否存在风险的类型。 |
| [PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e-sys.md) | PhotoSubtype是不同[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)类型的枚举。 |
| [PositionType](arkts-medialibrary-photoaccesshelper-positiontype-e-sys.md) | 枚举，文件位置，表示文件在本地或云端。 |
| [RankingMethod](arkts-medialibrary-photoaccesshelper-rankingmethod-e-sys.md) | 随机类型 |
| [RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e-sys.md) | 枚举，推荐的图片类型。 |
| [RequestPhotoType](arkts-medialibrary-photoaccesshelper-requestphototype-e-sys.md) | 枚举，获取图片或视频缩略图的操作类型。 |
| [ResourceType](arkts-medialibrary-photoaccesshelper-resourcetype-e-sys.md) | 枚举，写入资源的类型。 |
| [SearchSuggestionType](arkts-medialibrary-photoaccesshelper-searchsuggestiontype-e-sys.md) | 搜索推荐词类型 |
| [SourceMode](arkts-medialibrary-photoaccesshelper-sourcemode-e-sys.md) | 枚举，资源文件的读取类型。 |
| [StrongAssociationType](arkts-medialibrary-photoaccesshelper-strongassociationtype-e-sys.md) | 枚举，表示图片的强关联类型。 |
| [SupportedImageFormat](arkts-medialibrary-photoaccesshelper-supportedimageformat-e-sys.md) | 枚举，支持转换的图片格式。 |
| [ThumbnailChangeStatus](arkts-medialibrary-photoaccesshelper-thumbnailchangestatus-e-sys.md) | 枚举，表示缩略图（包括图片/视频）更新的状态。 |
| [ThumbnailType](arkts-medialibrary-photoaccesshelper-thumbnailtype-e-sys.md) | 枚举，缩略图类型。 |
| [ThumbnailVisibility](arkts-medialibrary-photoaccesshelper-thumbnailvisibility-e-sys.md) | 枚举，缩略图是否可访问。 |
| [VideoEnhancementType](arkts-medialibrary-photoaccesshelper-videoenhancementtype-e-sys.md) | 枚举，分段式视频的二段式触发类型。 |
| [WatermarkType](arkts-medialibrary-photoaccesshelper-watermarktype-e-sys.md) | 枚举，水印可编辑标识。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [MemberType](arkts-medialibrary-photoaccesshelper-membertype-t.md) | PhotoAsset的成员类型。 成员类型为下表类型的并集。 |
| [OperationValueType](arkts-medialibrary-photoaccesshelper-operationvaluetype-t.md) | 表示不同谓词所需要匹配的值。 |
| [PhotoAssetParams](arkts-medialibrary-photoaccesshelper-photoassetparams-t.md) | 文件属性名称及其值的Record类型数组。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ProgressListener](arkts-medialibrary-photoaccesshelper-progresslistener-t-sys.md) | 表示复制操作进度的监听类型。 进度回调可以表示复制操作的大小进度和复制操作的文件数量进度。 |
| [ResultListener](arkts-medialibrary-photoaccesshelper-resultlistener-t-sys.md) | 表示复制操作结果的监听类型。 |
| [ValueType](arkts-medialibrary-photoaccesshelper-valuetype-t-sys.md) | 用于表示允许的数据字段类型，接口参数的具体类型根据其功能而定。 |
| [ValuesBucket](arkts-medialibrary-photoaccesshelper-valuesbucket-t-sys.md) | 用于存储键值对的类型。 |
<!--DelEnd-->

