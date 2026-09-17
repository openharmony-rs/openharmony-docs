# MediaAssetChangeRequest

Represents a media asset change request.

**Inheritance/Implementation:** MediaAssetChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md)

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## addResource

```TypeScript
addResource(type: ResourceType, proxy: PhotoProxy): void
```

Adds resources using **PhotoProxy** data.

> **NOTE:** 
> 
> For the same asset change request, this API cannot be repeatedly called after resources are successfully added.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ResourceType](arkts-medialibrary-photoaccesshelper-resourcetype-e.md) | Yes | Type of the resource to add. |
| proxy | [PhotoProxy](arkts-medialibrary-photoaccesshelper-photoproxy-i-sys.md) | Yes | PhotoProxy data of the resource to add. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## addResourceForPicker

```TypeScript
addResourceForPicker(type: ResourceType, fileUri: string): void
```

Adds a resource using fileUri from file management directory

**Since:** 22

**Required permissions:** ohos.permission.ACCESS_MEDIALIB_THUMB_DB

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ResourceType](arkts-medialibrary-photoaccesshelper-resourcetype-e.md) | Yes | Type of the resource to add. |
| fileUri | string | Yes | Data source of the resource to be added, which is specified by a URI in the application sandbox directory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. You are advised to retry and check the logs. Possible causes:<br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) |  |

## createAssetRequest

```TypeScript
static createAssetRequest(context: Context, displayName: string, options?: PhotoCreateOptions): MediaAssetChangeRequest
```

Creates an asset change request with the specified file name.

The file name must meet the following requirements:

- A valid file name must include a base name and a supported image or video extension.  
- The total length of the file name must be between 1 and 255 characters.  
- The base name must not contain any invalid characters.

Starting from API version 18, the following characters are considered invalid: \ / : * ? " &lt; &gt; |

For API versions 10 to 17, the following characters are considered invalid: . .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| displayName | string | Yes | File name of the image or video to create. |
| options | [PhotoCreateOptions](arkts-medialibrary-photoaccesshelper-photocreateoptions-i-sys.md) | No | Options for creating an image or video asset. |

**Return value:**

| Type | Description |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | **MediaAssetChangeRequest** created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000001 | Invalid display name |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## deleteAssetsPermanentlyWithUri

```TypeScript
static deleteAssetsPermanentlyWithUri(context: Context, assetUris: string[]): Promise<void>
```

Permanently deletes images or videos in batches by URI. The deleted images or videos are not stored in the recycle bin. This API uses a promise to return the result.

> **NOTE:** 
> 
> - Assets that exist only on the local device, on the cloud, or on both the local device and the cloud can be permanently deleted. The deleted assets are not stored in the recycle bin.
> 
> - This operation is irreversible. The deleted assets cannot be restored. Exercise caution when performing this operation.

**Since:** 24

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| assetUris | string[] | Yes | Array of URIs of the images or videos to be deleted. The array can contain a maximum of 500 elements. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by nonsystem application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. The context is empty; <br>2. Asset uri array size is empty or bigger than 500 . |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes:<br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out; |

**Examples**

```TypeScript
async function example(context: Context, assetUri: string) {
    console.info('deleteAssetsPermanentlyWithUri');
    try {
      await photoAccessHelper.MediaAssetChangeRequest.deleteAssetsPermanentlyWithUri(context, [assetUri]);
      console.info('deleteAssetsPermanentlyWithUri success.');
    } catch (err) {
      console.error(`deleteAssetsPermanentlyWithUri failed with error: ${err.code}, ${err.message}`);
    }
}
```

## deleteCloudAssetsWithUri

```TypeScript
static deleteCloudAssetsWithUri(context: Context, assetUris: string[]): Promise<void>
```

Deletes cloud media assets to the trash in batches. This API uses a promise to return the result.

> **NOTE:** 
> 
> - If the assets are only on the local device, no changes are made.
> 
> - If the assets are only in the cloud, they are moved directly to the trash.
> 
> - If the assets are on both the local device and the cloud, after deletion, they only remain on the local device, and the cloud copies are moved in the trash.

