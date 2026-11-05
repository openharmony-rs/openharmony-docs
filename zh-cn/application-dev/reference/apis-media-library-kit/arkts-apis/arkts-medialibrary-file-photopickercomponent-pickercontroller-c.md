# PickerController

```TypeScript
export declare class PickerController
```

应用可通过PickerController向picker组件发送数据。

> **说明：** 
> 
> 调用本接口前需确保onPickerControllerReady回调已触发，否则接口调用不生效。

**起始版本：** 12

**装饰器类型：** @Observed

<!--Device-unnamed-export declare class PickerController--><!--Device-unnamed-export declare class PickerController-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { PhotoPickerComponent, PickerController, PickerOptions, DataType, BaseItemInfo, ItemInfo, PhotoBrowserInfo, AnimatorParams, MaxSelected, ItemType, ClickType, PickerOrientation, SelectMode, PickerColorMode, ReminderMode, MaxCountType, PhotoBrowserRange, PhotoBrowserUIElement, ItemsDeletedCallback, ExceedMaxSelectedCallback, CurrentAlbumDeletedCallback, videoPlayStateChangedCallback, MovingPhotoBadgeStateChangedCallback, UpdatablePickerConfigs, SingleLineConfig, BadgeConfig, PreselectedInfo, SaveMode, BadgeType, VideoPlayerState, ItemDisplayRatio, ScrollStopAtStartCallback, ItemClickedNotifyCallback, ScrollStopAtEndCallback, PhotoBrowserChangeStartCallback, PinchGridSwitchedCallback, ErrorCallback, ClickResult, PickerError } from '@kit.MediaLibraryKit';
```

## addData

```TypeScript
addData(dataType: DataType, data: Object): void
```

应用可通过该接口向picker组件发送增加配置数据。通过DataType来区分具体发送的数据类型。在API version 23之前，该方法仅支持SET_BADGE_CONFIGS类型。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-addData(dataType: DataType, data: Object): void--><!--Device-PickerController-addData(dataType: DataType, data: Object): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataType | [DataType](arkts-medialibrary-file-photopickercomponent-datatype-e.md) | 是 | 发送增加配置数据的数据类型。 |
| data | Object | 是 | 发送的增加配置数据。 |

## completed

```TypeScript
completed(): Promise<CompletedResult>
```

应用可通过该接口，在Picker界面完成选择操作后获取完整现场数据，下一次启动Picker时可以使用该数据恢复现场。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-completed(): Promise<CompletedResult>--><!--Device-PickerController-completed(): Promise<CompletedResult>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CompletedResult](arkts-medialibrary-file-photopickercomponent-completedresult-c.md)&gt; | Promise对象，返回恢复现场的信息。 |

## deleteData

```TypeScript
deleteData(dataType: DataType, data: Object): void
```

应用可通过该接口向picker组件发送移除配置数据。通过DataType来区分具体发送的数据类型，该方法仅支持SET_BADGE_CONFIGS类型。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-deleteData(dataType: DataType, data: Object): void--><!--Device-PickerController-deleteData(dataType: DataType, data: Object): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataType | [DataType](arkts-medialibrary-file-photopickercomponent-datatype-e.md) | 是 | 发送移除配置数据的数据类型。 |
| data | Object | 是 | 发送的移除配置数据。 |

## enterSearchPage

```TypeScript
enterSearchPage(): Promise<void>
```

进入Picker的搜索页面。

呼叫生效的前提条件：-picker已经被初始化（onPickerControllerReady已经被调用）。-选择器选项`isSearchSupported`设置为`false`。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-enterSearchPage(): Promise<void>--><!--Device-PickerController-enterSearchPage(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800202](../errorcode-medialibrary.md#23800202-非法场景调用错误) | Invalid call context. That is, one of the following conditions is met:         1. The picker is not ready (onPickerControllerReady has not been invoked).         2. The search UI is rendered by the picker itself (that is, `isSearchSupported` is set to `true`).         3. The picker is in the photo browsing view. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |

## exitPhotoBrowser

```TypeScript
exitPhotoBrowser(): void
```

应用可通过该接口，向picker发送退出大图的通知。

> **说明：** 
> 
> 当PickerOptions.singleLineConfig配置为单行模式时，本接口调用将无效。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-exitPhotoBrowser(): void--><!--Device-PickerController-exitPhotoBrowser(): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## exitSearchPage

```TypeScript
exitSearchPage(): Promise<void>
```

退出搜索页面，选择器返回默认相册网格。

前提条件：-选择器当前处于搜索状态（PickerState.SEARCH）。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-exitSearchPage(): Promise<void>--><!--Device-PickerController-exitSearchPage(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800202](../errorcode-medialibrary.md#23800202-非法场景调用错误) | Invalid call context: the picker is not in the search state. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |

## navigateBackInSearchPage

```TypeScript
navigateBackInSearchPage(): Promise<void>
```

Navigates back one level within the search page.在搜索页面中返回一层。第一个调用从搜索结果页面返回到搜索推荐页面。并且随后的调用从搜索推荐页面返回到默认的相册网格（相当于exitSearch）。

前提条件：-选择器当前处于搜索状态（PickerState.SEARCH）。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-navigateBackInSearchPage(): Promise<void>--><!--Device-PickerController-navigateBackInSearchPage(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800202](../errorcode-medialibrary.md#23800202-非法场景调用错误) | Invalid call context: the picker is not in the search state. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |

## replacePhotoPickerPreview

```TypeScript
replacePhotoPickerPreview(originalUri: string, newUri: string, callback: AsyncCallback<void>): void
```

应用可通过该接口，将图片选择器组件中用户勾选的图片替换为应用后期编辑修改后的图片。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-replacePhotoPickerPreview(originalUri: string, newUri: string, callback: AsyncCallback<void>): void--><!--Device-PickerController-replacePhotoPickerPreview(originalUri: string, newUri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| originalUri | string | 是 | 原URI，将会被替换掉的URI。 |
| newUri | string | 是 | 新URI，即替换后的URI。期望在图片选择器组件上替换originalUri显示的、暂存在应用沙箱的图片或视频的URI。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 调用接口完成替换后的回调。 |

## saveTrustedPhotoAssets

```TypeScript
saveTrustedPhotoAssets(trustedUris: Array<string>, callback: AsyncCallback<Array<string>>,
    configs?: Array<photoAccessHelper.PhotoCreationConfig>, saveMode?: SaveMode): void
