# AbsAlbum

```TypeScript
interface AbsAlbum
```

Defines the abstract interface of albums.

**Since:** 10

<!--Device-photoAccessHelper-interface AbsAlbum--><!--Device-photoAccessHelper-interface AbsAlbum-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## getSharedPhotoAssets

```TypeScript
getSharedPhotoAssets(options: FetchOptions): Array<SharedPhotoAsset>
```

Fetch shared photo assets in an album.

**Since:** 13

**Required permissions:** ohos.permission.ACCESS_MEDIALIB_THUMB_DB

<!--Device-AbsAlbum-getSharedPhotoAssets(options: FetchOptions): Array<SharedPhotoAsset>--><!--Device-AbsAlbum-getSharedPhotoAssets(options: FetchOptions): Array<SharedPhotoAsset>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | Yes | Fetch options. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[SharedPhotoAsset](arkts-medialibrary-photoaccesshelper-sharedphotoasset-i-sys.md)&gt; | Returns the shared photo assets |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

## coverUriSource

```TypeScript
readonly coverUriSource?: CoverUriSource
```

Source URI of the album cover.<br>

**Type:** [CoverUriSource](arkts-medialibrary-photoaccesshelper-coverurisource-e-sys.md)

**Since:** 20

<!--Device-AbsAlbum-readonly coverUriSource?: CoverUriSource--><!--Device-AbsAlbum-readonly coverUriSource?: CoverUriSource-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## hidden

```TypeScript
readonly hidden?: boolean
```

Whether the album is hidden. **true** if hidden, **false** otherwise.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-AbsAlbum-readonly hidden?: boolean--><!--Device-AbsAlbum-readonly hidden?: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## uploadStatus

```TypeScript
readonly uploadStatus: boolean
```

Whether the album can be synced to cloud storage or family storage. **true** if it can be synced, **false** otherwise.

**Type:** boolean

**Since:** 22

<!--Device-AbsAlbum-readonly uploadStatus: boolean--><!--Device-AbsAlbum-readonly uploadStatus: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
