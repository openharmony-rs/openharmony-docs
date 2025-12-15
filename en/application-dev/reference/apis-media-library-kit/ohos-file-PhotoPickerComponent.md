# @ohos.file.PhotoPickerComponent (PhotoPickerComponent)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xuchangda-->
<!--Designer: @guxinggang-->
<!--Tester: @wangbeibei-->
<!--Adviser: @w_Machine_cc-->

You can embed the **PhotoPickerComponent** in your application's layout to let users pick images or videos without requiring extra permissions. Once the users have made their selection, your application gets read-only access to the chosen images or videos.

Note that the **PhotoPickerComponent** does not support nesting. Additionally, avoid overlaying components with the **overlay** attribute on top of the **PhotoPickerComponent**, as this will prevent the **PhotoPickerComponent** from receiving gesture events.

Once embedded, users can directly select images or videos within the **PhotoPickerComponent**.

> **NOTE**
>
> This component is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import {
  PhotoPickerComponent, PickerController, PickerOptions,
  DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, ItemType, ClickType,
  MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement,
  ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback
} from '@ohos.file.PhotoPickerComponent';
```

## Attributes

The [universal attributes](../apis-arkui/arkui-ts/ts-component-general-attributes.md) are supported.

## PhotoPickerComponent

PhotoPickerComponent({
  pickerOptions?: PickerOptions,
  onSelect?: (uri: string) => void,
  onDeselect?: (uri: string) => void,
  onItemClicked?: (itemInfo: ItemInfo, clickType: ClickType) => boolean,
  onEnterPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean,
  onExitPhotoBrowser?: (photoBrowserInfo: PhotoBrowserInfo) => boolean,
  onPickerControllerReady?: () => void,
  onPhotoBrowserChanged?: (browserItemInfo: BaseItemInfo) => boolean,
  onSelectedItemsDeleted?: ItemsDeletedCallback,
  onExceedMaxSelected?: ExceedMaxSelectedCallback,
  onCurrentAlbumDeleted?: CurrentAlbumDeletedCallback,
  onVideoPlayStateChanged?: videoPlayStateChangedCallback,
  pickerController: PickerController
})

Allows the application to access images or videos in the user directory without any permission.

> **NOTE**
>
> If the **PhotoPickerComponent** is used with the **Tabs** component, the swipe gestures of the **Tabs** component conflict with those of the photo browser page. To prevent this problem, you can disable the swipe operation for the **Tabs** component in **onEnterPhotoBrowser()** and enable it in **onExitPhotoBrowser()**. This conflict will be resolved in later versions.

**Decorator**: @Component

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name                     | Type                                                                              | Mandatory | Decorator Type     | Description                                                                                                                                                                                                                                                                                                                                                           |
|-------------------------|----------------------------------------------------------------------------------|-----|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| pickerOptions           | [PickerOptions](#pickeroptions)                                                  | No  | - | Picker configuration parameters.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                                                                                    |
| onSelect                | (uri: string) => void                                                            | No  | - | Callback to be invoked when an image is selected by using **PhotoPickerComponent**. This callback returns the URI of the image selected to the application.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                                                           |
| onDeselect              | (uri: string) => void                                                            | No  | - | Callback to be invoked when an image is deselected by using **PhotoPickerComponent**. This callback returns the URI of the image deselected to the application.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                                                     |
| onItemClicked           | (itemInfo: [ItemInfo](#iteminfo), clickType: [ClickType](#clicktype)) => boolean | No  | - | Callback to be invoked when an item in a **PhotoPickerComponent** is clicked.<br>For an image (thumbnail item), if **true** is returned, the image is selected. Otherwise, the image is not selected and the URI is not granted with the permission. For a camera item, if **true** is returned, the system camera is started. Otherwise, the camera is not started and the application handles the request.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                           |
| onEnterPhotoBrowser     | (photoBrowserInfo: [PhotoBrowserInfo](#photobrowserinfo)) => boolean             | No  | - | Callback to be invoked when the photo browser page is displayed. The callback returns photo browser information to the application. No special processing is performed on the return value.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                                                                    |
| onExitPhotoBrowser      | (photoBrowserInfo: [PhotoBrowserInfo](#photobrowserinfo)) => boolean             | No  | - | Callback to be invoked when the photo browser page exits. The callback returns photo browser information to the application. No special processing is performed on the return value.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                                                                      |
| onPickerControllerReady | () => void                                                                       | No  | - | Callback to be invoked when **pickerController** is available.<br>The **PickerController** APIs can be called only after this callback is invoked.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                              |
| onPhotoBrowserChanged   | (browserItemInfo: [BaseItemInfo](#baseiteminfo)) => boolean                      | No  | - | Callback to be invoked when the photo browser page is swiped left or right. The callback returns photo browser information to the application. The setting takes effect only in multi-selection mode. No special processing is performed on the return value.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                                                                    |
| onSelectedItemsDeleted<sup>13+</sup>  | [ItemsDeletedCallback](#itemsdeletedcallback13)                                  | No  | - | Callback to be invoked when the selected items are deleted. This callback returns information about the deleted items to the application.<br>**Atomic service API**: This API can be used in atomic services since API version 13.                                                                                                                                                                                                                                                                                                                             |
| onExceedMaxSelected<sup>13+</sup>     | [ExceedMaxSelectedCallback](#exceedmaxselectedcallback13)                          | No  | - | Callback to be invoked when the number of selected media assets exceeds the limit (maximum number of selected images, selected videos, or selected items).<br>- If the number of selected images reaches the maximum but does not reach the maximum count of selected items, **exceedMaxCountType** in the callback is [MaxCountType](#maxcounttype).PHOTO_MAX_COUNT.<br>- If the number of selected videos reaches the maximum but does not reach the maximum count of selected items, **exceedMaxCountType** in the callback is [MaxCountType](#maxcounttype).VIDEO_MAX_COUNT.<br>- If the number of selected media assets reaches the maximum count of selected items, **exceedMaxCountType** in the callback is [MaxCountType](#maxcounttype).TOTAL_MAX_COUNT.<br>**Atomic service API**: This API can be used in atomic services since API version 13.|
| onCurrentAlbumDeleted<sup>13+</sup>   | [CurrentAlbumDeletedCallback](#currentalbumdeletedcallback13)                    | No  | - | Callback to be invoked when the current album is deleted.<br>The album is specified by **currentAlbumUri** in pickerController.[setData](#setdata)([DataType](#datatype).SET_ALBUM_URI, currentAlbumUri).<br>To refresh the grid page to display the default album after the current album is deleted, you can set the title bar name to the default album name, for example, **Photos and videos**, **Photos**, or **Videos**, and call pickerController.[setData](#setdata)([DataType](#datatype).SET_ALBUM_URI, '') with an empty string.<br>**Atomic service API**: This API can be used in atomic services since API version 13.                                 |
| onVideoPlayStateChanged<sup>14+</sup>   | [videoPlayStateChangedCallback](#videoplaystatechangedcallback14)                    | No  | - | Callback to be invoked when the video playback state on a photo browser page changes.<br>**Atomic service API**: This API can be used in atomic services since API version 14.                                 |
| pickerController        | [PickerController](#pickercontroller)                                            | Yes  | @ObjectLink | Instance used to send data to the **PhotoPickerComponent**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| onMovingPhotoBadgeStateChanged<sup>22+</sup> | [MovingPhotoBadgeStateChangedCallback](#movingphotobadgestatechangedcallback22) | No| - | Callback to be invoked when the moving photo effect of the **PhotoPickerComponent** is enabled or disabled. This callback reports the image's URI and its new moving photo badge state to the application.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|

## PickerOptions

Describes the configuration of a Picker. It inherits from [photoAccessHelper.BaseSelectOptions](arkts-apis-photoAccessHelper-class.md#baseselectoptions).

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                             | Type                                     | Read-Only| Optional | Description                                                                      |
|---------------------------------|-----------------------------------------|-----|-----|--------------------------------------------------------------------------|
| checkBoxColor                   | string                                  | No | Yes| Background color of the check box. The value is an 8-digit hexadecimal color code.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                  |
| backgroundColor                 | string                                  | No | Yes| Background color of the Picker grid page. The value is an 8-digit hexadecimal color code.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                            |
| isRepeatSelectSupported         | boolean                                 | No | Yes| Whether a single image can be repeatedly selected. The value **true** means that a single image can be repeatedly selected. The default value is **false**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                  |
| checkboxTextColor               | string                                  | No | Yes| Text color in the check box. The value is an 8-digit hexadecimal color code. (This parameter is supported since API version 19. In earlier versions, the system defaults to white.)<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                       |
| photoBrowserBackgroundColorMode | [PickerColorMode](#pickercolormode)     | No | Yes| Background color of the photo browser page. The options are **AUTO**, **LIGHT**, and **DARK**. The default value is **AUTO**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                       |
| maxSelectedReminderMode         | [ReminderMode](#remindermode)           | No | Yes| Mode of the reminder when the number of selected items reaches the maximum. The options are **NONE**, **TOAST**, and **MASK**. The default value **TOAST**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                        |
| orientation                     | [PickerOrientation](#pickerorientation) | No | Yes| Sliding preview direction of the grid page. The options are **HORIZONTAL** and **VERTICAL**. The default value is **VERTICAL**. (This parameter is supported since API version 20. In earlier versions, the system defaults to vertical.)<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                |
| selectMode                      | [SelectMode](#selectmode)               | No | Yes | Select mode, which can be **SINGLE_SELECT** or **MULTI_SELECT**. The default value is **MULTI_SELECT**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                     |
| maxPhotoSelectNumber            | number                                  | No | Yes| Maximum number of images that can be selected. The maximum value is **500**, which is limited by **MaxSelected**. The default value is **500**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                          |
| maxVideoSelectNumber            | number                                  | No | Yes| Maximum number of videos that can be selected. The maximum value is **500**, and it is restricted by the maximum number of media files that can be selected in the system. The default value is **500**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                          |
| isSlidingSelectionSupported<sup>13+</sup>     | boolean                                 | No | Yes| Whether sliding selection (selecting multiple items by sliding finger across the screen) is supported. The value **true** means that sliding selection is supported. By default, it is not supported. This parameter is not available for repeat selection.<br>**Atomic service API**: This API can be used in atomic services since API version 13.                                           |
| photoBrowserCheckboxPosition<sup>13+</sup>    | [number, number]                        | No | Yes| Position of the check box on the photo browser page. The first parameter specifies the offset in the X direction, and the second parameter specifies the offset in the Y direction. The value range is 0-1, which indicates the offset (from 0% to 100%) to the upper-left corner of the component. The default value is [0, 0].<br>**Atomic service API**: This API can be used in atomic services since API version 13.|
| gridMargin<sup>14+</sup>        | [Margin](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#margin)                        | No | Yes| Margin of the component on a grid page.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| photoBrowserMargin<sup>14+</sup>    | [Margin](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#margin)                        | No | Yes| Margin of the component on a photo browser page.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| singleLineConfig<sup>20+</sup>             | [SingleLineConfig](#singlelineconfig20)                                                | No | Yes| Single-line display mode of a grid page. In single-line mode, the component does not provide functions for viewing a larger image. The component does not support callbacks related to large images, and the PickerController does not support APIs related to large images, making API calls ineffective.<br>**Atomic service API**: This API can be used in atomic services since API version 20.     |  
| uiComponentColorMode<sup>20+</sup>             | [PickerColorMode](#pickercolormode)                                                | No | Yes| Picker color mode. Dark/Light color mode (excluding the background color) of other components on the Picker grid page, including the search box, camera entry, safety tips for using Gallery, and recommendation bubble. This attribute is usually used together with **backgroundColor**. The default value is **PickerColorMode.AUTO**, which follows the system's dark/light color mode.<br>When setting this attribute, avoid using **PickerColorMode.LIGHT** with a dark backgroundColor, as it may make components or text hard to see. Avoid using **PickerColorMode.DARK** with a light backgroundColor for the same reason.<br>**Atomic service API**: This API can be used in atomic services since API version 20. |
| gridStartOffset<sup>20+</sup>    | number                              | No | Yes | Space between the top of the component and the first row of the grid thumbnail. The default value is **0**, in vp.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| gridEndOffset<sup>20+</sup>    | number                              | No | Yes| Space between the bottom of the component and the last row of the grid thumbnail. The default value is **0**, in vp.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| pickerIndex<sup>21+</sup>    | number                              | No | Yes | Unique serial number used to distinguish different picker components. The default value is **-1**, indicating that no distinction is made.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|
| preselectedInfos<sup>21+</sup>    | Array&lt;[PreselectedInfo](#preselectedinfo21)&gt;                              | No  | Yes| Array of information previously selected by the user, so that the PhotoPickerComponent identified by **pickerIndex** can display the information.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|
| badgeConfig<sup>21+</sup>    | [BadgeConfig](#badgeconfig21)                              | No  | Yes| Badge configuration. Currently, the **PhotoPickerComponent** supports only one type of badge. For details, see [BadgeType](#badgetype21).<br>**Atomic service API**: This API can be used in atomic services since API version 21.|
| isSlidingSupported<sup>23+</sup>         | boolean                         | No  | Yes| Whether scrolling in the **PhotoPickerComponent** is enabled. The value **true** means that scrolling is not blocked and the component responds to user scroll gestures. The value **false** means that scrolling is blocked and the component does not respond to user scroll gestures.<br>The default value is **true**.<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|

## ItemsDeletedCallback<sup>13+</sup>

type ItemsDeletedCallback = (baseItemInfos: Array&lt;BaseItemInfo&gt;) => void

Called when the selected items are deleted.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name| Type                                        | Mandatory| Description      |
| -------- |--------------------------------------------| -------- |----------|
| baseItemInfos | Array&lt;[BaseItemInfo](#baseiteminfo)&gt; | Yes| Basic information about the selected items.|

## ExceedMaxSelectedCallback<sup>13+</sup>

type ExceedMaxSelectedCallback = (exceedMaxCountType: MaxCountType) => void

Called when items are selected after the maximum count has been reached.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name| Type                           | Mandatory| Description                                          |
| -------- |-------------------------------| -------- |----------------------------------------------|
| exceedMaxCountType | [MaxCountType](#maxcounttype) | Yes| Type of the maximum count that has been reached. It can be the maximum count of selected images, maximum count of selected videos, or maximum count of selected images and videos.|

## CurrentAlbumDeletedCallback<sup>13+</sup>

type CurrentAlbumDeletedCallback = () => void

Called when the current album is deleted.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

## videoPlayStateChangedCallback<sup>14+</sup>

type videoPlayStateChangedCallback = (state: VideoPlayerState) => void

Callback to be invoked when the video playback state on a photo browser page changes.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name| Type                           | Mandatory| Description                                          |
| -------- |-------------------------------| -------- |----------------------------------------------|
| state | [VideoPlayerState](#videoplayerstate14) | Yes| Enumerates the video playback states.|

## MovingPhotoBadgeStateChangedCallback<sup>22+</sup>

type MovingPhotoBadgeStateChangedCallback = (uri: string, state: photoAccessHelper.MovingPhotoBadgeStateType) => void

Callback to be invoked when the moving photo effect of the **PhotoPickerComponent** is enabled or disabled.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name| Type                           | Mandatory| Description|
| ----- |-------------------------------| ----- |----------------------------------------------|
| uri    | string                         | Yes   | URI of the moving photo.|
| state  | [photoAccessHelper.MovingPhotoBadgeStateType](arkts-apis-photoAccessHelper-e.md#movingphotobadgestatetype22) | Yes| State of the moving photo badge.|

## PickerController

Defines an instance used to send data to the **PhotoPickerComponent**.

**Decorator Type**: @Observed

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

### setData

setData(dataType: DataType, data: Object): void

Sends data of the specified type to the **PhotoPickerComponent**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

|  Name       | Type                                   | Mandatory | Description |
| ------------------------- | ------------------ | ----- | --------------- |
| dataType | [DataType](#datatype) | Yes| Type of the data to send.|
| data | Object | Yes| Data to send.| 

### addData<sup>21+</sup>

addData(dataType: DataType, data: Object): void

Sends additional configuration data to the **PhotoPickerComponent**. The [DataType](#datatype) parameter identifies the type of data to send, and only the **SET_BADGE_CONFIGS** type is supported currently.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

|  Name       | Type                                   | Mandatory | Description |
| ------------------------- | ------------------ | ----- | --------------- |
| dataType | [DataType](#datatype) | Yes| Type of additional configuration data to send.|
| data | Object | Yes| Additional configuration data to send.| 

### deleteData<sup>21+</sup>

deleteData(dataType: DataType, data: Object): void

Sends removal configuration data to the **PhotoPickerComponent**. The [DataType](#datatype) parameter identifies the type of data being sent, and only the **SET_BADGE_CONFIGS** type is supported currently.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

|  Name       | Type                                   | Mandatory | Description |
| ------------------------- | ------------------ | ----- | --------------- |
| dataType | [DataType](#datatype) | Yes| Type of removal configuration data to send.|
| data | Object | Yes| Removal configuration data to send.| 

### setMaxSelected

setMaxSelected(maxSelected: MaxSelected): void

Sets the maximum number of images, videos, or images and videos that can be selected on a real-time basis.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

|  Name       | Type                                   | Mandatory | Description    |
| ------------------------- | ------------------ | ----- | --------------- |
| maxSelected | [MaxSelected](#maxselected) | Yes| Maximum number of media assets that can be selected at a time.|

### setPhotoBrowserItem

setPhotoBrowserItem(uri: string, photoBrowserRange?: PhotoBrowserRange): void

Switches from the **PhotoPickerComponent** to the photo browser page or from the photo browser page to the image to be viewed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

|  Name       | Type                                   | Mandatory | Description |
| ------------------------- | ------------------ | ----- | --------------- |
| uri | string | Yes| URI of the image to view. Only the images selected by the user are supported.|
| photoBrowserRange | [PhotoBrowserRange](#photobrowserrange) | No| View range on the photo browser page. The value can be **ALL** or **SELECTED_ONLY**. The default value is **ALL**, which means to view all images and videos.| 

### exitPhotoBrowser<sup>13+</sup>

exitPhotoBrowser(): void

Exits the photo browser page.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

### setPhotoBrowserUIElementVisibility<sup>13+</sup>

setPhotoBrowserUIElementVisibility(elements: Array&lt;PhotoBrowserUIElement&gt;, isVisible: boolean): void

Sets whether other UI elements are visible on the photo browser page. By default, other UI elements are visible.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name        | Type                                                            | Mandatory | Description               |
|-------------|----------------------------------------------------------------| ----- |-------------------|
| elements    | Array&lt;[PhotoBrowserUIElement](#photobrowseruielement13)&gt; | Yes| Other UI elements on the photo browser page.|
| isVisible | boolean                                                        | Yes| Whether the specified UI elements are visible. The value **true** means that they are visible. The default value is **false**.            |

### replacePhotoPickerPreview<sup>15+</sup>

replacePhotoPickerPreview(originalUri: string, newUri: string, callback: AsyncCallback&lt;void&gt;): void

Replaces the image selected by the user in the **PhotoPickerComponent** with the image edited by the application.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name        | Type                    |     Mandatory    | Description               |
|-------------|----------------------------| -------------- |-------------------|
| originalUri     | string  | Yes| URI of the original image, which will be replaced.|
| newUri  | string   | Yes| URI of the new image. The new image is temporarily stored in the application sandbox path. Therefore, this URI specifies a directory in the application sandbox path.     |
| callback   | AsyncCallback&lt;void&gt;   | Yes| Callback invoked when image replacement is complete.     |

### saveTrustedPhotoAssets<sup>15+</sup>

saveTrustedPhotoAssets(trustedUris: Array&lt;string&gt;, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;, configs?: Array&lt;photoAccessHelper.PhotoCreationConfig&gt;, saveMode?: SaveMode): void

Saves files in a URI list. Generally, this API is used together with [replacePhotoPickerPreview](#replacephotopickerpreview15) to save the new images or videos in the application sandbox path to Gallery.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name        | Type                                                            | Mandatory | Description               |
|-------------|----------------------------------------------------------------| ----- |-------------------|
| trustedUris     | Array&lt;string&gt; | Yes| URIs of the images or videos in the application sandbox path. Generally, **trustedUris** comes from **newUri** of new images generated by [replacePhotoPickerPreview](#replacephotopickerpreview15).|
| callback  | AsyncCallback&lt;Array&lt;string&gt;&gt;          | Yes| URIs of the new files in Gallery.            |
| configs | Array&lt;[photoAccessHelper.PhotoCreationConfig](arkts-apis-photoAccessHelper-i.md#photocreationconfig12)&gt;          | No| Configuration parameters corresponding to the original files.<br>**NOTE**<br>If a **subtype** option is passed, the configuration does not take effect. Only DEFAULT images can be saved.            |
| saveMode | [SaveMode](#savemode15)           | No| Mode for saving the files.            |

### updatePickerOptions<sup>22+</sup>

updatePickerOptions(updateConfig: UpdatablePickerConfigs): Promise\<void>

Updates the attributes of the **PhotoPickerComponent**. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name        | Type                                                            | Mandatory | Description               |
|-------------|----------------------------------------------------------------| ----- |-------------------|
| updateConfig | [UpdatablePickerConfigs](#updatablepickerconfigs22) | Yes| New attributes, which are a subset of [PickerOptions](#pickeroptions).|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| Promise\<void> | Promise that returns no value.|

## BaseItemInfo

Represents basic image and video information.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name    | Type   | Read-Only| Optional | Description                                               |
|----------|--------|-----|-----|---------------------------------------------------|
| uri      | string                | No| Yes  | URI of the image or video.<br>This parameter is supported only when [ItemType](#itemtype) is set to **THUMBNAIL**. Otherwise, it is left empty.<br>**Atomic service API**: This API can be used in atomic services since API version 12.           |
| mimeType | string                | No| Yes  | MIME type of the image or video.<br>This parameter is supported only when [ItemType](#itemtype) is set to **THUMBNAIL**. Otherwise, it is left empty.<br>**Atomic service API**: This API can be used in atomic services since API version 12.      |
| width    | number                | No| Yes  | Width of the image or video, in px.<br>This parameter is supported only when [ItemType](#itemtype) is set to **THUMBNAIL**. Otherwise, it is left empty.<br>**Atomic service API**: This API can be used in atomic services since API version 12.      |
| height   | number                | No| Yes  | Height of the image or video, in px.<br>This parameter is supported only when [ItemType](#itemtype) is set to **THUMBNAIL**. Otherwise, it is left empty.<br>**Atomic service API**: This API can be used in atomic services since API version 12.      |
| size     | number                | No| Yes  | Size of the image or video, in bytes.<br>This parameter is supported only when [ItemType](#itemtype) is set to **THUMBNAIL**. Otherwise, it is left empty.<br>**Atomic service API**: This API can be used in atomic services since API version 12.    |
| duration   | number                | No| Yes  | Video duration, in milliseconds. For an image or a moving photo, the value **-1** is returned.<br>This parameter is supported only when [ItemType](#itemtype) is set to **THUMBNAIL**. Otherwise, it is left empty.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| photoSubType<sup>21+</sup>   | [photoAccessHelper.PhotoSubtype](arkts-apis-photoAccessHelper-e.md#photosubtype12)        | No| Yes  | Subtype of the photo. The options are **DEFAULT**, **MOVING_PHOTO**, and **BRUST**.<br>The default value is **DEFAULT (0)**.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|
| dynamicRangeType<sup>21+</sup>   | [photoAccessHelper.DynamicRangeType](arkts-apis-photoAccessHelper-e.md#dynamicrangetype12)                 | No| Yes  | Dynamic range type of the media file. The options are **HDR** and **SDR**.<br>For moving photos, this parameter specifies the dynamic range type of the cover image.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|
| orientation<sup>21+</sup>   | number             | No| Yes  | Image or video direction information.<br>1: **TOP-left**: The image is not rotated.<br>2: **TOP-right**: The image is flipped horizontally.<br>3: **Bottom-right**: The image is rotated by 180°.<br>4: **Bottom-left**: The image is flipped vertically.<br>5: **Left-top**: The image is flipped horizontally and then rotated clockwise by 270°.<br>6: **Right-top**: The image is rotated clockwise by 90°.<br>7: **Right-bottom**: The image is vertically flipped and then rotated clockwise by 90°.<br>8: **Left-bottom**: The image is rotated clockwise by 270°.<br>Images with mirroring information retain their original width and height attributes regardless of rotation, whereas images without such information have these attributes updated to reflect the post-rotation dimensions.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|
| movingPhotoBadgeState<sup>22+</sup> | [photoAccessHelper.MovingPhotoBadgeStateType](arkts-apis-photoAccessHelper-e.md#movingphotobadgestatetype22) | No| Yes  | State of the moving photo badge.<br>This parameter is supported only when [ItemType](#itemtype) is set to **THUMBNAIL**. Otherwise, it is left empty.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
| VideoMode<sup>22+</sup> | [photoAccessHelper.VideoMode](arkts-apis-photoAccessHelper-e.md#videomode22) | No| Yes  | Log mode of a video file.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
## ItemInfo

Represents the image and video information. It inherits from [BaseItemInfo](#baseiteminfo), adding the parameter **itemType**.
 

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name    | Type   | Read-Only| Optional | Description                                               |
|----------|--------|-----|-----|---------------------------------------------------|
| itemType | [ItemType](#itemtype) | No| Yes  | Type of the item, which can be **THUMBNAIL** or **CAMERA**.                     |

## PhotoBrowserInfo

Represents information about the photo browser page.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name    | Type   | Read-Only | Optional| Description    |
|----------|--------|-----|-----|---------|
| animatorParams | [AnimatorParams](#animatorparams) | No|  Yes | Animation for entering or exiting the photo browser page.|

## AnimatorParams

Animation parameters for entering or exiting the photo browser page.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name    | Type   | Read-Only| Optional | Description          |
|----------|--------|-----|-----|--------------|
| duration | number  | No | Yes| Animation duration, in ms.|
| curve      | [Curve](../apis-arkui/js-apis-curve.md#curve) &verbar; [ICurve](../apis-arkui/js-apis-curve.md#icurve9) &verbar; string | No  | Yes| Animation curve.       |

## MaxSelected

Represents the maximum number of media assets that can be selected at a time.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name    | Type   | Read-Only | Optional| Description    |
|----------|--------|-----|-----|---------|
| data | Map&lt;[MaxCountType](#maxcounttype), number&gt; | No            | Yes| Maximum number of media assets (images, videos, or both) that can be selected at a time.|

## SingleLineConfig<sup>20+</sup>

Represents the single-line display mode. In single-line mode, the component does not provide functions for viewing a larger image. The component does not support callbacks related to large images, and the PickerController does not support APIs related to large images, making API calls ineffective.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name| Type                                            | Read-Only| Optional| Description                                                                          |
| ---- | ------------------------------------------------ | ---- | ---- | ------------------------------------------------------------------------------ |
| itemDisplayRatio | [ItemDisplayRatio](#itemdisplayratio20) | No  | Yes| Aspect ratio for grid display. Both 1:1 and the original image aspect ratio are supported. The default value is 1:1.|
| itemBorderRadius | [Length](../apis-arkui/arkui-ts/ts-types.md#length) &verbar; [BorderRadiuses](../apis-arkui/arkui-ts/ts-types.md#borderradiuses9) &verbar; [LocalizedBorderRadiuses](../apis-arkui/arkui-ts/ts-types.md#localizedborderradiuses12) | No  | Yes|Rounded corner radius for grid items.|
| itemGap | [Length](../apis-arkui/arkui-ts/ts-types.md#length) | No  | Yes| Spacing between grid items.|

## BadgeConfig<sup>21+</sup>

Describes the badge configuration.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name| Type                                            | Read-Only| Optional| Description                                                                          |
| ---- | ------------------------------------------------ | ---- | ---- | ------------------------------------------------------------------------------ |
| badgeType | [BadgeType](#badgetype21) | No  | Yes| Badge type.|
| uris | Array&lt;string&gt;  | No  | Yes| URIs of the assets for the badge.|

## PreselectedInfo<sup>21+</sup>

Describes the information about the preselected files and their corresponding **PhotoPickerComponent** index.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name| Type                                            | Read-Only| Optional| Description                                                                          |
| ---- | ------------------------------------------------ | ---- | ---- | ------------------------------------------------------------------------------ |
| uri | string | No  | No|URI of the preselected media file.|
| preselectablePickerIndex | number | No  | Yes| Index of the **PhotoPickerComponent** that can be used in automatic selection. The default value is **-1**, which allows automatic selection in any **PhotoPickerComponent**.|

## UpdatablePickerConfigs<sup>22+</sup>

Describes the updatable attributes of the **PhotoPickerComponent**. These attributes are a subset of [PickerOptions](#pickeroptions).

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                           | Type                                            | Read-Only| Optional| Description |
| ------------------------------- | ----------------------------------------------- | ---- | ---- | ---- |
| mimeType                        | [photoAccessHelper.PhotoViewMIMETypes](arkts-apis-photoAccessHelper-e.md#photoviewmimetypes)            | No| Yes  | MIME types.<br>If this parameter is not specified, **IMAGE_VIDEO_TYPE** is used by default.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
| mimeTypeFilter                  | [photoAccessHelper.MimeTypeFilter](arkts-apis-photoAccessHelper-class.md#mimetypefilter19)  | No  | Yes| Configuration for file type filtering. Multiple types can be specified.<br>- When this parameter is set, the **mimeType** configuration automatically becomes invalid.<br>- When this parameter is set, only media files of the configured filter type are displayed. You are advised to notify users that only images or videos of the specified type can be selected.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
| maxSelectNumber                 | number                          | No  | Yes| Maximum number of media files that can be selected.<br>The maximum value is 500, and the default value is 50.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
| maxPhotoSelectNumber            | number                          | No | Yes| Maximum number of images that can be selected (unit: number).<br>The maximum value is **500**, which is limited by **MaxSelected**. The default value is **500**.<br>**Atomic service API**: This API can be used in atomic services since API version 22.                                    |
| maxVideoSelectNumber            | number                          | No | Yes| Maximum number of videos that can be selected (unit: number).<br>The maximum value is **500**, and it is restricted by the maximum number of media files that can be selected in the system. The default value is **500**.<br>**Atomic service API**: This API can be used in atomic services since API version 22.                                     |
| selectMode                      | [SelectMode](#selectmode)       | No | Yes | Picker selection mode.<br>**SINGLE_SELECT** or **MULTI_SELECT**. The default value is **MULTI_SELECT**.<br>**Atomic service API**: This API can be used in atomic services since API version 22.                                                   |
| singleSelectionMode             | [photoAccessHelper.SingleSelectionMode](arkts-apis-photoAccessHelper-e.md#singleselectionmode18) | No  | Yes| Single selection mode. The default value is **SingleSelectionMode.BROWSER_MODE**.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
| isRepeatSelectSupported         | boolean                         | No  | Yes| Whether a single image can be repeatedly selected.<br>**true** if supported, **false** otherwise. The default value is **false**.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
| preselectedUris | Array&lt;string&gt;                             | No  | Yes| URIs of the selected images.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
| checkBoxColor                   | string                          | No | Yes| Background color of the check box.<br>The value is an 8-digit hexadecimal color code.<br>**Atomic service API**: This API can be used in atomic services since API version 22.                                                 |
| backgroundColor                 | string                          | No | Yes| Background color of the Picker grid page.<br>The value is an 8-digit hexadecimal color code.<br>**Atomic service API**: This API can be used in atomic services since API version 22.                                          |
| checkboxTextColor               | string                          | No | Yes| Text color in the check box.<br>The value is an 8-digit hexadecimal color code.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
| photoBrowserBackgroundColorMode | [PickerColorMode](#pickercolormode) | No | Yes| Background color of the photo browser page.<br>The options are **AUTO**, **LIGHT**, and **DARK**. The default value is **AUTO**.<br>**Atomic service API**: This API can be used in atomic services since API version 22.                                     |
| uiComponentColorMode            | [PickerColorMode](#pickercolormode) | No | Yes| Color mode of the Picker UI component.<br>Dark/Light color mode (excluding the background color) of other components on the Picker grid page, including the search box, camera entry, safety tips for using Gallery, and recommendation bubble. This attribute is usually used together with **backgroundColor**. The default value is **PickerColorMode.AUTO**, which follows the system's dark/light color mode.<br>When setting this attribute, avoid using **PickerColorMode.LIGHT** with a dark background color, as it may make components or text hard to see. Avoid using **PickerColorMode.DARK** with a light background color for the same reason.<br>**Atomic service API**: This API can be used in atomic services since API version 22. |
| isSlidingSupported<sup>23+</sup>         | boolean                         | No  | Yes| Whether scrolling in the **PhotoPickerComponent** is enabled. The value **true** means that scrolling is not blocked and the component responds to user scroll gestures. The value **false** means that scrolling is blocked and the component does not respond to user scroll gestures.<br>The default value is **true**.<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 23.|

## DataType

Enumerates the types of data sent from **PickerController** to the **PhotoPickerComponent**.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description                                                                                                                |
|-------------------|-----|--------------------------------------------------------------------------------------------------------------------|
| SET_SELECTED_URIS | 1   | Sends a list of selected items to instruct the **PhotoPickerComponent** to refresh the selection status. A string array needs to be passed in.<br>For example, after an image is deleted from an application's page, the application calls **setData()** to notify the **PhotoPickerComponent** of the remaining selected items. Then, the **PhotoPickerComponent** refreshes the check box status.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| SET_ALBUM_URI | 2   | Sends the selected album to instruct the **PhotoPickerComponent** to refresh the album data. A string array needs to be passed in.<br>For example, after an album is selected from an application's page, the application calls **setData** to notify the **PhotoPickerComponent** of the URI of the selected album. Then, the **PhotoPickerComponent** refreshes the album data.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| SET_SELECTED_INFO<sup>21+</sup> | 3   | Sends the URI of the selected file and the index of the selected **PhotoPickerComponent**. If the index of a **PhotoPickerComponent** matches the one provided in the parameter, the selected file is automatically highlighted in that **PhotoPickerComponent**.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|
| SET_BADGE_CONFIGS<sup>21+</sup> | 4   | Sends the badge configurations, which are of the [badgeConfig](#badgeconfig21) type and include a list of data with badge types and corresponding file URIs. Once configured, the badge of the configured type is displayed in the specified file.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|

## ItemType

Enumerates the types of the item clicked.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description        |
|-------------------|-----|------------|
| THUMBNAIL | 0   | Image or video (thumbnail).|
| CAMERA | 1   | Camera item.   |

## ClickType

Enumerates the click operation types.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description                    |
|-------------------|-----|------------------------|
| SELECTED | 0   | Select (select an image or click a camera item).|
| DESELECTED | 1   | Deselect (deselect an image).      |

## PickerOrientation

Enumerates the sliding preview directions of the Picker grid page.

This capability can be configured since API version 20. If this capability is set since API version 12 to 19, the setting does not take effect and the default direction (vertical) is used.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description   |
|-------------------|-----|-------|
| VERTICAL | 0   | Vertical direction.|
| HORIZONTAL | 1   | Horizontal direction.|

## SelectMode

Enumerates the select modes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description   |
|-------------------|-----|-------|
| SINGLE_SELECT | 0   | Select a single option.|
| MULTI_SELECT | 1   | Select multiple options.|

## PickerColorMode

Enumerates the Picker color modes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description   |
|-------------------|-----|-------|
| AUTO | 0   | Same with the system.|
| LIGHT | 1   | Light mode.|
| DARK | 2   | Dark mode.|

## ReminderMode

Enumerates the types of the reminder when the number of selected items reaches the maximum.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description       |
|-------------------|-----|-----------|
| NONE | 0   | No reminder.     |
| TOAST | 1   | Toast message.|
| MASK | 2   | Grayed-out hint.    |

## MaxCountType

Enumerates the types of the maximum count.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description                       |
|-------------------|-----|---------------------------|
| TOTAL_MAX_COUNT | 0   | Total number of media assets (images and videos) that can be selected.                |
| PHOTO_MAX_COUNT | 1   | Total number of images that can be selected. The value cannot be greater than **Total_MAX_Count**.|
| VIDEO_MAX_COUNT | 2   | Total number of videos that can be selected. The value cannot be greater than **Total_MAX_Count**.|

## PhotoBrowserRange

Enumerates the view range on the photo browser page.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description                       |
|-------------------|-----|---------------------------|
| ALL | 0   | View all images and videos.                |
| SELECTED_ONLY | 1   | View selected images and videos only.|

## PhotoBrowserUIElement<sup>13+</sup>

Represents other UI elements except the image preview component on the photo browser page.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name         | Value  | Description      |
|-------------|-----|----------|
| CHECKBOX    | 0   | Check box on the photo browser page. |
| BACK_BUTTON | 1   | **Back** button on the photo browser page.|

## SaveMode<sup>15+</sup>

Enumerates the modes for saving images or videos.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name         | Value  | Description      |
|-------------|-----|----------|
| SAVE_AS     | 0   | Saves the image or video as a new one. |
| OVERWRITE  | 1   | Replaces the original image or video. After the replacements, you can roll back the saved content in Gallery to restore the original image or video.|

## BadgeType<sup>21+</sup>

Enumerates the badge types.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name         | Value  | Description      |
|-------------|-----|----------|
| BADGE_UPLOADED     | 0   | Uploaded. |

## VideoPlayerState<sup>14+</sup>

Enumerates the video playback states.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description                       |
|-------------------|-----|---------------------------|
| PLAYING | 0   | The video is being played.                |
| PAUSED | 1   | Video playback is paused.|
| STOPPED | 2   | Video playback is stopped.|
| SEEK_START | 3   | Started dragging the progress bar.|
| SEEK_FINISH | 4   | Finished dragging the progress bar.|

## ItemDisplayRatio<sup>20+</sup>

Enumerates the aspect ratios for grid display in single-line display mode.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value | Description          |
| ------------------- | --- | -------------- |
| SQUARE_RATIO        | 0   | 1:1 ratio.   |
| ORIGINAL_SIZE_RATIO | 1   | Original image aspect ratio.|

## Example

```ts
// xxx.ets
import {
  PhotoPickerComponent,
  PickerController,
  PickerOptions,
  DataType,
  BaseItemInfo,
  ItemInfo,
  PhotoBrowserInfo,
  ItemType,
  ClickType,
  MaxCountType,
  PhotoBrowserRange,
  PhotoBrowserUIElement,
  ItemsDeletedCallback,
  ExceedMaxSelectedCallback,
  CurrentAlbumDeletedCallback,
  videoPlayStateChangedCallback,
  VideoPlayerState
} from '@ohos.file.PhotoPickerComponent';
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct PickerDemo {
  pickerOptions: PickerOptions = new PickerOptions();
  @State pickerController: PickerController = new PickerController();
  @State selectUris: string[] = [];
  @State currentUri: string = '';
  @State isBrowserShow: boolean = false;
  private selectedItemsDeletedCallback: ItemsDeletedCallback =
    (baseItemInfos: Array<BaseItemInfo>) => this.onSelectedItemsDeleted(baseItemInfos);
  private exceedMaxSelectedCallback: ExceedMaxSelectedCallback =
    (exceedMaxCountType: MaxCountType) => this.onExceedMaxSelected(exceedMaxCountType);
  private currentAlbumDeletedCallback: CurrentAlbumDeletedCallback = () => this.onCurrentAlbumDeleted();
  private videoPlayStateChangedCallback: videoPlayStateChangedCallback =
    (state: VideoPlayerState) => this.videoPlayStateChanged(state);
  private thumbnail: PixelMap[] = [];
  private assets: photoAccessHelper.PhotoAsset[] = [];

  aboutToAppear() {
    this.pickerOptions.MIMEType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_VIDEO_TYPE;
    this.pickerOptions.maxSelectNumber = 5;
    this.pickerOptions.isSearchSupported = false;
    this.pickerOptions.isPhotoTakingSupported = false;
    this.pickerOptions.photoBrowserCheckboxPosition = [0.5, 0.5];
    // Other attributes
  }

  private onSelect(uri: string): void {
    // Add
    if (uri) {
      this.selectUris.push(uri);
    }
  }

  private onDeselect(uri: string): void {
    // Remove
    if (uri) {
      this.selectUris = this.selectUris.filter((item: string) => {
        return item != uri;
      })
    }
  }

  private onItemClicked(itemInfo: ItemInfo, clickType: ClickType): boolean {
    if (!itemInfo) {
      return false;
    }
    let type: ItemType | undefined = itemInfo.itemType;
    let uri: string | undefined = itemInfo.uri;
    if (type === ItemType.CAMERA) {
      // Click a camera item.
      return true; // If true is returned, the system camera is started. If false is returned, the app processes its services.
    } else {
      if (clickType === ClickType.SELECTED) {
        // The application performs its own service logic (not time-consuming operations, such as opening a large file using OpenSync).
        if (uri) {
          this.selectUris.push(uri);
          this.pickerOptions.preselectedUris = [...this.selectUris];
        }
        return true; // If true is returned, the check box is selected. Otherwise, the check box is not selected.
      } else {
        if (uri) {
          this.selectUris = this.selectUris.filter((item: string) => {
            return item != uri;
          });
          this.pickerOptions.preselectedUris = [...this.selectUris];
        }
      }
      return true;
    }
  }

  private onEnterPhotoBrowser(photoBrowserInfo: PhotoBrowserInfo): boolean {
    // Callback to be invoked when the photo browser page is displayed.
    this.isBrowserShow = true;
    return true;
  }

  private onExitPhotoBrowser(photoBrowserInfo: PhotoBrowserInfo): boolean {
    // Callback to be invoked when the photo browser page is closed.
    this.isBrowserShow = false;
    return true;
  }

  private onPickerControllerReady(): void {
    // After the callback is called, pickerController APIs can be called to send data to Picker. Before the callback is called, pickerController APIs do not take effect.
    let elements: number[] = [PhotoBrowserUIElement.BACK_BUTTON];
    this.pickerController.setPhotoBrowserUIElementVisibility(elements, false); // Hide the Back button on the photo browser page.
  }

  private onPhotoBrowserChanged(browserItemInfo: BaseItemInfo): boolean {
    // Callback to be invoked when the photo browser is swiped left or right.
    this.currentUri = browserItemInfo.uri ?? '';
    return true;
  }

  private onSelectedItemsDeleted(baseItemInfos: Array<BaseItemInfo>): void {
    // Callback to be invoked when the selected image is deleted.
  }

  private onExceedMaxSelected(exceedMaxCountType: MaxCountType): void {
    // Callback to be invoked when the number of selected items exceeds the maximum.
  }

  private onCurrentAlbumDeleted(): void {
    // Callback to be invoked when the current album is deleted.
  }

  private videoPlayStateChanged(state: VideoPlayerState): void {
    // Called when the video playback state changes.
  }
  build() {
    Flex({
      direction: FlexDirection.Column,
      justifyContent: FlexAlign.Center,
      alignItems: ItemAlign.Center
    }) {
      Column() {
        if (this.isBrowserShow) {
          // Back button of the application on the photo browser page.
          Row() {
            Button("Exit photo browser page").width('33%').height('8%').onClick(() => {
              this.pickerController.exitPhotoBrowser();
            })
          }.margin({ bottom: 20 })
        }

        PhotoPickerComponent({
          pickerOptions: this.pickerOptions,
          // onSelect: (uri: string): void => this.onSelect(uri),
          // onDeselect: (uri: string): void => this.onDeselect(uri),
          onItemClicked: (itemInfo: ItemInfo, clickType: ClickType): boolean => this.onItemClicked(itemInfo,
            clickType), // This API can replace the preceding two APIs.
          onEnterPhotoBrowser: (photoBrowserInfo: PhotoBrowserInfo): boolean => this.onEnterPhotoBrowser(photoBrowserInfo),
          onExitPhotoBrowser: (photoBrowserInfo: PhotoBrowserInfo): boolean => this.onExitPhotoBrowser(photoBrowserInfo),
          onPickerControllerReady: (): void => this.onPickerControllerReady(),
          onPhotoBrowserChanged: (browserItemInfo: BaseItemInfo): boolean => this.onPhotoBrowserChanged(browserItemInfo),
          onSelectedItemsDeleted: this.selectedItemsDeletedCallback,
          onExceedMaxSelected: this.exceedMaxSelectedCallback,
          onCurrentAlbumDeleted: this.currentAlbumDeletedCallback,
          onVideoPlayStateChanged: this.videoPlayStateChangedCallback,
          pickerController: this.pickerController,
        }).height('60%').width('100%')

        // Simulate the selection bar at the bottom of the application.
        if (this.isBrowserShow) {
          Row() {
            ForEach(this.assets, async (asset: photoAccessHelper.PhotoAsset, index) => {
              if (asset.uri === this.currentUri) {
                Image(this.thumbnail[index])
                  .height('10%')
                  .width('10%')
                  .onClick(() => {
                  })
                  .borderWidth(1)
                  .borderColor('red')
              } else {
                Image(this.thumbnail[index]).height('10%').width('10%').onClick(() => {
                  this.pickerController.setData(DataType.SET_SELECTED_URIS, this.selectUris);
                  this.pickerController.setPhotoBrowserItem(asset.uri, PhotoBrowserRange.ALL);
                })
              }
            }, (uri: string) => JSON.stringify(uri))
          }
        } else {
          Button('Preview').width('33%').height('5%').onClick(async () => {
            if (this.selectUris.length > 0) {
              this.thumbnail = [];
              this.assets = [];
              for (let selectUri of this.selectUris) {
                let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
                predicates.equalTo(photoAccessHelper.PhotoKeys.URI, selectUri);
                let fetchOptions: photoAccessHelper.FetchOptions = {
                  fetchColumns: [],
                  predicates: predicates
                };
                let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
                let photoHelper = photoAccessHelper.getPhotoAccessHelper(context);
                let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> =
                  await photoHelper.getAssets(fetchOptions);
                let asset = await fetchResult.getFirstObject()
                this.assets.push(asset);
                this.thumbnail.push(await asset.getThumbnail())
              }
              this.pickerController.setPhotoBrowserItem(this.selectUris[0], PhotoBrowserRange.SELECTED_ONLY);
            }
          })
        }
      }
    }
  }
}
```
