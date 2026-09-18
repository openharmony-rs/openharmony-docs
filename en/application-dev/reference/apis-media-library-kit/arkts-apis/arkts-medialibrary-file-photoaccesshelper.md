# @ohos.file.photoAccessHelper(Helper functions to access image and video assets)

The module provides APIs for album management, including creating an album and accessing and modifying media data in an album.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getPhotoAccessHelper](arkts-medialibrary-photoaccesshelper-getphotoaccesshelper-f.md) | Obtains a PhotoAccessHelper instance for accessing and modifying media files in the album. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getPhotoAccessHelper](arkts-medialibrary-photoaccesshelper-getphotoaccesshelper-f-sys.md) | Obtains a PhotoAccessHelper instance for the specified user, letting you access and modify media files in an album. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [AutoPlayScene](arkts-medialibrary-photoaccesshelper-autoplayscene-c.md) | Defines the playback mode of the moving photo in different scenarios. |
| [BaseSelectOptions](arkts-medialibrary-photoaccesshelper-baseselectoptions-c.md) | Defines the basic options for selecting media files from Gallery. |
| [ContextRecoveryInfo](arkts-medialibrary-photoaccesshelper-contextrecoveryinfo-c.md) | Describes the information about the context of exiting the PhotoPicker. It can be used during the subsequent launch of the PhotoPicker to restore the state from the previous exit. |
| [FileSizeFilter](arkts-medialibrary-photoaccesshelper-filesizefilter-c.md) | Describes the configuration for file size filtering. |
| [GridPinchMode](arkts-medialibrary-photoaccesshelper-gridpinchmode-c.md) | Represents the pinch mode of the grid in the picker. |
| [MediaAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md) | Provides APIs for managing the media album change request. |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | Represents a media asset change request. |
| [MediaAssetManager](arkts-medialibrary-photoaccesshelper-mediaassetmanager-c.md) | The MediaAssetManager class is used for manipulating the read and write operations of media assets. |
| [MediaAssetsChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetschangerequest-c.md) | Represents a request for changing multiple assets. |
| [MimeTypeFilter](arkts-medialibrary-photoaccesshelper-mimetypefilter-c.md) | Describes the configuration for file type filtering. |
| [OperationItem](arkts-medialibrary-photoaccesshelper-operationitem-c.md) | Describes the settings for filtering media files. |
| [PhotoSelectOptions](arkts-medialibrary-photoaccesshelper-photoselectoptions-c.md) | Defines additional options for selecting media assets from Gallery. It inherits from **BaseSelectOptions**. It is used to start the picker of the corresponding user ID space. |
| [PhotoSelectResult](arkts-medialibrary-photoaccesshelper-photoselectresult-c.md) | Defines information about the images or videos selected. |
| [PhotoViewMimeTypeFileSizeFilter](arkts-medialibrary-photoaccesshelper-photoviewmimetypefilesizefilter-c.md) | Describes the settings for filtering media files by type and size. |
| [PhotoViewPicker](arkts-medialibrary-photoaccesshelper-photoviewpicker-c.md) | PhotoViewPicker provides APIs for the user to select images and videos. Before using the APIs of PhotoViewPicker, you need to create a PhotoViewPicker instance. |
| [RecentPhotoInfo](arkts-medialibrary-photoaccesshelper-recentphotoinfo-c.md) | Recent photo info |
| [RecentPhotoOptions](arkts-medialibrary-photoaccesshelper-recentphotooptions-c.md) | RecentPhotoOptions Object |
| [RecommendationOptions](arkts-medialibrary-photoaccesshelper-recommendationoptions-c.md) | Defines the image recommendation options. The image recommendation feature depends on the image data analysis capability, which varies with devices. |
| [RequestReadPermissionResult](arkts-medialibrary-photoaccesshelper-requestreadpermissionresult-c.md) | Request read permission result |
| [VideoDurationFilter](arkts-medialibrary-photoaccesshelper-videodurationfilter-c.md) | Describes the configuration for video duration filtering. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [AnalysisAlbum](arkts-medialibrary-photoaccesshelper-analysisalbum-c-sys.md) | Implements an **Analysis** album. |
| [CloudEnhancement](arkts-medialibrary-photoaccesshelper-cloudenhancement-c-sys.md) | Provides APIs for cloud enhancement management, including managing the tasks of generating AI-powered cloud- enhanced photos and obtaining the association between the original photos and AI cloud-enhanced photos. |
| [CloudMediaAssetManager](arkts-medialibrary-photoaccesshelper-cloudmediaassetmanager-c-sys.md) | A class used for cloud media asset management. It is used to manage download tasks for media assets stored in the cloud and delete local data and files pertaining to these cloud-based assets. |
| [DefaultCoverOrderInfo](arkts-medialibrary-photoaccesshelper-defaultcoverorderinfo-c-sys.md) | Default Cover Order |
| [HighlightAlbum](arkts-medialibrary-photoaccesshelper-highlightalbum-c-sys.md) | Provides APIs for managing the **Highlights** album, which is an automatically generated collection of memorable photos or videos. |
| [KnowledgeContent](arkts-medialibrary-photoaccesshelper-knowledgecontent-c-sys.md) | Knowledge Content class, used for geting related entity. |
| [MediaAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md) | Provides APIs for managing the media album change request. |
| [MediaAnalysisAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaanalysisalbumchangerequest-c-sys.md) | Provides APIs for managing the analysis album change request. |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md) | Represents a media asset change request. |
| [MediaAssetEditData](arkts-medialibrary-photoaccesshelper-mediaasseteditdata-c-sys.md) | Represents the edited media asset data. |
| [MediaAssetManager](arkts-medialibrary-photoaccesshelper-mediaassetmanager-c-sys.md) | The MediaAssetManager class is used for manipulating the read and write operations of media assets. |
| [MediaAssetsChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetschangerequest-c-sys.md) | Represents a request for changing multiple assets. |
| [MediaHighlightAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediahighlightalbumchangerequest-c-sys.md) | Provides APIs for managing the media album change request. It inherits from [MediaAnalysisAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaanalysisalbumchangerequest-c-sys.md). |
| [MediaShareAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediasharealbumchangerequest-c-sys.md) | Represents a change request for managing the share album. |
| [MemberInfo](arkts-medialibrary-photoaccesshelper-memberinfo-c-sys.md) | Member information |
| [PhotoAssetCustomRecordManager](arkts-medialibrary-photoaccesshelper-photoassetcustomrecordmanager-c-sys.md) | Provides APIs for custom user behavior recording for Gallery. |
| [PhotoSelectOptions](arkts-medialibrary-photoaccesshelper-photoselectoptions-c-sys.md) | Defines additional options for selecting media assets from Gallery. It inherits from **BaseSelectOptions**. It is used to start the picker of the corresponding user ID space. |
| [RecommendationOptions](arkts-medialibrary-photoaccesshelper-recommendationoptions-c-sys.md) | Defines the image recommendation options. The image recommendation feature depends on the image data analysis capability, which varies with devices. |
| [ResultSet](arkts-medialibrary-photoaccesshelper-resultset-c-sys.md) | Defines APIs to access the result set obtained by querying the RDB store. |
| [ShareAlbumMemberInfo](arkts-medialibrary-photoaccesshelper-sharealbummemberinfo-c-sys.md) | Member information of shared album |
| [TaskSignal](arkts-medialibrary-photoaccesshelper-tasksignal-c-sys.md) | for interrupting batch operations. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AbsAlbum](arkts-medialibrary-photoaccesshelper-absalbum-i.md) | Defines the abstract interface of albums. |
| [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | Provides APIs to manage albums. |
| [AlbumChangeData](arkts-medialibrary-photoaccesshelper-albumchangedata-i.md) | Describes the change data of an album. |
| [AlbumChangeInfo](arkts-medialibrary-photoaccesshelper-albumchangeinfo-i.md) | Describes the information about an album. |
| [AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md) | Describes the notification information about the change of an album. |
| [AssetCompatibleCapability](arkts-medialibrary-photoaccesshelper-assetcompatiblecapability-i.md) | Defines the asset compatibility capability. |
| [ChangeData](arkts-medialibrary-photoaccesshelper-changedata-i.md) | Defines the return value of the listener callback. |
| [CreateOptions](arkts-medialibrary-photoaccesshelper-createoptions-i.md) | Options for creating an image or video asset. |
| [CreationSetting](arkts-medialibrary-photoaccesshelper-creationsetting-i.md) | Represents the configuration for saving images or videos to the media library, including the file name, file type, and other related parameters. |
| [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | Defines the retrieval options. |
| [FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md) | FetchResult provides APIs to manage the file retrieval result. |
| [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md) | MediaAssetDataHandler is a media asset handler used to customize the media asset processing logic in **onDataPrepared**. |
| [MediaAssetProgressHandler](arkts-medialibrary-photoaccesshelper-mediaassetprogresshandler-i.md) | **MediaAssetProgressHandler** is used to obtain the media asset processing progress from **onProgress()**. |
| [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md) | Media change request, which is the parent class of the asset change request and album change request. |
| [MediaLibraryAvailability](arkts-medialibrary-photoaccesshelper-medialibraryavailability-i.md) | MediaLibrary availability. |
| [MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i.md) | MovingPhoto provides APIs for managing a moving photo instance. |
| [PhotoAccessHelper](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md) | Helper functions to access photos and albums. |
| [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | PhotoAsset provides APIs for encapsulating file asset attributes. |
| [PhotoAssetChangeData](arkts-medialibrary-photoaccesshelper-photoassetchangedata-i.md) | Describes the change data of a media asset. |
| [PhotoAssetChangeInfo](arkts-medialibrary-photoaccesshelper-photoassetchangeinfo-i.md) | Describes the information about a media asset. |
| [PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md) | Describes the notification information about the change of a media asset. |
| [PhotoCreationConfig](arkts-medialibrary-photoaccesshelper-photocreationconfig-i.md) | Represents the configuration for saving a media asset (image or video) to the media library, including the file name. |
| [QuickImageDataHandler](arkts-medialibrary-photoaccesshelper-quickimagedatahandler-i.md) | QuickImageDataHandler is a media asset handler used to customize the media asset processing logic in **onDataPrepared**. |
| [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | Represents request options. |
| [TextContextInfo](arkts-medialibrary-photoaccesshelper-textcontextinfo-i.md) | Represents the text information about the recommended images. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AbsAlbum](arkts-medialibrary-photoaccesshelper-absalbum-i-sys.md) | Defines the abstract interface of albums. |
| [Album](arkts-medialibrary-photoaccesshelper-album-i-sys.md) | Provides APIs to manage albums. |
| [AlbumAttributeInfo](arkts-medialibrary-photoaccesshelper-albumattributeinfo-i-sys.md) | Album attribute info. |
| [AlbumChangeData](arkts-medialibrary-photoaccesshelper-albumchangedata-i-sys.md) | Describes the change data of an album. |
| [AlbumChangeInfo](arkts-medialibrary-photoaccesshelper-albumchangeinfo-i-sys.md) | Describes the information about an album. |
| [AlbumOperation](arkts-medialibrary-photoaccesshelper-albumoperation-i-sys.md) | Represents an album operation configuration. |
| [AlbumOrder](arkts-medialibrary-photoaccesshelper-albumorder-i-sys.md) | Describes the album sorting order. |
| [AnalysisConfig](arkts-medialibrary-photoaccesshelper-analysisconfig-i-sys.md) | Defines the asset analysis configuration. |
| [AnalysisResult](arkts-medialibrary-photoaccesshelper-analysisresult-i-sys.md) | Defines the asset analysis result. |
| [AnalysisToolResult](arkts-medialibrary-photoaccesshelper-analysistoolresult-i-sys.md) | Result of an analysis tool execution. |
| [BatchOperationOptions](arkts-medialibrary-photoaccesshelper-batchoperationoptions-i-sys.md) | Batch operation options |
| [ChangeData](arkts-medialibrary-photoaccesshelper-changedata-i-sys.md) | Defines the return value of the listener callback. |
| [CloudAssetDownloadProgressInfo](arkts-medialibrary-photoaccesshelper-cloudassetdownloadprogressinfo-i-sys.md) | Describes the progress information about a batch download. |
| [CloudAssetDownloadStatus](arkts-medialibrary-photoaccesshelper-cloudassetdownloadstatus-i-sys.md) | Describes the status information about a batch download. |
| [CloudEnhancementTaskState](arkts-medialibrary-photoaccesshelper-cloudenhancementtaskstate-i-sys.md) | Represents the cloud enhancement task information, which includes the cloud enhancement task state and other information related to certain states. |
| [CloudMediaAssetStatus](arkts-medialibrary-photoaccesshelper-cloudmediaassetstatus-i-sys.md) | Describes the details of a cloud media asset download task. It is the return value of the API used by applications to obtain the cloud asset download task status. |
| [ContextMap](arkts-medialibrary-photoaccesshelper-contextmap-i-sys.md) | Provides APIs for input Context Map. |
| [DeepOptimizeSpaceProgress](arkts-medialibrary-photoaccesshelper-deepoptimizespaceprogress-i-sys.md) | Defines the DeepOptimizeSpaceProgress data structure. |
| [Entity](arkts-medialibrary-photoaccesshelper-entity-i-sys.md) | Provides APIs for output Entity. |
| [FormInfo](arkts-medialibrary-photoaccesshelper-forminfo-i-sys.md) | Defines the Gallery widget information. |
| [FusionAssetsInfo](arkts-medialibrary-photoaccesshelper-fusionassetsinfo-i-sys.md) | Fusion assets information. |
| [GalleryFormInfo](arkts-medialibrary-photoaccesshelper-galleryforminfo-i-sys.md) | Defines the Gallery widget information. |
| [MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i-sys.md) | MovingPhoto provides APIs for managing a moving photo instance. |
| [Options](arkts-medialibrary-photoaccesshelper-options-i-sys.md) | Provides APIs for input Options. |
| [PhotoAccessHelper](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md) | Helper functions to access photos and albums. |
| [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i-sys.md) | PhotoAsset provides APIs for encapsulating file asset attributes. |
| [PhotoAssetChangeData](arkts-medialibrary-photoaccesshelper-photoassetchangedata-i-sys.md) | Describes the change data of a media asset. |
| [PhotoAssetChangeInfo](arkts-medialibrary-photoaccesshelper-photoassetchangeinfo-i-sys.md) | Describes the information about a media asset. |
| [PhotoAssetCustomRecord](arkts-medialibrary-photoaccesshelper-photoassetcustomrecord-i-sys.md) | Provides APIs for custom user behavior recording for Gallery. |
| [PhotoCreateOptions](arkts-medialibrary-photoaccesshelper-photocreateoptions-i-sys.md) | Options for creating an image or video asset. |
| [PhotoCreationSource](arkts-medialibrary-photoaccesshelper-photocreationsource-i-sys.md) | Defines the application information provided to create assets on behalf of the application. |
| [PhotoProxy](arkts-medialibrary-photoaccesshelper-photoproxy-i-sys.md) | Photo proxy object, which is used by the camera application to write image data. |
| [Progress](arkts-medialibrary-photoaccesshelper-progress-i-sys.md) | progress info of batch operations. |
| [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i-sys.md) | Represents request options. |
| [RequestPhotoOptions](arkts-medialibrary-photoaccesshelper-requestphotooptions-i-sys.md) | Defines the options for obtaining the thumbnail of an image or video. |
| [ResultInfo](arkts-medialibrary-photoaccesshelper-resultinfo-i-sys.md) | ResultInfo info of batch operations. |
| [SearchSuggestionResult](arkts-medialibrary-photoaccesshelper-searchsuggestionresult-i-sys.md) | Search suggestion result. |
| [SharedAlbumAsset](arkts-medialibrary-photoaccesshelper-sharedalbumasset-i-sys.md) | Defines the shared album asset |
| [SharedPhotoAsset](arkts-medialibrary-photoaccesshelper-sharedphotoasset-i-sys.md) | Describes the information about a shared media asset. |
| [ToolCancelConfig](arkts-medialibrary-photoaccesshelper-toolcancelconfig-i-sys.md) | Configuration for canceling an analysis tool. |
| [ToolInvokeConfig](arkts-medialibrary-photoaccesshelper-toolinvokeconfig-i-sys.md) | Configuration for invoking an analysis tool. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AlbumKeys](arkts-medialibrary-photoaccesshelper-albumkeys-e.md) | Enumerates the album keys. |
| [AlbumSubtype](arkts-medialibrary-photoaccesshelper-albumsubtype-e.md) | Enumerate the album subtypes. |
| [AlbumType](arkts-medialibrary-photoaccesshelper-albumtype-e.md) | Enumerates the album types, |
| [AvailabilityStatus](arkts-medialibrary-photoaccesshelper-availabilitystatus-e.md) | Enumeration of medialibrary availability status. |
| [CompatibleMode](arkts-medialibrary-photoaccesshelper-compatiblemode-e.md) | Enumerates the compatible modes. |
| [CompleteButtonText](arkts-medialibrary-photoaccesshelper-completebuttontext-e.md) | Enumerates the text displayed on the complete button. |
| [DefaultChangeUri](arkts-medialibrary-photoaccesshelper-defaultchangeuri-e.md) | Enumerates the **DefaultChangeUri** subtypes. |
| [DeliveryMode](arkts-medialibrary-photoaccesshelper-deliverymode-e.md) | Enumerates the asset delivery modes. |
| [DynamicRangeType](arkts-medialibrary-photoaccesshelper-dynamicrangetype-e.md) | Enumerates the dynamic range types of media assets. |
| [FilterOperator](arkts-medialibrary-photoaccesshelper-filteroperator-e.md) | Enumeration type of filter operator. |
| [GridLevel](arkts-medialibrary-photoaccesshelper-gridlevel-e.md) | Enumeration type of grid level. |
| [GridPinchModeType](arkts-medialibrary-photoaccesshelper-gridpinchmodetype-e.md) | Enumeration type of grid pinch mode. |
| [ImageFileType](arkts-medialibrary-photoaccesshelper-imagefiletype-e.md) | Enumerates the types of image files to save. |
| [MediaAssetPermissionState](arkts-medialibrary-photoaccesshelper-mediaassetpermissionstate-e.md) | Enumeration of permission level for an application to access asset. |
| [MovingPhotoBadgeStateType](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md) | Enumerates the types of the moving photo badge. |
| [NotifyChangeType](arkts-medialibrary-photoaccesshelper-notifychangetype-e.md) | Enumerates the types of changes that trigger the media asset or album change events. |
| [NotifyType](arkts-medialibrary-photoaccesshelper-notifytype-e.md) | Enumerates the notification event types. |
| [OperationType](arkts-medialibrary-photoaccesshelper-operationtype-e.md) | Enumerates the predicates. |
| [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md) | Defines the key information about an image or video file. |
| [PhotoSource](arkts-medialibrary-photoaccesshelper-photosource-e.md) | Enumeration of PhotoSource type |
| [PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e.md) | Enumerates the [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) types. |
| [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md) | Enumerates the media file types. |
| [PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md) | Enumerates the media file types. |
| [PickerColorMode](arkts-medialibrary-photoaccesshelper-pickercolormode-e.md) | Enumerates the Picker color modes. |
| [PlayMode](arkts-medialibrary-photoaccesshelper-playmode-e.md) | Enumerates whether to support automatic playback of the moving photo. |
| [PositionType](arkts-medialibrary-photoaccesshelper-positiontype-e.md) | Enumerates the file locations. |
| [PreferredCompatibleMode](arkts-medialibrary-photoaccesshelper-preferredcompatiblemode-e.md) | Preferred compatible mode. |
| [RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md) | Enumerates the types of recommended images. |
| [ResourceType](arkts-medialibrary-photoaccesshelper-resourcetype-e.md) | Enumerates the types of the resources to write. |
| [SceneType](arkts-medialibrary-photoaccesshelper-scenetype-e.md) | Enumeration type of scene. |
| [SingleSelectionMode](arkts-medialibrary-photoaccesshelper-singleselectionmode-e.md) | Enumeration type of single selection mode |
| [VideoMode](arkts-medialibrary-photoaccesshelper-videomode-e.md) | Enumerates the log modes of video files. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AlbumAttribute](arkts-medialibrary-photoaccesshelper-albumattribute-e-sys.md) | Album operation attribute. |
| [AlbumKeys](arkts-medialibrary-photoaccesshelper-albumkeys-e-sys.md) | Enumerates the album keys. |
| [AlbumOperationType](arkts-medialibrary-photoaccesshelper-albumoperationtype-e-sys.md) | Album operation type. |
| [AlbumSubtype](arkts-medialibrary-photoaccesshelper-albumsubtype-e-sys.md) | Enumerate the album subtypes. |
| [AlbumType](arkts-medialibrary-photoaccesshelper-albumtype-e-sys.md) | Enumerates the album types, |
| [AnalysisToolType](arkts-medialibrary-photoaccesshelper-analysistooltype-e-sys.md) | Enumerates the smart analysis tool types. |
| [AnalysisType](arkts-medialibrary-photoaccesshelper-analysistype-e-sys.md) | Enumerates the smart analysis types. |
| [AppLinkState](arkts-medialibrary-photoaccesshelper-applinkstate-e-sys.md) | Enumerates the states of a file memory link. |
| [AssetSourceType](arkts-medialibrary-photoaccesshelper-assetsourcetype-e-sys.md) | Enumerates the flags of asset source. |
| [AuthorizationMode](arkts-medialibrary-photoaccesshelper-authorizationmode-e-sys.md) | Enumerates the authorization modes. |
| [CloudAssetDownloadCode](arkts-medialibrary-photoaccesshelper-cloudassetdownloadcode-e-sys.md) | Enumerates the status codes returned when adding an item to a batch download. |
| [CloudAssetDownloadNotifyType](arkts-medialibrary-photoaccesshelper-cloudassetdownloadnotifytype-e-sys.md) | Enumerates the types of events reported during a cloud asset download. |
| [CloudEnhancementState](arkts-medialibrary-photoaccesshelper-cloudenhancementstate-e-sys.md) | Enumerates the cloud enhancement states. |
| [CloudEnhancementTaskStage](arkts-medialibrary-photoaccesshelper-cloudenhancementtaskstage-e-sys.md) | Enumerates the cloud enhancement task states, which are returned by [CloudEnhancementTaskState](arkts-medialibrary-photoaccesshelper-cloudenhancement-c-sys.md). |
| [CloudMediaAssetTaskStatus](arkts-medialibrary-photoaccesshelper-cloudmediaassettaskstatus-e-sys.md) | Enumerates the statuses of tasks used for downloading cloud media assets. |
| [CloudMediaDownloadType](arkts-medialibrary-photoaccesshelper-cloudmediadownloadtype-e-sys.md) | Enumerates the types of download tasks. |
| [CloudMediaRetainType](arkts-medialibrary-photoaccesshelper-cloudmediaretaintype-e-sys.md) | Enumerates the modes used for deleting cloud media assets. |
| [CloudMediaTaskPauseCause](arkts-medialibrary-photoaccesshelper-cloudmediataskpausecause-e-sys.md) | Enumerates the reasons why a cloud media asset download task is paused. |
| [CompositeDisplayMode](arkts-medialibrary-photoaccesshelper-compositedisplaymode-e-sys.md) | Enumerates the display modes available for a composite image. |
| [CoverUriSource](arkts-medialibrary-photoaccesshelper-coverurisource-e-sys.md) | Enumerates the sources of the album covers. |
| [DeepOptimizeState](arkts-medialibrary-photoaccesshelper-deepoptimizestate-e-sys.md) | Describes the state type of deep optimize space. |
| [DefaultChangeUri](arkts-medialibrary-photoaccesshelper-defaultchangeuri-e-sys.md) | Enumerates the **DefaultChangeUri** subtypes. |
| [FieldType](arkts-medialibrary-photoaccesshelper-fieldtype-e-sys.md) | Enumerates related entity filed type. |
| [FusionAssetType](arkts-medialibrary-photoaccesshelper-fusionassettype-e-sys.md) | Enumeration of fusion asset type |
| [HdrMode](arkts-medialibrary-photoaccesshelper-hdrmode-e-sys.md) | Enumerates the HDR modes of media assets. |
| [HiddenPhotosDisplayMode](arkts-medialibrary-photoaccesshelper-hiddenphotosdisplaymode-e-sys.md) | Enumerates the display modes of hidden files in the system. |
| [HideSensitiveType](arkts-medialibrary-photoaccesshelper-hidesensitivetype-e-sys.md) | Enumerates the types of data masking applied to media resources when accessed by an application. |
| [HighlightAlbumChangeAttribute](arkts-medialibrary-photoaccesshelper-highlightalbumchangeattribute-e-sys.md) | Enumerates the attributes of a highlights album. |
| [HighlightAlbumInfoType](arkts-medialibrary-photoaccesshelper-highlightalbuminfotype-e-sys.md) | Enumerates the types of the highlights album information. |
| [HighlightUserActionType](arkts-medialibrary-photoaccesshelper-highlightuseractiontype-e-sys.md) | Enumerates the user behavior types of the highlights album. |
| [LivePhoto4dStatus](arkts-medialibrary-photoaccesshelper-livephoto4dstatus-e-sys.md) | Enumerates the 4d livephoto status. |
| [MovingPhotoEffectMode](arkts-medialibrary-photoaccesshelper-movingphotoeffectmode-e-sys.md) | Enumerates the effects of a moving photo. |
| [NotifyChangeType](arkts-medialibrary-photoaccesshelper-notifychangetype-e-sys.md) | Enumerates the types of changes that trigger the media asset or album change events. |
| [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e-sys.md) | Defines the key information about an image or video file. |
| [PhotoPermissionType](arkts-medialibrary-photoaccesshelper-photopermissiontype-e-sys.md) | Enumerates the types of permissions for accessing media assets. |
| [PhotoRiskStatus](arkts-medialibrary-photoaccesshelper-photoriskstatus-e-sys.md) | Enumerates the risk types of images. |
| [PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e-sys.md) | Enumerates the [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) types. |
| [RankingMethod](arkts-medialibrary-photoaccesshelper-rankingmethod-e-sys.md) | Enumerates related entity Ranking Method |
| [RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e-sys.md) | Enumerates the types of recommended images. |
| [RequestPhotoType](arkts-medialibrary-photoaccesshelper-requestphototype-e-sys.md) | Enumerates the types of the operation for obtaining image or video thumbnails. |
| [ResourceType](arkts-medialibrary-photoaccesshelper-resourcetype-e-sys.md) | Enumerates the types of the resources to write. |
| [SearchSuggestionType](arkts-medialibrary-photoaccesshelper-searchsuggestiontype-e-sys.md) | Search Suggestion Type. |
| [ShareAlbumRiskStatus](arkts-medialibrary-photoaccesshelper-sharealbumriskstatus-e-sys.md) | Enumerates the risk status of share album. |
| [ShareMemberStatus](arkts-medialibrary-photoaccesshelper-sharememberstatus-e-sys.md) | Enumerates the member status of share album. |
| [SourceMode](arkts-medialibrary-photoaccesshelper-sourcemode-e-sys.md) | Enumerates the types of the file to read. |
| [StrongAssociationType](arkts-medialibrary-photoaccesshelper-strongassociationtype-e-sys.md) | Enumerates the strong association types of photos. |
| [SupportedImageFormat](arkts-medialibrary-photoaccesshelper-supportedimageformat-e-sys.md) | Enumerates the supported image formats. |
| [ThumbnailChangeStatus](arkts-medialibrary-photoaccesshelper-thumbnailchangestatus-e-sys.md) | Enumerates the change statuses of thumbnails (including images and videos). |
| [ThumbnailType](arkts-medialibrary-photoaccesshelper-thumbnailtype-e-sys.md) | Enumerates thumbnail types. |
| [ThumbnailVisibility](arkts-medialibrary-photoaccesshelper-thumbnailvisibility-e-sys.md) | Enumerates the visibility statuses of thumbnails. |
| [VideoEnhancementType](arkts-medialibrary-photoaccesshelper-videoenhancementtype-e-sys.md) | Enumerates the types of segmented video enhancement. |
| [WatermarkType](arkts-medialibrary-photoaccesshelper-watermarktype-e-sys.md) | Enumerates the watermark editable flags. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [MemberType](arkts-medialibrary-photoaccesshelper-membertype-t.md) | Defines the types of the PhotoAsset members. |
| [OperationValueType](arkts-medialibrary-photoaccesshelper-operationvaluetype-t.md) | Indicates possible value types |
| [PhotoAssetParams](arkts-medialibrary-photoaccesshelper-photoassetparams-t.md) | Defines the array of record types that map file property names to their values. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [ProgressListener](arkts-medialibrary-photoaccesshelper-progresslistener-t-sys.md) | Indicates the type of the progress of batch operation. |
| [ResultListener](arkts-medialibrary-photoaccesshelper-resultlistener-t-sys.md) | Indicates the type of the result of batch operation. |
| [ValuesBucket](arkts-medialibrary-photoaccesshelper-valuesbucket-t-sys.md) | Defines the type of key and value in a KV pair. |
| [ValueType](arkts-medialibrary-photoaccesshelper-valuetype-t-sys.md) | Defines the type of value in a KV pair. The type varies with the parameter function. |
<!--DelEnd-->
