# PickerController

Defines an instance used to send data to the **PhotoPickerComponent**.

**Since:** 12

**Decorator:** @Observed

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## addData

```TypeScript
addData(dataType: DataType, data: Object): void
```

Sends additional configuration data to the **PhotoPickerComponent**. The [DataType](arkts-medialibrary-file-photopickercomponent-datatype-e.md) parameter identifies the type of data to send. In versions earlier than API version 23, only the **SET_BADGE_CONFIGS** type is supported.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataType | [DataType](arkts-medialibrary-file-photopickercomponent-datatype-e.md) | Yes | Type of additional configuration data to send. |
| data | Object | Yes | Additional configuration data to send. |

## completed

```TypeScript
completed(): Promise<CompletedResult>
```

This API is used by an application to obtain the complete data after a selection operation is completed on the Picker page. The data can be used to restore the scene when the Picker is started next time.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CompletedResult](arkts-medialibrary-file-photopickercomponent-completedresult-c.md)&gt; | Promise used to return the information about the restored scene. |

## deleteData

```TypeScript
deleteData(dataType: DataType, data: Object): void
```

Sends removal configuration data to the **PhotoPickerComponent**. The [DataType](arkts-medialibrary-file-photopickercomponent-datatype-e.md) parameter identifies the type of data to send, and only the **SET_BADGE_CONFIGS** type is supported currently.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataType | [DataType](arkts-medialibrary-file-photopickercomponent-datatype-e.md) | Yes | Type of removal configuration data to send. |
| data | Object | Yes | Removal configuration data to send. |

## exitPhotoBrowser

```TypeScript
exitPhotoBrowser(): void
```

Exits the photo browser page.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## replacePhotoPickerPreview

```TypeScript
replacePhotoPickerPreview(originalUri: string, newUri: string, callback: AsyncCallback<void>): void
```

Replaces the image selected by the user in the **PhotoPickerComponent** with the image edited by the application.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| originalUri | string | Yes | URI of the original image, which will be replaced. |
| newUri | string | Yes | URI of the new image. The new image is temporarily stored in the application sandbox path. Therefore, this URI specifies a directory in the application sandbox path. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked when image replacement is complete. |

## saveTrustedPhotoAssets

```TypeScript
saveTrustedPhotoAssets(trustedUris: Array<string>, callback: AsyncCallback<Array<string>>,
    configs?: Array<photoAccessHelper.PhotoCreationConfig>, saveMode?: SaveMode): void
```