```

应用可通过该接口，保存对应URI列表的文件。使用时，一般结合[replacePhotoPickerPreview](#replacephotopickerpreview)接口使用，将替换显示成功后的应用沙箱图片/视频newUris保存到图库。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-saveTrustedPhotoAssets(trustedUris: Array<string>, callback: AsyncCallback<Array<string>>,    configs?: Array<photoAccessHelper.PhotoCreationConfig>, saveMode?: SaveMode): void--><!--Device-PickerController-saveTrustedPhotoAssets(trustedUris: Array<string>, callback: AsyncCallback<Array<string>>,    configs?: Array<photoAccessHelper.PhotoCreationConfig>, saveMode?: SaveMode): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| trustedUris | Array&lt;string&gt; | 是 | 需要保存到图库的应用沙箱图片/视频URI。trustedUris一般来自[replacePhotoPickerPreview](#replacephotopickerpreview)替换显示成功的newUri。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 返回保存后新生成的媒体库文件对应的URI。 |
| configs | Array&lt;[photoAccessHelper.PhotoCreationConfig](arkts-medialibrary-photoaccesshelper-photocreationconfig-i.md)&gt; | 否 | 需要保存的文件对应的配置参数。<br>**注意：** <br>1. 传入subtype选项，配置项不生效，仅支持保存DEFAULT类型图片。<br>默认使用trustedUris对应mediaItem的title、fileNameExtension和photoType值，且subtype固定为DEFAULT。<br>2. 该参数在[SaveMode](arkts-medialibrary-file-photopickercomponent-savemode-e.md)为OVERWRITE下不生效。 |
| saveMode | [SaveMode](arkts-medialibrary-file-photopickercomponent-savemode-e.md) | 否 | 图片保存模式。<br>默认使用SAVE_AS模式保存为新图片。 |

## saveTrustedPhotoAssetsEx

```TypeScript
saveTrustedPhotoAssetsEx(trustedUris: Array<string>,settings?: Array<photoAccessHelper.CreationSetting>,
    saveMode?: SaveMode): Promise<Array<string>>
