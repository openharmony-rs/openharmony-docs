# MediaAssetManager

The MediaAssetManager class is used for manipulating the read and write operations of media assets.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## requestCompositeAuxiliaryImageData

```TypeScript
static requestCompositeAuxiliaryImageData(
      context: Context,
      asset: PhotoAsset,
      dataHandler: MediaAssetDataHandler<ArrayBuffer>
    ): Promise<string>
```

Request composite auxiliary image data.

The AI enhancement generates an additional image. Together with the original image, they form a composite image. One image is displayed externally, while the other serves as an auxiliary image.

**Since:** 26.1.0

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | Yes | PhotoAsset to request. |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;ArrayBuffer&gt; | Yes | Callback will be called when the requested data is ready. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the request ID, which can be used in [cancelRequest](arkts-medialibrary-photoaccesshelper-mediaassetmanager-c.md#cancelrequest) to cancel a request. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Permission denied. The application does not have the required permission ohos.permission.READ_IMAGEVIDEO. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scene parameters validate failed, possible causes: 1. The asset is not a cloud-enhanced composite photo asset. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes: 1. The database is corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |
