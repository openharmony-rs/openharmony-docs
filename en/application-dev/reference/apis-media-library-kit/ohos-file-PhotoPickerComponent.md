# @ohos.file.PhotoPickerComponent (PhotoPickerComponent)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xuchangda-->
<!--SE: @guxinggang-->
<!--TSE: @wangbeibei-->

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

## Properties

The [universal properties](../apis-arkui/arkui-ts/ts-component-general-attributes.md) are supported.

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
| onEnterPhotoBrowser     | (photoBrowserInfo: [PhotoBrowserInfo](#photobrowserinfo)) => boolean             | No  | - | Callback to be invoked when the photo browser page is displayed. The callback returns photo browser information to the application.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                                                                    |
| onExitPhotoBrowser      | (photoBrowserInfo: [PhotoBrowserInfo](#photobrowserinfo)) => boolean             | No  | - | Callback to be invoked when the photo browser page exits. The callback returns photo browser information to the application.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                                                                      |
| onPickerControllerReady | () => void                                                                       | No  | - | Callback to be invoked when **pickerController** is available.<br>The **PickerController** APIs can be called only after this callback is invoked.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                              |
| onPhotoBrowserChanged   | (browserItemInfo: [BaseItemInfo](#baseiteminfo)) => boolean                      | No  | - | Callback to be invoked when the photo browser page is swiped left or right. The callback returns photo browser information to the application. The setting takes effect only in multi-selection mode.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                                                                    |
| onSelectedItemsDeleted<sup>13+</sup>  | [ItemsDeletedCallback](#itemsdeletedcallback13)                                  | No  | - | Callback to be invoked when the selected items are deleted. This callback returns information about the deleted items to the application.<br>**Atomic service API**: This API can be used in atomic services since API version 13.                                                                                                                                                                                                                                                                                                                             |
| onExceedMaxSelected<sup>13+</sup>     | [ExceedMaxSelectedCallback](#exceedmaxselectedcallback13)                          | No  | - | Callback to be invoked when the number of selected media assets exceeds the limit (maximum number of selected images, selected videos, or selected items).<br>- If the number of selected images reaches the maximum but does not reach the maximum count of selected items, **exceedMaxCountType** in the callback is [MaxCountType](#maxcounttype).PHOTO_MAX_COUNT.<br>- If the number of selected videos reaches the maximum but does not reach the maximum count of selected items, **exceedMaxCountType** in the callback is [MaxCountType](#maxcounttype).VIDEO_MAX_COUNT.<br>- If the number of selected media assets reaches the maximum count of selected items, **exceedMaxCountType** in the callback is [MaxCountType](#maxcounttype).TOTAL_MAX_COUNT.<br>**Atomic service API**: This API can be used in atomic services since API version 13.|
| onCurrentAlbumDeleted<sup>13+</sup>   | [CurrentAlbumDeletedCallback](#currentalbumdeletedcallback13)                    | No  | - | Callback to be invoked when the current album is deleted.<br>The album is specified by **currentAlbumUri** in pickerController.[setData](#setdata)([DataType](#datatype).SET_ALBUM_URI, currentAlbumUri).<br>To refresh the grid page to display the default album after the current album is deleted, you can set the title bar name to the default album name, for example, **Photos and videos**, **Photos**, or **Videos**, and call pickerController.[setData](#setdata)([DataType](#datatype).SET_ALBUM_URI, '') with an empty string.<br>**Atomic service API**: This API can be used in atomic services since API version 13.                                 |
| onVideoPlayStateChanged<sup>14+</sup>   | [videoPlayStateChangedCallback](#videoplaystatechangedcallback14)                    | No  | - | Callback to be invoked when the video playback state on a photo browser page changes.<br>**Atomic service API**: This API can be used in atomic services since API version 14.                                 |
| pickerController        | [PickerController](#pickercontroller)                                            | No  | @ObjectLink | Instance used to send data to the **PhotoPickerComponent**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                                                                                                                                                                                                                                            |

## PickerOptions

Describes the configuration of a Picker. It inherits from [BaseSelectOptions](arkts-apis-photoAccessHelper-class.md#baseselectoptions12).

 

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                             | Type                                     | Mandatory | Description                                                                      |
|---------------------------------|-----------------------------------------|-----|--------------------------------------------------------------------------|
| checkBoxColor                   | string                                  | No  | Background color of the check box. The value is an 8-digit hexadecimal color code.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                  |
| backgroundColor                 | string                                  | No  | Background color of the Picker grid page. The value is an 8-digit hexadecimal color code.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                            |
| isRepeatSelectSupported         | boolean                                 | No  | Whether to support repeat selection of a single image. The value **true** means that a single image can be repeatedly selected. The default value is **false**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                  |
| checkboxTextColor               | string                                  | No  | Text color in the check box. The value is an 8-digit hexadecimal color code. (This capability is not supported currently.)<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                       |
| photoBrowserBackgroundColorMode | [PickerColorMode](#pickercolormode)     | No  | Background color of the photo browser page. The options are **AUTO**, **LIGHT**, and **DARK**. The default value is **AUTO**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                       |
| maxSelectedReminderMode         | [ReminderMode](#remindermode)           | No  | Mode of the reminder when the number of selected items reaches the maximum. The options are **NONE**, **TOAST**, and **MASK**. The default value **TOAST**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                        |
| orientation                     | [PickerOrientation](#pickerorientation) | No  | Sliding preview direction of the grid page. The options are **HORIZONTAL** and **VERTICAL**. The default value is **VERTICAL**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                |
| selectMode                      | [SelectMode](#selectmode)               | No  | Select mode, which can be **SINGLE_SELECT** or **MULTI_SELECT**. The default value is **MULTI_SELECT**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                     |
| maxPhotoSelectNumber            | number                                  | No  | Maximum number of images that can be selected. The maximum value is **500**, which is limited by **MaxSelected**. The default value is **500**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                          |
| maxVideoSelectNumber            | number                                  | No  | Maximum number of videos that can be selected. The maximum value is **500**, which is limited by **MaxSelected**. The default value is **500**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                          |
| isSlidingSelectionSupported<sup>13+</sup>     | boolean                                 | No  | Whether sliding selection (selecting multiple items by sliding finger across the screen) is supported. The value **true** means that sliding selection is supported. By default, it is not supported. This parameter is not available for repeat selection.<br>**Atomic service API**: This API can be used in atomic services since API version 13.                                           |
| photoBrowserCheckboxPosition<sup>13+</sup>    | [number, number]                        | No  | Position of the check box on the photo browser page. The first parameter specifies the offset in the X direction, and the second parameter specifies the offset in the Y direction. The value range is 0-1, which indicates the offset (from 0% to 100%) to the upper left corner of the component. The default value is [0, 0].<br>**Atomic service API**: This API can be used in atomic services since API version 13.|
| gridMargin<sup>14+</sup>        | [Margin](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#margin)                        | No  | Margin of the component on a grid page.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| photoBrowserMargin<sup>14+</sup>    | [Margin](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#margin)                        | No  | Margin of the component on a photo browser page.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| singleLineConfig<sup>20+</sup>             | [SingleLineConfig](#singlelineconfig)                                                | No  | Single-line display mode of a grid page. In single-line mode, the component does not provide functions for viewing a larger image. The component does not support callbacks related to large images, and the PickerController does not support APIs related to large images, making API calls ineffective.<br>**Atomic service API**: This API can be used in atomic services since API version 20.     |  
| uiComponentColorMode<sup>20+</sup>             | [PickerColorMode](#pickercolormode)                                                | No  | Picker color mode. Dark/Light color mode (excluding the background color) of other components on the Picker grid page, including the search box, camera entry, safety tips for using Gallery, and recommendation bubble. This property is usually used together with **backgroundColor**. The default value is **PickerColorMode.AUTO**, which follows the system's dark/light color mode.<br>When setting this property, avoid using **PickerColorMode.LIGHT** with a dark backgroundColor, as it may make components or text hard to see. Avoid using **PickerColorMode.DARK** with a light backgroundColor for the same reason.<br>**Atomic service API**: This API can be used in atomic services since API version 20. |
| gridStartOffset<sup>20+</sup>    | number                              | No  | Space between the top of the component and the first row of the grid thumbnail. The default value is **0**, in vp.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| gridEndOffset<sup>20+</sup>    | number                              | No  | Space between the bottom of the component and the last row of the grid thumbnail. The default value is **0**, in vp.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

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

## PickerController

Defines an instance used to send data to the **PhotoPickerComponent**.

**Decorator Type**: @Observed

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

### setData

setData(dataType: DataType, data: Object): void

Sends data of the specified type to **PhotoPickerComponent**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

|  Name       | Type                                   | Mandatory | Description |
| ------------------------- | ------------------ | ----- | --------------- |
| dataType | [DataType](#datatype) | Yes| Type of the data to send.|
| data | Object | Yes| Data to send.| 

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
| configs | Array&lt;[photoAccessHelper.PhotoCreationConfig](arkts-apis-photoAccessHelper-i.md#photocreationconfig12)&gt;          | No| Configuration parameters corresponding to the original files.            |
| saveMode | [SaveMode](#savemode15)           | No| Mode for saving the files.            |

## BaseItemInfo

Represents basic image and video information.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name    | Type   | Mandatory | Description                                               |
|----------|--------|-----|---------------------------------------------------|
| uri      | string                | No  | Image or video URI. This parameter is mandatory when **itemType** is **THUMBNAIL**. Otherwise, it is left empty.           |
| mimeType | string                | No  | MIME type of the image or video. This parameter is mandatory when **itemType** is **THUMBNAIL**. Otherwise, it is left empty.      |
| width    | number                | No  | Width of the image or video, in pixels. This parameter is mandatory when **itemType** is **THUMBNAIL**. Otherwise, it is left empty.      |
| height   | number                | No  | Height of the image or video, in pixels. This parameter is mandatory when **itemType** is **THUMBNAIL**. Otherwise, it is left empty.      |
| size     | number                | No  | Size of the image or video, in bytes. This parameter is mandatory when **itemType** is **THUMBNAIL**. Otherwise, it is left empty.    |
| duration   | number                | No  | Video duration, in ms. This parameter is mandatory when **itemType** is **THUMBNAIL**. Otherwise, it is left empty. The value **-1** indicates an image.|

## ItemInfo

Represents image and video information. It inherits from [BaseItemInfo](#baseiteminfo), adding the private parameter **itemType**.
 

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name    | Type   | Mandatory | Description                                               |
|----------|--------|-----|---------------------------------------------------|
| itemType | [ItemType](#itemtype) | No  | Type of the item, which can be **THUMBNAIL** or **CAMERA**.                     |

## PhotoBrowserInfo

Represents information about the photo browser page.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name    | Type   | Mandatory | Description    |
|----------|--------|-----|---------|
| animatorParams | [AnimatorParams](#animatorparams) | No  | Animation for entering or exiting the photo browser page.|

## AnimatorParams

Animation parameters for entering or exiting the photo browser page.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name    | Type   | Mandatory | Description          |
|----------|--------|-----|--------------|
| duration | number  | No           | Animation duration, in ms.|
| curve      | [Curve](../apis-arkui/js-apis-curve.md#curve) &verbar; [ICurve](../apis-arkui/js-apis-curve.md#icurve9) &verbar; string | No  | Animation curve.       |

## MaxSelected

Represents the maximum number of media assets that can be selected at a time.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name    | Type   | Mandatory | Description    |
|----------|--------|-----|---------|
| data | Map&lt;[MaxCountType](#maxcounttype), number&gt; | No            | Maximum number of media assets (images, videos, or both) that can be selected at a time.|

## SingleLineConfig

Represents the single-line display mode. In single-line mode, the component does not provide functions for viewing a larger image. The component does not support callbacks related to large images, and the PickerController does not support APIs related to large images, making API calls ineffective.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name| Type                                            | Mandatory| Description                                                                          |
| ---- | ------------------------------------------------ | ---- | ------------------------------------------------------------------------------ |
| itemDisplayRatio | [ItemDisplayRatio](#itemdisplayratio20) | No  | Aspect ratio for grid display. Both 1:1 and the original image aspect ratio are supported. The default value is 1:1.|
| itemBorderRadius | [Length](../apis-arkui/arkui-ts/ts-types.md#length) &verbar; [BorderRadiuses](../apis-arkui/arkui-ts/ts-types.md#borderradiuses9) &verbar; [LocalizedBorderRadiuses](../apis-arkui/arkui-ts/ts-types.md#localizedborderradiuses12) | No  | Rounded corner radius for grid items.|
| itemGap | [Length](../apis-arkui/arkui-ts/ts-types.md#length) | No  | Spacing between grid items.|

## DataType

Enumerates the types of data sent from **PickerController** to the **PhotoPickerComponent**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name               | Value  | Description                                                                                                                |
|-------------------|-----|--------------------------------------------------------------------------------------------------------------------|
| SET_SELECTED_URIS | 1   | Send a list of selected items to instruct the **PhotoPickerComponent** to refresh the selection status. A string array needs to be passed in.<br>For example, after an image is deleted from an application's page, the application calls **setData()** to notify the **PhotoPickerComponent** of the remaining selected items. Then, the **PhotoPickerComponent** refreshes the check box status.|
| SET_ALBUM_URI | 2   | Send the selected album to instruct the **PhotoPickerComponent** to refresh the album data. A string array needs to be passed in.<br>For example, after an album is selected from an application's page, the application calls **setData** to notify the **PhotoPickerComponent** of the URI of the selected album. Then, the **PhotoPickerComponent** refreshes the album data.|

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
                let photoHelper = photoAccessHelper.getPhotoAccessHelper(getContext());
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
