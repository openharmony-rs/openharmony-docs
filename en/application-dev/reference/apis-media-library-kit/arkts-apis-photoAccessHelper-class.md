# Classes (Others)

<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xuchangda; @yixiaoff-->
<!--Designer: @guxinggang; @liweilu1-->
<!--Tester: @wangbeibei; @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## RecommendationOptions<sup>11+</sup>

Defines the image recommendation options. The image recommendation feature depends on the image data analysis capability, which varies with devices.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type               | Read-Only| Optional| Description                         |
| ----------------------- | ------------------- | ---- | ---- | -------------------------------- |
| recommendationType | [RecommendationType](arkts-apis-photoAccessHelper-e.md#recommendationtype11)   | No  | Yes| Type of the recommended image.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| textContextInfo<sup>12+</sup> | [TextContextInfo](arkts-apis-photoAccessHelper-i.md#textcontextinfo12)   | No  | Yes| Text based on which images are recommended. If both **recommendationType** and **textContextInfo** are set, **textContextInfo** takes precedence over **recommendationType**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|

## BaseSelectOptions

Defines the basic options for selecting media files from Gallery.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type               | Read-Only| Optional| Description                         |
| ----------------------- | ------------------- | ---- | ---- | -------------------------------- |
| MIMEType    | [PhotoViewMIMETypes](arkts-apis-photoAccessHelper-e.md#photoviewmimetypes)   | No| Yes  | Available media file types. **IMAGE_VIDEO_TYPE** is used by default.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| maxSelectNumber      | number | No  | Yes| Maximum number of media files that can be selected. The maximum value is **500**, and the default value is **50**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.  |
| isPhotoTakingSupported<sup>11+</sup> | boolean  | No  | Yes| Whether photo taking is supported. **true** if supported, **false** otherwise.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| isSearchSupported<sup>11+</sup> | boolean  | No  | Yes| Whether the image is searchable. **true** if searchable, **false** otherwise.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| recommendationOptions<sup>11+</sup>       | [RecommendationOptions](#recommendationoptions11)   | No  | Yes| Image recommendation parameters.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| preselectedUris<sup>11+</sup> | Array&lt;string&gt;  | No  | Yes| URI of the preselected image.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| isPreviewForSingleSelectionSupported<sup>12+</sup> | boolean  | No  | Yes| Whether to enable full image preview if a single image is selected. **true** to enable, **false** otherwise. The default value is **true**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| singleSelectionMode<sup>18+</sup> | [SingleSelectionMode](arkts-apis-photoAccessHelper-e.md#singleselectionmode18) | No  | Yes| Single selection mode. The default value is **SingleSelectionMode.BROWSER_MODE**.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| mimeTypeFilter<sup>19+</sup> | [MimeTypeFilter](#mimetypefilter19)  | No  | Yes| Configuration for file type filtering. Multiple types can be specified.<br>When this parameter is set, the **MIMEType** configuration automatically becomes invalid.<br>When this parameter is set, only media files of the configured filter type are displayed. You are advised to notify users that only images or videos of the specified type can be selected.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| fileSizeFilter<sup>19+</sup> | [FileSizeFilter](#filesizefilter19)  | No  | Yes| Configuration for file size filtering.<br>When this parameter is set, only media files within the specified size range are displayed. You are advised to notify users that only images or videos of the specified size can be selected.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| videoDurationFilter<sup>19+</sup> | [VideoDurationFilter](#videodurationfilter19)  | No  | Yes| Configuration for video duration filtering.<br>When this parameter is set, only media files within the specified duration range are displayed. You are advised to notify users that only videos of the specified length can be selected.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| combinedMediaTypeFilter<sup>20+</sup> | Array\<string\> | No| Yes| A string array of filter criteria, supporting combinations of various types.<br>The format for the strings is follows: `photoType \| photoSubType1,photoSubType2, … \| mimeType1,mimeType2, ...`.<br>- The first part specifies a single **photoType**, which is fixed at **image** or **video**.<br>- The second part lists 1 to *N* photoSubTypes, separated by commas, with an OR relationship. Currently, the maximum value of *N* is **1**. Options include **movingPhoto** or "*" (ignore).<br>- The third part lists 1 to *N* mimeTypes, separated by commas, with an OR relationship. Currently, the maximum value of *N* is **10**. The format is similar to [MimeTypeFilter](#mimetypefilter19).<br>Filters are combined using intersection logic.<br>The NOT logic is supported. To exclude types, use parentheses. Each string can have only one set.<br>If the filter string does not match the specifications, the result is empty.<br>Only the first three array elements are used; **MIMETypes** and **mimeTypeFilter** are ignored.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| photoViewMimeTypeFileSizeFilters<sup>20+</sup> | Array\<[PhotoViewMimeTypeFileSizeFilter](#photoviewmimetypefilesizefilter20)\>  | No  | Yes| An array used to filter media files by type and size.<br>Only the first three array elements are used; **MIMETypes** and **fileSizeFilter** are ignored.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| isMovingPhotoBadgeShown<sup>22+</sup> | boolean  | No  | Yes| Whether the moving photo badge is displayed in the photo browser page. **true** to display the badge, **false** to hide it. The default is **false**.<br>When this parameter is set to **true**, [Photoselectresult](#photoselectresult) includes an array of movingPhotoBadgeStates, with moving photos defaulting to the **MOVING_PHOTO_ENABLED** state.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
| assetFilter<sup>22+</sup>       | Array\<[OperationItem](#operationitem22)\> | No  | Yes| Media asset filter, with a maximum length of 50 items. If the limit is exceeded, only the first 50 items are used.<br>**NOTE**<br> 1. When this filter is applied, other filters become invalid.<br>2. When setting multiple conditions, enclose the filter conditions in parentheses to prevent conflicts with internal filter items.<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|

## PhotoSelectOptions

PhotoSelectOptions extends BaseSelectOptions

Defines additional options for selecting media files from Gallery. It inherits from [BaseSelectOptions](#baseselectoptions).

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type               | Read-Only| Optional| Description                         |
| ----------------------- | ------------------- | ---- | ---- | -------------------------------- |
| isEditSupported<sup>11+</sup>       | boolean | No  | Yes| Whether the image can be edited. **true** if editable, **false** otherwise.<br>**Atomic service API**: This API can be used in atomic services since API version 11.    |
| isOriginalSupported<sup>12+</sup>       | boolean | No  | Yes| Whether to display the button for selecting the original image. **true** to display, **false** otherwise. The default value is **false**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.    |
| subWindowName<sup>12+</sup>       | string | No  | Yes| Name of the child window.<br>**Atomic service API**: This API can be used in atomic services since API version 12.    |
| completeButtonText<sup>14+</sup>       | [CompleteButtonText](arkts-apis-photoAccessHelper-e.md#completebuttontext14) | No  | Yes| Text displayed on the complete button.<br>The complete button is located in the lower-right corner of the page. It is used by users to signify that they have finished selecting images.<br>**Atomic service API**: This API can be used in atomic services since API version 14.    |
| contextRecoveryInfo<sup>21+</sup>       | [ContextRecoveryInfo](#contextrecoveryinfo21) | No  | Yes| Information for restoring the PhotoPicker's state from the last exit.<br>When the selection process is complete, the PhotoPicker returns **contextRecoveryInfo** to the application. The application can then use the information to restore the PhotoPicker's state and the last viewed grid interface the next time it starts the PhotoPicker.<br>**Atomic service API**: This API can be used in atomic services since API version 21.    |
| isDestroyedWithNavigation<sup>23+</sup>       | boolean | No  | Yes| Whether destruction with [Navigation](../apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigation-1) is supported. **true** if supported, **false** otherwise. The default value is **false**.<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 23.    |

## PhotoSelectResult

Defines information about the images or videos selected.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type               | Read-Only| Optional| Description                         |
| ----------------------- | ------------------- | ---- | ---- | -------------------------------- |
| photoUris       | Array&lt;string&gt; | No  | No| URIs of the images or videos selected. The URI array can be used only by calling [photoAccessHelper.getAssets](arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets) with temporary authorization. For details about how to use the media file URI, see [Using a Media File URI](../../file-management/user-file-uri-intro.md#using-a-media-file-uri).<br>**Atomic service API**: This API can be used in atomic services since API version 11.    |
| isOriginalPhoto       | boolean | No  | No| Whether the selected media file is the original image. **true** if yes, **false** otherwise. The default value is **false**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.    |
| contextRecoveryInfo<sup>21+</sup>         | [ContextRecoveryInfo](#contextrecoveryinfo21)    | No  | No| Information about the context of exiting the PhotoPicker. This information is returned when the selection process is complete and is used by the application within **PhotoSelectOptions** during the subsequent launch of the PhotoPicker to restore the state from the previous exit.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|
| movingPhotoBadgeStates<sup>22+</sup>         | Array\<[MovingPhotoBadgeStateType](arkts-apis-photoAccessHelper-e.md#movingphotobadgestatetype22)\>    | No  | No| Array of moving photo badge states for the media files selected from Gallery.<br>If **isMovingPhotoBadgeShown** is set to **true**, this array contains the moving photo badge states. Otherwise, it is empty.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|

## MimeTypeFilter<sup>19+</sup>

Describes the configuration for file type filtering.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type               | Read-Only| Optional| Description                          |
| ----------------------- | ------------------- | ---- | ---- | ------------------------------ |
| mimeTypeArray        | Array&lt;string&gt;    | No  | No| Types of media files that PhotoPicker allows users to filter by. Up to ten media file types can be specified for filtering.<br>The filter type is defined by the MIME type, for example, image/jpeg and video/mp4.|

## FileSizeFilter<sup>19+</sup>

Describes the configuration for file size filtering.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type               | Read-Only| Optional| Description                          |
| ----------------------- | ------------------- | ---- | ---- |------------------------------ |
| filterOperator        | [FilterOperator](arkts-apis-photoAccessHelper-e.md#filteroperator19)    | No | No| Filter operator.<br>For example, files can be filtered based on being greater than or less than a certain file size.|
| fileSize        | number    | No| No| File size used for filtering.<br>The unit is bytes.|
| extraFileSize   | number    | No| Yes| Maximum file size in **FilterOperator.BETWEEN** mode. The default value is **-1**.<br>The unit is bytes.|

## VideoDurationFilter<sup>19+</sup>

Describes the configuration for video duration filtering.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type               | Read-Only| Optional| Description                          |
| ----------------------- | ------------------- | ---- | ---- |------------------------------ |
| filterOperator        | [FilterOperator](arkts-apis-photoAccessHelper-e.md#filteroperator19)    | No| No |Filter operator.<br>For example, videos can be filtered based on being greater than or less than a certain duration.|
| videoDuration        | number    | No| No| Video duration used for filtering.<br>The unit is milliseconds (ms).|
| extraVideoDuration   | number    | No| Yes| Maximum video duration in **FilterOperator.BETWEEN** mode. The default value is **-1**.<br>The unit is milliseconds (ms).|

## RecentPhotoOptions<sup>20+</sup>

Represents the configuration options of the recent images or videos.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type                                                                                    | Read-Only| Optional | Description  |
|-------------------------|-----------------------------------------------------------------------------------------|-------|-------|--------|
| period                  | number                                                                                  | No   | Yes| Time range for displaying the recent images or videos, measured in seconds. After setting, the system shows images or videos taken within the specified time from the current moment. The longest duration you can set is 1 day (86400s).<br>If the value is less than or equal to 0, greater than 86400, or not set, the system uses the longest duration (1 day) by default. If there are no images or videos within the set time range, the component does not show anything.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| MIMEType                | [photoAccessHelper.PhotoViewMIMETypes](arkts-apis-photoAccessHelper-e.md#photoviewmimetypes) | No   | Yes| Types of the file displayed. The default value is **PhotoViewMIMETypes.IMAGE_VIDEO_TYPE**.<br>**Atomic service API**: This API can be used in atomic services since API version 20.                        |
| photoSource             | [PhotoSource](arkts-apis-photoAccessHelper-e.md#photosource20)                                                             | No   | Yes| Source of the recent image or video, for example, image or video taken by the camera or screenshot. By default, the source is not restricted.<br>**Atomic service API**: This API can be used in atomic services since API version 20.                              |

## RecentPhotoInfo<sup>20+</sup>

Describes the information about the recent image or video.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name        | Type    | Read-Only| Optional | Description                                                       |
|------------|--------|-------|-------|-----------------------------------------------------------|
| dateTaken  | number | No   | Yes| Time when the recent image or video was shot (in milliseconds since January 1, 1970). The unit is ms.<br>**Atomic service API**: This API can be used in atomic services since API version 20.                    |
| identifier | string | No   | Yes| Hash value of the name of the recent image or video, which is used to help the application determine whether the image or video to be displayed is the same as the one displayed before.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## PhotoViewMimeTypeFileSizeFilter<sup>20+</sup>

Describes the settings for filtering media files by type and size.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type               | Read-Only| Optional| Description                         |
| ----------------------- | ------------------- | ---- | ---- | -------------------------------- |
| photoViewMimeType    | [PhotoViewMIMETypes](arkts-apis-photoAccessHelper-e.md#photoviewmimetypes)   | No| No  | Media file types used for filtering.|
| sizeFilter    | [FileSizeFilter](#filesizefilter19)   | No| No  | Media file size used for filtering.|

## ContextRecoveryInfo<sup>21+</sup>

Describes the information about the context of exiting the PhotoPicker. It can be used during the subsequent launch of the PhotoPicker to restore the state from the previous exit.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type               | Read-Only| Optional| Description                         |
| ----------------------- | ------------------- | ---- | ---- | -------------------------------- |
| albumUri    | string | No  | No| URI of the album in the media library when the user selects an image and exits.<br> <br>- If the user selects all images last time, **albumUri** is a fixed **"allPhotos"** string.<br>- If the user exits after selecting from search results, text recommendations, or avatar recommendations, the next restoration is not supported, and the returned **albumUri** is an empty string.<br>The default value is an empty string.|
| time    | number   | No  | No| Time of the top-left image in the grid interface when the user last selected an image.<br>- For albums sorted by capture time, the capture time is returned.<br>- For albums sorted by save time, the save time is returned. The default value is **0**.|
| displayName    | string   | No  | No| File name of the top-left image in the grid interface when the user last selected an image. The default value is an empty string.|
| recommendationType    | number   | No  | No| Enumerated value of the recommended content set by the user during the last selection. For details, see [RecommendationType](arkts-apis-photoAccessHelper-e.md#recommendationtype11).<br>If no recommendation was set during the last selection, the default value is **0**.|
| selectedRecommendationType    | number   | No  | No| Enumerated value of the recommended content selected by the user during the last selection. For details, see [RecommendationType](arkts-apis-photoAccessHelper-e.md#recommendationtype11).<br>If no recommendation was selected during the last selection or **All** is selected, the default value is **0**.|
| version    | number   | No  | No| Version number of the state data, used to verify the compatibility of the state information data with the state recovery capability.<br>The version number must be greater than or equal to 1.0.|

## OperationItem<sup>22+</sup>

Describes the settings for filtering media files.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                   | Type               | Read-Only| Optional| Description                         |
| ----------------------- | ------------------- | ---- | ---- | -------------------------------- |
| operationType    | [OperationType](arkts-apis-photoAccessHelper-e.md#operationtype22)   | No| No  | Predicates.|
| field    | [PhotoKeys](arkts-apis-photoAccessHelper-e.md#photokeys)   | No| Yes  | Column name in the data table.<br>Currently, only the following key fields are supported: **URI**, **PHOTO_TYPE**, **DISPLAY_NAME**, **SIZE**, **DURATION**, **WIDTH**, **HEIGHT**, **ORIENTATION**, **FAVORITE**, **TITLE**, **POSITION**, **PHOTO_SUBTYPE**, **DYNAMIC_RANGE_TYPE**, **COVER_POSITION**, **BURST_KEY**, **LCD_SIZE**, **THM_SIZE**, **DETAIL_TIME**, **MEDIA_SUFFIX**, **OWNER_ALBUM_ID**, and **ASPECT_RATIO**.<br>When [select](arkts-apis-photoAccessHelper-PhotoViewPicker.md#select) is used to set this parameter, an invalid field results in error code 401. When [@ohos.file.PhotoPickerComponent (PhotoPickerComponent)](ohos-file-PhotoPickerComponent.md) is used to set this parameter, an invalid field does not trigger the **onPickerControllerReady** callback.<br>This field is not involved in non-conditional predicates such as **and**, **or**, **beginWrap**, and **endWrap**.|
| value    | Array<[OperationValueType](arkts-apis-photoAccessHelper-t.md#operationvaluetype22)>   | No| Yes  |  Values needed for matching different predicates.<br>This field is not involved in non-conditional predicates such as **and**, **or**, **beginWrap**, and **endWrap**.<br>The maximum length is 10; if exceeded, only the first 10 values are considered.|
