# PhotoAccessHelper

```TypeScript
interface PhotoAccessHelper extends lang.ISendable
```

Helper functions to access photos and albums.

**Inheritance/Implementation:** PhotoAccessHelper extends [lang.ISendable](../../apis-arkts/arkts-apis/arkts-arkts-lang-isendable-i.md)

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## createAsset

```TypeScript
createAsset(displayName: string): Promise<PhotoAsset>
```

Creates an asset with the specified file name. This API uses a promise to return the result.

The file name must meet the following requirements:

- A valid file name must include a base name and a supported image or video extension.  
- The total length of the file name must be between 1 and 255 characters.  
- The base name must not contain any invalid characters.

Starting from API version 18, the following characters are considered invalid: \ / : * ? " &lt; &gt; |

For API versions 10 to 17, the following characters are considered invalid: . .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**Since:** 12

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayName | string | Yes | File name of the asset to create. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md)&gt; | Promise used to return the created asset. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid argument. |
| 14000001 | Invalid display name. |
| 14000011 | Internal system error. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [@ohos.file.sendablePhotoAccessHelper (Album Management Based on a Sendable Object)](arkts-medialibrary-file-sendablephotoaccesshelper.md).

```TypeScript
async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  try {
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    let photoAsset: sendablePhotoAccessHelper.PhotoAsset = await phAccessHelper.createAsset(testFileName);
    console.info('createAsset file displayName' + photoAsset.displayName);
    console.info('createAsset successfully');
  } catch (err) {
    console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

<a id="createasset-1"></a>

## createAsset

```TypeScript
createAsset(displayName: string, options: photoAccessHelper.PhotoCreateOptions): Promise<PhotoAsset>
```

Creates an asset with the specified file name and options. This API uses a promise to return the result.

The file name must meet the following requirements:

- A valid file name must include a base name and a supported image or video extension.  
- The total length of the file name must be between 1 and 255 characters.  
- The base name must not contain any invalid characters.

Starting from API version 18, the following characters are considered invalid: \ / : * ? " &lt; &gt; |

For API versions 10 to 17, the following characters are considered invalid: . .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**Since:** 12

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayName | string | Yes | File name of the asset to create. |
| options | [photoAccessHelper.PhotoCreateOptions](arkts-medialibrary-photoaccesshelper-photocreateoptions-i-sys.md) | Yes | Options for creating the asset. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md)&gt; | Promise used to return the created asset. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid argument. |
| 14000001 | Invalid display name. |
| 14000011 | Internal system error. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [@ohos.file.sendablePhotoAccessHelper (Album Management Based on a Sendable Object)](arkts-medialibrary-file-sendablephotoaccesshelper.md).

```TypeScript
async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  try {
    let testFileName:string = 'testFile' + Date.now() + '.jpg';
    let createOption: photoAccessHelper.PhotoCreateOptions = {
      subtype: photoAccessHelper.PhotoSubtype.DEFAULT
    }
    let photoAsset: sendablePhotoAccessHelper.PhotoAsset = await phAccessHelper.createAsset(testFileName, createOption);
    console.info('createAsset file displayName' + photoAsset.displayName);
    console.info('createAsset successfully');
  } catch (err) {
    console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getHiddenAlbums

```TypeScript
getHiddenAlbums(
      mode: photoAccessHelper.HiddenPhotosDisplayMode,
      options?: photoAccessHelper.FetchOptions
    ): Promise<FetchResult<Album>>
```

Obtains hidden albums based on the specified display mode and retrieval options. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [photoAccessHelper.HiddenPhotosDisplayMode](arkts-medialibrary-photoaccesshelper-hiddenphotosdisplaymode-e-sys.md) | Yes | Display mode of hidden albums. |
| options | [photoAccessHelper.FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | No | Options for retrieving the albums. If this parameter is not specified, the albums are retrieved based on the display mode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-sendablephotoaccesshelper-fetchresult-i.md)&lt;[Album](arkts-medialibrary-sendablephotoaccesshelper-album-i.md)&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [@ohos.file.sendablePhotoAccessHelper (Album Management Based on a Sendable Object)](arkts-medialibrary-file-sendablephotoaccesshelper.md).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the preset hidden album.
async function getSysHiddenAlbum(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('getSysHiddenAlbumDemo');
  phAccessHelper.getHiddenAlbums(photoAccessHelper.HiddenPhotosDisplayMode.ASSETS_MODE)
    .then( async (fetchResult) => {
      if (fetchResult === undefined) {
        console.error('getSysHiddenAlbumPromise fetchResult is undefined');
        return;
      }
      let hiddenAlbum: sendablePhotoAccessHelper.Album = await fetchResult.getFirstObject();
      console.info('getAlbumsPromise successfully, albumUri: ' + hiddenAlbum.albumUri);
      fetchResult.close();
    }).catch((err: BusinessError) => {
      console.error(`getSysHiddenAlbumPromise failed with err: ${err.code}, ${err.message}`);
    });
}

// Obtain the hidden albums displayed by album, that is, the albums with hidden files. Such albums do not include the preset hidden album and the albums in the trash.
async function getHiddenAlbumsView(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('getHiddenAlbumsViewDemo');
  phAccessHelper.getHiddenAlbums(photoAccessHelper.HiddenPhotosDisplayMode.ALBUMS_MODE).then( async (fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getHiddenAlbumsViewPromise fetchResult is undefined');
      return;
    }
    let albums: Array<sendablePhotoAccessHelper.Album> = await fetchResult.getAllObjects();
    console.info('getHiddenAlbumsViewPromise successfully, albums size: ' + albums.length);

    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    for (let i = 0; i < albums.length; i++) {
      // Obtain hidden files in the album.
      albums[i].getAssets(fetchOption).then((assetFetchResult) => {
        console.info('album get hidden assets successfully, getCount: ' + assetFetchResult.getCount());
      }).catch((err: BusinessError) => {
        console.error(`album get hidden assets failed with error: ${err.code}, ${err.message}`);
      });
    }
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error(`getHiddenAlbumsViewPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## getPhotoAssets

```TypeScript
getPhotoAssets(assetsData: photoAccessHelper.ValuesBucket[]): Promise<PhotoAsset[]>
```

Converts the **ValuesBucket** record to a **PhotoAsset** object.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetsData | [photoAccessHelper.ValuesBucket](arkts-medialibrary-photoaccesshelper-valuesbucket-t-sys.md)[] | Yes | Array of asset records.<br>Each element in the array contains the column name and value of the asset. <br>The array can contain a maximum of 500 elements. <br>Each element in the array must contain the following asset column information: **file_id**, **data**, **display_name**, **media_type**, and **subtype**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md)[]&gt; | Promise used to return the PhotoAsset object array (which may be empty). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. Invalid value type in ValuesBucket; <br>2. Missing required column in ValuesBucket; <br>3. Array size exceeds 500. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [@ohos.file.sendablePhotoAccessHelper (Album Management Based on a Sendable Object)](arkts-medialibrary-file-sendablephotoaccesshelper.md).

```TypeScript
async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('getPhotoAssets demo');
  let valuesArr: photoAccessHelper.ValuesBucket[] = [];
  let resultSet: photoAccessHelper.ResultSet | undefined = undefined;
  let photoAssetArr: sendablePhotoAccessHelper.PhotoAsset[] = [];
  let QUERY_SQL = 'SELECT file_id,data,display_name,media_type,subtype from Photos limit 100';
  try {
    resultSet = await photoAccessHelper.getPhotoAccessHelper(context).query(QUERY_SQL);
    let index: number = 0;
    while(resultSet && index < resultSet.rowCount){
      resultSet.goToRow(index);
      valuesArr.push(resultSet.getRow());
      index++;
    }
    photoAssetArr = await phAccessHelper.getPhotoAssets(valuesArr);
    console.info('getPhotoAssets successfully');
  } catch (err) {
    console.error(`valuesArr failed: ${err.code}, ${err.message}`);
  }
}
```

## getSharedPhotoAssets

```TypeScript
getSharedPhotoAssets(options: photoAccessHelper.FetchOptions): Array<SharedPhotoAsset>
```

Fetch shared photo assets.

**Since:** 14

**Required permissions:** ohos.permission.ACCESS_MEDIALIB_THUMB_DB

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [photoAccessHelper.FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | Yes | Fetch options. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[SharedPhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-sharedphotoasset-i-sys.md)&gt; | Returns the shared photo assets |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |
