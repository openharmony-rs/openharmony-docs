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

## getAssets

```TypeScript
getAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<PhotoAsset>>): void
```

Obtains image and video assets. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

<!--Device-AbsAlbum-getAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<PhotoAsset>>): void--><!--Device-AbsAlbum-getAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<PhotoAsset>>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | Yes | Retrieval options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt;&gt; | Yes | Callback function. If files from the album are obtained successfully, **err** is **undefined**, and **data** is the result set of the obtained image and video data ([FetchResult](arkts-medialibrary-file-photoaccesshelper.md)). Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied<br>**Applicable version:** 10 - 11 |
| 13900020 | Invalid parameter. Possible causes:<br>1.The predicate contains invalid statements, the key must be a valid PhotoKeys value; <br>2.The fetchColumns contain invalid column names, the column must be a valid PhotoKeys value; <br>3.The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum(); <br>4.The album instance is invalid; <br>5.The album ID is invalid; <br>6.The album type or subtype is not a valid enum value; <br>7.The combination of album type and subtype is invalid. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.Database query failed, possible causes: 1. Database connection exception; 2. Database operation error. Please retry and check logs; <br>2.IPC call failed, the server returned an error code; <br>3.Both sandbox query and IPC query failed to retrieve data; <br>4.Failed to create the query result, possible causes: 1. Memory insufficient; 2. IPC timeout. Please retry; <br>5.FetchOptions parsing failed, please check if the parameter is a valid FetchOptions type; <br>6.Parameter parsing failed, please check parameter types and count. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumGetAssetsDemoCallback');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  album.getAssets(fetchOption, (err, albumFetchResult) => {
    if (albumFetchResult !== undefined) {
      console.info('album getAssets successfully, getCount: ' + albumFetchResult.getCount());
    } else {
      console.error(`album getAssets failed with error: ${err.code}, ${err.message}`);
    }
  });
}
```

<a id="getassets-1"></a>

## getAssets

```TypeScript
getAssets(options: FetchOptions): Promise<FetchResult<PhotoAsset>>
```

Obtains image and video assets. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-AbsAlbum-getAssets(options: FetchOptions): Promise<FetchResult<PhotoAsset>>--><!--Device-AbsAlbum-getAssets(options: FetchOptions): Promise<FetchResult<PhotoAsset>>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | Yes | Retrieval options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt;&gt; | Promise used to return the image and video assets obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 20 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied<br>**Applicable version:** 10 - 19 |
| 13900020 | Invalid parameter. Possible causes:<br>1.The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum(); <br>2.The album instance is invalid; <br>3.The album type is invalid, must be a valid AlbumType enum value; <br>4.The object is not a valid instance. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.FetchOptions parsing failed, please check if the parameter is a valid FetchOptions type; <br>2.Parameter parsing failed, please check parameter types and count; <br>3.Database query failed, possible causes: 1. Database connection exception; 2. Database operation error. Please retry and check logs; <br>4.Failed to create the query result, possible causes: 1. Memory insufficient; 2. IPC timeout. Please retry; <br>5.Database query returned empty result set in async execution path. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumGetAssetsDemoPromise');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  album.getAssets(fetchOption).then((albumFetchResult) => {
    console.info('album getAssets successfully, getCount: ' + albumFetchResult.getCount());
  }).catch((err: BusinessError) => {
    console.error(`album getAssets failed with error: ${err.code}, ${err.message}`);
  });
}
```

## albumName

```TypeScript
albumName: string
```

Name of the album. System albums are not writable, whereas user albums can be written to.

**Type:** string

**Since:** 10

<!--Device-AbsAlbum-albumName: string--><!--Device-AbsAlbum-albumName: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumSubtype

```TypeScript
readonly albumSubtype: AlbumSubtype
```

Subtype of the album.

**Type:** [AlbumSubtype](arkts-medialibrary-photoaccesshelper-albumsubtype-e.md)

**Since:** 10

<!--Device-AbsAlbum-readonly albumSubtype: AlbumSubtype--><!--Device-AbsAlbum-readonly albumSubtype: AlbumSubtype-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumType

```TypeScript
readonly albumType: AlbumType
```

Type of the album.

**Type:** [AlbumType](arkts-medialibrary-photoaccesshelper-albumtype-e.md)

**Since:** 10

<!--Device-AbsAlbum-readonly albumType: AlbumType--><!--Device-AbsAlbum-readonly albumType: AlbumType-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumUri

```TypeScript
readonly albumUri: string
```

URI of the album.

**Type:** string

**Since:** 10

<!--Device-AbsAlbum-readonly albumUri: string--><!--Device-AbsAlbum-readonly albumUri: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## changeTime

```TypeScript
readonly changeTime?: number
```

Time when the album is changed. Unit: second, The value must be greater than or equal to 0.

**Type:** number

**Since:** 23

<!--Device-AbsAlbum-readonly changeTime?: long--><!--Device-AbsAlbum-readonly changeTime?: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## count

```TypeScript
readonly count: number
```

Number of files in the album.

**Type:** number

**Since:** 10

<!--Device-AbsAlbum-readonly count: int--><!--Device-AbsAlbum-readonly count: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## coverUri

```TypeScript
readonly coverUri: string
```

URI of the cover file of the album.

**Type:** string

**Since:** 10

<!--Device-AbsAlbum-readonly coverUri: string--><!--Device-AbsAlbum-readonly coverUri: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## lpath

```TypeScript
readonly lpath?: string
```

Virtual path of the album.

Albums and their virtual path values:

- Camera application album: '/DCIM/Camera'  
- Screenshot application album: '/Pictures/Screenshots'  
- Screen recording application album: '/Pictures/Screenrecords'  
- User-created album: '/Pictures/Users/{Custom album name}'

**Type:** string

**Since:** 23

<!--Device-AbsAlbum-readonly lpath?: string--><!--Device-AbsAlbum-readonly lpath?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
