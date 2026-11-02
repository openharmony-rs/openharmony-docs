# SingleFileMovingPhotoUtil

```TypeScript
class SingleFileMovingPhotoUtil
```

Single file moving photo manager.

**Since:** 26.1.0

<!--Device-photoAccessHelper-class SingleFileMovingPhotoUtil--><!--Device-photoAccessHelper-class SingleFileMovingPhotoUtil-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## getVideoOffset

```TypeScript
static getVideoOffset(singleFileMovingPhotoUri: string): number
```

Get video offset in the single file moving photo.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleFileMovingPhotoUtil-static getVideoOffset(singleFileMovingPhotoUri: string): int--><!--Device-SingleFileMovingPhotoUtil-static getVideoOffset(singleFileMovingPhotoUri: string): int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| singleFileMovingPhotoUri | string | Yes | Uri of single file moving photo. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Video offset in the single file moving photo. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: <br>1. The singleFileMovingPhotoUri is empty or can not open. <br>2. The singleFileMovingPhotoUri is belonging to MediaLibrary. |
| 23800109 | Incorrect file format. |

## isSingleFileMovingPhoto

```TypeScript
static isSingleFileMovingPhoto(uri: string): boolean
```

Determine whether the asset specified by the uri is a single file moving photo.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleFileMovingPhotoUtil-static isSingleFileMovingPhoto(uri: string): boolean--><!--Device-SingleFileMovingPhotoUtil-static isSingleFileMovingPhoto(uri: string): boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Input uri. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the asset specified by the uri is a single file moving photo, return true if yes, and false otherwise.. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: <br>1. The uri is invalid. <br>2. The uri can not be opened. |

## packingSingleFileMovingPhoto

```TypeScript
static packingSingleFileMovingPhoto(imageUri: string, videoUri: string, outParentFolder: string): string
```

Packing an image and a video into a single file moving photo.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleFileMovingPhotoUtil-static packingSingleFileMovingPhoto(imageUri: string, videoUri: string, outParentFolder: string): string--><!--Device-SingleFileMovingPhotoUtil-static packingSingleFileMovingPhoto(imageUri: string, videoUri: string, outParentFolder: string): string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageUri | string | Yes | Input image uri. |
| videoUri | string | Yes | Input video uri. |
| outParentFolder | string | Yes | Output single file moving photo parent folder. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the single file moving photo path. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: <br>1. ImageUri、videoUri and outParentFolder are empty or can not open. <br>2. The image and video formats do not satisfy jpeg/jpg/heic/heif+mp4. <br>3. When saving generated files, a naming conflict occurs after more than 10 attempts. |

## unpackingSingleFileMovingPhoto

```TypeScript
static unpackingSingleFileMovingPhoto(
        singleFileMovingPhotoUri: string, 
        outImageParentFolder: string, 
        outVideoParentFolder: string): string[]
```

Unpacking the single file moving photo into an image and a video.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleFileMovingPhotoUtil-static unpackingSingleFileMovingPhoto(        singleFileMovingPhotoUri: string,         outImageParentFolder: string,         outVideoParentFolder: string): string[]--><!--Device-SingleFileMovingPhotoUtil-static unpackingSingleFileMovingPhoto(        singleFileMovingPhotoUri: string,         outImageParentFolder: string,         outVideoParentFolder: string): string[]-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| singleFileMovingPhotoUri | string | Yes | The single file moving photo. |
| outImageParentFolder | string | Yes | Image output parent folder. |
| outVideoParentFolder | string | Yes | Video output parent folder. |

**Return value:**

| Type | Description |
| --- | --- |
| string[] | Returns the path to pictures and videos |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: <br>1. SingleFileMovingPhotoUri、outImageParentFolder、outVideoParentFolder are empty or can not open. <br>2. When saving generated files, a naming conflict occurs after more than 10 attempts. |
| 23800109 | Incorrect file format. |