**Since:** 22

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| assetUris | string[] | Yes | Array of URIs of the images or videos to be deleted. The array can contain a maximum of 500 elements. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. The context is empty; <br>2. Asset uri array size is empty or bigger than 500 . |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes:<br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out; |

**Examples**

```TypeScript
async function example(context: Context, assetUri: string) {
    console.info('deleteCloudAssetsWithUriDemo');
    try {
      await photoAccessHelper.MediaAssetChangeRequest.deleteCloudAssetsWithUri(context, [assetUri]);
    } catch (err) {
      console.error(`deleteCloudAssetsWithUri failed with error: ${err.code}, ${err.message}`);
    }
}
```

## deleteLocalAssetsPermanently

```TypeScript
static deleteLocalAssetsPermanently(context: Context, assets: Array<PhotoAsset>): Promise<void>
```

Permanently deletes images or videos in batches. This API uses a promise to return the result.

> **NOTE:** 
> 
> This operation is irreversible. The assets deleted cannot be restored. Exercise caution when performing this
> operation.

**Since:** 18

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Array of images or videos to be permanently deleted. The array can contain a maximum of 500 elements. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('deleteAssetsPermanentlyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAssetList: Array<photoAccessHelper.PhotoAsset> = await fetchResult.getAllObjects();
    await photoAccessHelper.MediaAssetChangeRequest.deleteLocalAssetsPermanently(context, photoAssetList);
  } catch (err) {
    console.error(`deleteAssetsPermanentlyDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## deleteLocalAssetsPermanentlyWithUri

```TypeScript
static deleteLocalAssetsPermanentlyWithUri(context: Context, assetUris: Array<string>): Promise<void>
```

Permanently deletes images or video assets in batches by URI. This API uses a promise to return the result.

> **NOTE:** 
> 
> This operation is irreversible. The assets deleted cannot be restored. Exercise caution when performing this
> operation.

**Since:** 19

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| assetUris | Array&lt;string&gt; | Yes | Array of URIs of the images or videos to be permanently deleted. The array can contain a maximum of 500 elements. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| 13900020 | Invalid argument |
| 14000011 | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
    console.info('deleteLocalAssetsPermanentlyWithUriDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
    };
    try {
        let  photoUris: Array<string> = [];
        let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
        let assets: Array<photoAccessHelper.PhotoAsset> = await fetchResult.getAllObjects();
        for (const asset of assets) {
            if (!asset?.uri) {
                continue; 
            }
            let uri:string = asset.uri.trim();
            photoUris.push(uri);
        }
        await photoAccessHelper.MediaAssetChangeRequest.deleteLocalAssetsPermanentlyWithUri(context, photoUris);
    } catch (err) {
    console.error(`deleteLocalAssetsPermanentlyWithUriDemo failed with error: ${err.code}, ${err.message}`);
}
}
```

## deleteLocalAssetsWithUri

```TypeScript
static deleteLocalAssetsWithUri(context: Context, assetUris: string[]): Promise<void>
```

Deletes local media assets to the trash in batches. This API uses a promise to return the result.

> **NOTE:** 
> 
> - If the assets are only on the local device, they are moved directly to the trash.
> 
> - If the assets are only in the cloud, no changes are made.
> 
> - If the assets are on both the local device and the cloud, after deletion, they only remain in the cloud, and the local copies are moved in the trash.

**Since:** 22

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| assetUris | string[] | Yes | Array of URIs of the images or videos to be deleted. The array can contain a maximum of 500 elements. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. The context is empty; <br>2. Asset uri array size is empty or bigger than 500 . |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes:<br>1.Database corrupted; <br>2.The file system is abnormal; <br>3.The IPC request timed out; |

**Examples**

```TypeScript
async function example(context: Context, assetUri: string) {
    console.info('deleteLocalAssetsWithUriDemo');
    try {
      await photoAccessHelper.MediaAssetChangeRequest.deleteLocalAssetsWithUri(context, [assetUri]);
    } catch (err) {
      console.error(`deleteLocalAssetsWithUri failed with error: ${err.code}, ${err.message}`);
    }
}
```

## setAppLinkInfo

```TypeScript
setAppLinkInfo(appLink: string): void
```

Sets the information about the app link association.

**Since:** 21

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appLink | string | Yes | Information about the app link association. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: The input parameter's length is not within the valid range. |

**Examples**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';


async function example(asset: photoAccessHelper.PhotoAsset, appLinkInfo: string, context: Context) {
    try {
      let phAccessHelper: photoAccessHelper.PhotoAccessHelper =
        photoAccessHelper.getPhotoAccessHelper(context);
      let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest =
        new photoAccessHelper.MediaAssetChangeRequest(asset);
      assetChangeRequest.setAppLinkInfo(appLinkInfo);
      await phAccessHelper.applyChanges(assetChangeRequest);
    } catch (error) {
      console.error('set appLinkInfo error: ' + error);
      return;
    }
}
```

## setAppLinkState

```TypeScript
setAppLinkState(appLinkState: AppLinkState): void
```

Sets the status of the app link association.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appLinkState | [AppLinkState](arkts-medialibrary-photoaccesshelper-applinkstate-e-sys.md) | Yes | Whether to enable or disable the app link association. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Invoked by non-system applications |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: The input parameter is not within the valid range. |

**Examples**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(asset: photoAccessHelper.PhotoAsset, context: Context) {
    try {
      let phAccessHelper: photoAccessHelper.PhotoAccessHelper =
        photoAccessHelper.getPhotoAccessHelper(context);
      let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest =
        new photoAccessHelper.MediaAssetChangeRequest(asset);
      assetChangeRequest.setAppLinkState(photoAccessHelper.AppLinkState.HAS_NO_LINK);
      await phAccessHelper.applyChanges(assetChangeRequest);
    } catch (error) {
      console.error('set appLink state error: ' + error);
      return;
    }
}
```

## setCameraEditData

```TypeScript
setCameraEditData(editData: MediaAssetEditData): void
```

Saves the camera edited data of an asset.

**Since:** 26.1.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editData | [MediaAssetEditData](arkts-medialibrary-photoaccesshelper-mediaasseteditdata-c-sys.md) | Yes | Edited data to save. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: The input parameter is not within the valid range. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes: 1. Database corrupted. 2. The file system is abnormal. 3. The IPC request timed out. |

## setCameraShotKey

```TypeScript
setCameraShotKey(cameraShotKey: string): void
```

Sets the Key for the Ultra Snapshot feature, which allows the camera to take photos or record videos with the screen off.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraShotKey | string | Yes | Key for the Ultra Snapshot feature, which allows the camera to take photos or record videos with the screen off. (This parameter is available only for the system camera, and the key value is defined by the system camera.) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setCompositeDisplayMode

```TypeScript
setCompositeDisplayMode(compositeDisplayMode: CompositeDisplayMode): Promise<void>
```

Sets the display mode of the composite image. This API uses a promise to return the result.

**Since:** 23

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| compositeDisplayMode | [CompositeDisplayMode](arkts-medialibrary-photoaccesshelper-compositedisplaymode-e-sys.md) | Yes | Display mode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scene parameter verification failed. Possible causes:<br>1. The compositeDisplayMode is not within the supported range. <br>2. The original file does not exist locally in PhotoAsset. <br>3. The PhotoAsset is not a composite asset. <br>4. The original file format is not within the supported range. <br>5. The original file has been edited. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes:<br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
    console.info('setCompositeDisplayModeDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    try {
      let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
      let asset = await fetchResult.getFirstObject();
      let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
      assetChangeRequest.setCompositeDisplayMode(photoAccessHelper.CompositeDisplayMode.DEFAULT);
      await phAccessHelper.applyChanges(assetChangeRequest);
      console.info('apply setCompositeDisplayModeDemo successfully');
    } catch (err) {
      console.error(`apply setCompositeDisplayModeDemo failed with error: ${err.code}, ${err.message}`);
    }
}
```

## setEditData

```TypeScript
setEditData(editData: MediaAssetEditData): void
```

Saves the edited data of an asset.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editData | [MediaAssetEditData](arkts-medialibrary-photoaccesshelper-mediaasseteditdata-c-sys.md) | Yes | Edited data to save. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setEffectMode

```TypeScript
setEffectMode(mode: MovingPhotoEffectMode): void
```

Sets the effect of this moving photo.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [MovingPhotoEffectMode](arkts-medialibrary-photoaccesshelper-movingphotoeffectmode-e-sys.md) | Yes | Effect to set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setHasAppLink

```TypeScript
setHasAppLink(hasAppLink: number): void
```

Sets the status of the app link association.

**Since:** 21

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hasAppLink | number | Yes | Whether to enable or disable the app link association. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: The input parameter is not within the valid range. |

**Examples**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';

enum linkType {
  NOT_DECODED = 0,
  LINK_NOT_EXIST = 1,
  LINK_EXIST = 2
}

async function example(asset: photoAccessHelper.PhotoAsset, hasAppLink: linkType, context: Context) {
    try {
      let phAccessHelper: photoAccessHelper.PhotoAccessHelper =
        photoAccessHelper.getPhotoAccessHelper(context);
      let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest =
        new photoAccessHelper.MediaAssetChangeRequest(asset);
      assetChangeRequest.setHasAppLink(hasAppLink);
      await phAccessHelper.applyChanges(assetChangeRequest);
    } catch (error) {
      console.error('set hasAppLink error: ' + error);
      return;
    }
}
```

## setHidden

```TypeScript
setHidden(hiddenState: boolean): void
```

Hides this file.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hiddenState | boolean | Yes | Whether to hide the file. **true** to hide, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setLivePhoto4dStatus

```TypeScript
setLivePhoto4dStatus(status: LivePhoto4dStatus, livephoto_4d_latest_pair?: string): void
```

Set 4d livephoto status.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| status | [LivePhoto4dStatus](arkts-medialibrary-photoaccesshelper-livephoto4dstatus-e-sys.md) | Yes | 4d livephoto status. |
| livephoto_4d_latest_pair | string | No | The latest 4d livephoto which is genetated by the livephoto. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. |

## setLocation

```TypeScript
setLocation(longitude: number, latitude: number): void
```

Sets location information.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| longitude | number | Yes | Longitude. |
| latitude | number | Yes | Latitude. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setMovingPhotoVersion

```TypeScript
setMovingPhotoVersion(version: number): void
```

Saves MovingPhoto version which is used to determine what special efficacy is supported.

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| version | number | Yes | Motion picture version number |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Parameter error, only supports 9. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes: 1. Database corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setMovingPhotoVersionDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);

  let movingPhotoVersion: number = 9;
  assetChangeRequest.setMovingPhotoVersion(movingPhotoVersion);
  phAccessHelper.applyChanges(assetChangeRequest).then(() => {
    console.info('apply setMovingPhotoVersion successfully');
  }).catch((err: BusinessError) => {
    console.error(`apply setMovingPhotoVersion failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setSupportedWatermarkType

```TypeScript
setSupportedWatermarkType(watermarkType: WatermarkType): void
```

Sets the watermark type supported by photos.

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| watermarkType | [WatermarkType](arkts-medialibrary-photoaccesshelper-watermarktype-e-sys.md) | Yes | Watermark type to set.<br>**NOTE:** <br>**WatermarkType.DEFAULT** cannot be passed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setSupportedWatermarkTypeDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset = await fetchResult.getFirstObject();
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
    assetChangeRequest.setSupportedWatermarkType(photoAccessHelper.WatermarkType.BRAND_COMMON);
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply setSupportedWatermarkType successfully');
  } catch (err) {
    console.error(`apply setSupportedWatermarkType failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setUserComment

```TypeScript
setUserComment(userComment: string): void
```

Sets the user comment information of this media asset.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userComment | string | Yes | Comment information to set, which cannot exceed 420 characters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setVideoEnhancementAttr

```TypeScript
setVideoEnhancementAttr(videoEnhancementType: VideoEnhancementType, photoId: string): void
```

Set video enhancement attribute

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| videoEnhancementType | [VideoEnhancementType](arkts-medialibrary-photoaccesshelper-videoenhancementtype-e-sys.md) | Yes | The type of video enhancement |
| photoId | string | Yes | The photo id of video |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |
| 14000016 | Operation Not Support |