Saves files in a URI list. Generally, this API is used together with [replacePhotoPickerPreview](#replacephotopickerpreview) to save the new images or videos in the application sandbox path to Gallery.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| trustedUris | Array&lt;string&gt; | Yes | URIs of the images or videos in the application sandbox path. Generally, **trustedUris** comes from **newUri** of new images generated by [replacePhotoPickerPreview](#replacephotopickerpreview). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | URIs of the new files in Gallery. |
| configs | Array&lt;[photoAccessHelper.PhotoCreationConfig](arkts-medialibrary-photoaccesshelper-photocreationconfig-i.md)&gt; | No | Configuration parameters corresponding to the original files. <br>**NOTE:** <br>1. If a **subtype** option is passed, the configuration does not take effect. Only **DEFAULT** images can be saved. <br>By default, the values of **title**, **fileNameExtension**, and **photoType** of **mediaItem** corresponding to **trustedUris** are used, and the value of **subtype** is fixed to **DEFAULT**. <br>2. This parameter does not take effect when [SaveMode](arkts-medialibrary-file-photopickercomponent-savemode-e.md) is set to **OVERWRITE**. |
| saveMode | [SaveMode](arkts-medialibrary-file-photopickercomponent-savemode-e.md) | No | Mode for saving the files.<br>By default, the **SAVE_AS** mode is used to save the files as new files. |

## saveTrustedPhotoAssetsEx

```TypeScript
saveTrustedPhotoAssetsEx(trustedUris: Array<string>,settings?: Array<photoAccessHelper.CreationSetting>,
    saveMode?: SaveMode): Promise<Array<string>>
```

Saves files in a URI list. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is usually used together with
> [replacePhotoPickerPreview](#replacephotopickerpreview) to save the new images or videos in
> the application sandbox path to Gallery.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| trustedUris | Array&lt;string&gt; | Yes | URIs of the images or videos in the application sandbox path. <br>**trustedUris** is usually the **newUri** of the images or videos in the application sandbox path that are successfully replaced by [replacePhotoPickerPreview](#replacephotopickerpreview). |
| settings | Array&lt;[photoAccessHelper.CreationSetting](arkts-medialibrary-photoaccesshelper-creationsetting-i.md)&gt; | No | Configuration parameters corresponding to the original files.<br>By default, the **title**, **fileNameExtension**, and **photoType** values of **mediaItem** corresponding to **trustedUris** are used. |
| saveMode | [SaveMode](arkts-medialibrary-file-photopickercomponent-savemode-e.md) | No | Mode for saving images or videos.<br>By default, the **SAVE_AS** mode is used to save the files as new files. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the URI of the new asset. |

## setData

```TypeScript
setData(dataType: DataType, data: Object): void
```

Sends data of the specified type to the **PhotoPickerComponent**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataType | [DataType](arkts-medialibrary-file-photopickercomponent-datatype-e.md) | Yes | Type of the data to send. |
| data | Object | Yes | Data to send. |

## setMaxSelected

```TypeScript
setMaxSelected(maxSelected: MaxSelected): void
```

Sets the maximum number of images, videos, or images and videos that can be selected in real time.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxSelected | [MaxSelected](arkts-medialibrary-file-photopickercomponent-maxselected-c.md) | Yes | Maximum number of media assets that can be selected at a time. |

## setMovingPhotoState

```TypeScript
setMovingPhotoState(movingPhotoState: photoAccessHelper.MovingPhotoBadgeStateType): Promise<void>
```

Sets the state of the moving photo on the photo browser page. This API uses a promise to return the result.

This parameter takes effect only on the photo browser page. **NOT_MOVING_PHOTO** cannot be set.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| movingPhotoState | [photoAccessHelper.MovingPhotoBadgeStateType](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md) | Yes | State of the moving photo on the photo browser page. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scene parameters validate failed, possible causes: 1. An invalid enumeration value was passed. Only MOVING_PHOTO_ENABLED and MOVING_PHOTO_DISABLED are supported for configuration; |
| [23800202](../errorcode-medialibrary.md#23800202-invalid-scenario-call) | Invalid call context. Possible causes: 1. The API is called outside the photo browsing scenario. 2. The API is called when isMovingPhotoBadgeShown is already set to true. |

## setPhotoBrowserItem

```TypeScript
setPhotoBrowserItem(uri: string, photoBrowserRange?: PhotoBrowserRange): void
```

Switches from the **PhotoPickerComponent** to the photo browser page or from the photo browser page to the image to be viewed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the image to view. Only the images selected by the user are supported. |
| photoBrowserRange | [PhotoBrowserRange](arkts-medialibrary-file-photopickercomponent-photobrowserrange-e.md) | No | View range on the photo browser page. The value can be **ALL** or **SELECTED_ONLY**. The default value is **ALL**, which means to view all images and videos. |

## setPhotoBrowserUIElementVisibility

```TypeScript
setPhotoBrowserUIElementVisibility(elements: Array<PhotoBrowserUIElement>, isVisible: boolean): void
```

Sets whether other UI elements are visible on the photo browser page. By default, other UI elements are visible.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elements | Array&lt;[PhotoBrowserUIElement](arkts-medialibrary-file-photopickercomponent-photobrowseruielement-e.md)&gt; | Yes | Other UI elements on the photo browser page. |
| isVisible | boolean | Yes | Whether the specified elements are visible. **true**: visible; **false**: not visible. The default value is **false**. |

## updatePickerOptions

```TypeScript
updatePickerOptions(updateConfig: UpdatablePickerConfigs): Promise<void>
```

Updates the attributes of the **PhotoPickerComponent**. This API uses a promise to return the result.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| updateConfig | [UpdatablePickerConfigs](arkts-medialibrary-file-photopickercomponent-updatablepickerconfigs-c.md) | Yes | New attributes, which are a subset of [PickerOptions](arkts-medialibrary-file-photopickercomponent-pickeroptions-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