```

应用可通过该接口保存对应URI列表中的文件。使用Promise异步回调。

> **说明：** 
> 
> 此接口通常与[replacePhotoPickerPreview](#replacephotopickerpreview)接口结合使用，以保存替换显示成功后的应用沙箱图片或视频
> newUris到图库。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-saveTrustedPhotoAssetsEx(trustedUris: Array<string>,settings?: Array<photoAccessHelper.CreationSetting>,    saveMode?: SaveMode): Promise<Array<string>>--><!--Device-PickerController-saveTrustedPhotoAssetsEx(trustedUris: Array<string>,settings?: Array<photoAccessHelper.CreationSetting>,    saveMode?: SaveMode): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| trustedUris | Array&lt;string&gt; | 是 | 需要保存到图库的应用沙箱图片或视频URI。<br>trustedUris一般来自[replacePhotoPickerPreview](#replacephotopickerpreview)替换显示成功后的应用沙箱图片或视频newUri。 |
| settings | Array&lt;[photoAccessHelper.CreationSetting](arkts-medialibrary-photoaccesshelper-creationsetting-i.md)&gt; | 否 | 需要保存的文件对应的配置参数。<br>默认使用trustedUris对应mediaItem的title、fileNameExtension和photoType值。 |
| saveMode | [SaveMode](arkts-medialibrary-file-photopickercomponent-savemode-e.md) | 否 | 图片或视频的保存模式。<br>默认使用SAVE_AS模式保存为新图片。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回保存后新生成的媒体库文件对应的URI数组。 |

## search

```TypeScript
search(searchInfo: SearchInfo): Promise<void>
```

使用给定的搜索信息调用选择器搜索功能。picker显示搜索结果页面和onPickerStateChanged回调如果选择器尚未处于搜索状态，则使用PickerState.SEARCH调用。

前提条件：-选择器当前处于搜索状态（PickerState.SEARCH）。如果picker处于默认状态，则先调用enterSearch。-`searchInfo.text`和`searchInfo.smartEntityIds`至少有一个为非空。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-search(searchInfo: SearchInfo): Promise<void>--><!--Device-PickerController-search(searchInfo: SearchInfo): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchInfo | [SearchInfo](arkts-medialibrary-file-photopickercomponent-searchinfo-c.md) | 是 | 搜索信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameter check failed: empty search info or invalid entity id. |
| [23800202](../errorcode-medialibrary.md#23800202-非法场景调用错误) | Invalid call context: the picker is not in the search state. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |

## setData

```TypeScript
setData(dataType: DataType, data: Object): void
```

应用可通过该接口向picker组件发送数据，并通过DataType来区分具体发送的数据类型。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-setData(dataType: DataType, data: Object): void--><!--Device-PickerController-setData(dataType: DataType, data: Object): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataType | [DataType](arkts-medialibrary-file-photopickercomponent-datatype-e.md) | 是 | 发送数据的数据类型。 |
| data | Object | 是 | 发送的数据。 |

## setMaxSelected

```TypeScript
setMaxSelected(maxSelected: MaxSelected): void
```

应用可通过该接口，实时地设置图片的最大选择数量、视频的最大选择数量以及总的最大选择数量。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-setMaxSelected(maxSelected: MaxSelected): void--><!--Device-PickerController-setMaxSelected(maxSelected: MaxSelected): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxSelected | [MaxSelected](arkts-medialibrary-file-photopickercomponent-maxselected-c.md) | 是 | 最大选择数量。 |

## setMovingPhotoState

```TypeScript
setMovingPhotoState(movingPhotoState: photoAccessHelper.MovingPhotoBadgeStateType): Promise<void>
```

应用通过该接口，设置大图浏览下当前动态照片的效果。使用Promise异步回调。

仅在大图浏览下设置生效，不支持设置NOT_MOVING_PHOTO。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-setMovingPhotoState(movingPhotoState: photoAccessHelper.MovingPhotoBadgeStateType): Promise<void>--><!--Device-PickerController-setMovingPhotoState(movingPhotoState: photoAccessHelper.MovingPhotoBadgeStateType): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| movingPhotoState | [photoAccessHelper.MovingPhotoBadgeStateType](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md) | 是 | 设置当前大图动态照片的状态。仅支持设置MOVING_PHOTO_ENABLED和MOVING_PHOTO_DISABLED，不支持设置NOT_MOVING_PHOTO。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameters validate failed, possible causes:         1. An invalid enumeration value was passed. Only MOVING_PHOTO_ENABLED and MOVING_PHOTO_DISABLED are supported for configuration. |
| [23800202](../errorcode-medialibrary.md#23800202-非法场景调用错误) | Invalid call context. Possible causes:         1. The API is called outside the photo browsing scenario.         2. The API is called when isMovingPhotoBadgeShown is already set to true. |

## setPhotoBrowserItem

```TypeScript
setPhotoBrowserItem(uri: string, photoBrowserRange?: PhotoBrowserRange): void
```

应用可通过该接口，切换图片选择器组件至大图浏览模式浏览图片；当已处于大图浏览模式时，切换浏览的图片。

> **说明：** 
> 
> 当PickerOptions.singleLineConfig配置为单行模式时，本接口调用将无效。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-setPhotoBrowserItem(uri: string, photoBrowserRange?: PhotoBrowserRange): void--><!--Device-PickerController-setPhotoBrowserItem(uri: string, photoBrowserRange?: PhotoBrowserRange): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 指定大图浏览的图片URI。应用仅可指定用户已选择的图片，未选择的图片不生效。 |
| photoBrowserRange | [PhotoBrowserRange](arkts-medialibrary-file-photopickercomponent-photobrowserrange-e.md) | 否 | 打开大图浏览模式后，左右滑动切换浏览图片的范围，可配置仅浏览用户选择的或浏览全部图片，视频。默认：PhotoBrowserRange.ALL。浏览全部图片，视频。 |

## setPhotoBrowserUIElementVisibility

```TypeScript
setPhotoBrowserUIElementVisibility(elements: Array<PhotoBrowserUIElement>, isVisible: boolean): void
```

应用可通过该接口，设置大图页除预览组件外的其他UI元素是否可见。不设置则默认可见。

> **说明：** 
> 
> 当PickerOptions.singleLineConfig配置为单行模式时，本接口调用将无效。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-setPhotoBrowserUIElementVisibility(elements: Array<PhotoBrowserUIElement>, isVisible: boolean): void--><!--Device-PickerController-setPhotoBrowserUIElementVisibility(elements: Array<PhotoBrowserUIElement>, isVisible: boolean): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elements | Array&lt;[PhotoBrowserUIElement](arkts-medialibrary-file-photopickercomponent-photobrowseruielement-e.md)&gt; | 是 | 大图页大图预览组件外其他UI元素。 |
| isVisible | boolean | 是 | 设置的elements元素是否可见。true表示可见，false表示不可见。默认值为false。 |

## updatePickerOptions

```TypeScript
updatePickerOptions(updateConfig: UpdatablePickerConfigs): Promise<void>
```

应用通过该接口，更新图片选择器组件的属性。使用Promise异步回调。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-PickerController-updatePickerOptions(updateConfig: UpdatablePickerConfigs): Promise<void>--><!--Device-PickerController-updatePickerOptions(updateConfig: UpdatablePickerConfigs): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| updateConfig | [UpdatablePickerConfigs](arkts-medialibrary-file-photopickercomponent-updatablepickerconfigs-c.md) | 是 | 支持更新的图片选择器组件属性，为[PickerOptions](arkts-medialibrary-file-photopickercomponent-pickeroptions-c.md)的子集。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |
