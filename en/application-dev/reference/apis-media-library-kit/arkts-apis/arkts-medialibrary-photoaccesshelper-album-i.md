# Album

```TypeScript
interface Album extends AbsAlbum
```

Provides APIs to manage albums.

**Inheritance/Implementation:** Album extends [AbsAlbum](arkts-medialibrary-photoaccesshelper-absalbum-i.md)

**Since:** 10

<!--Device-photoAccessHelper-interface Album extends AbsAlbum--><!--Device-photoAccessHelper-interface Album extends AbsAlbum-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## commitModify

```TypeScript
commitModify(callback: AsyncCallback<void>): void
```

Commits the modification on the album attributes to the database. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-commitModify(callback: AsyncCallback<void>): void--><!--Device-Album-commitModify(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function. If the album properties are modified successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum(); <br>2.The album is not a user album, only user albums support this operation; <br>3.The album name exceeds the length limit or contains invalid characters; <br>4.The number of parameters is invalid; <br>5.The callback parameter must be of type AsyncCallback&lt;void&gt;. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The context parameter is invalid or not properly initialized, please pass a valid Context obtained from the application context; <br>2.The server returned an error during commitModify, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumCommitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  if (albumList === undefined) {
    console.error('albumList is undefined');
    return;
  }
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  if (album === undefined) {
    console.error('album is undefined');
    return;
  }
  album.albumName = 'hello';
  album.commitModify((err) => {
    if (err !== undefined) {
      console.error(`commitModify failed with error: ${err.code}, ${err.message}`);
    } else {
      console.info('commitModify successfully');
    }
  });
}
```

<a id="commitmodify-1"></a>

## commitModify

```TypeScript
commitModify(): Promise<void>
```

Commits the modification on the album attributes to the database. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-commitModify(): Promise<void>--><!--Device-Album-commitModify(): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.System out of memory, please retry; <br>2.The object is not a valid instance; <br>3.The album is not a user album, only user albums support this operation; <br>4.The album name exceeds the length limit or contains invalid characters; <br>5.The number of parameters is invalid. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The context parameter is invalid or not properly initialized, please pass a valid Context obtained from the application context; <br>2.The server returned an error during commitModify, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumCommitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  if (albumList === undefined) {
    console.error('albumList is undefined');
    return;
  }
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  if (album === undefined) {
    console.error('album is undefined');
    return;
  }
  album.albumName = 'hello';
  album.commitModify().then(() => {
    console.info('commitModify successfully');
  }).catch((err: BusinessError) => {
    console.error(`commitModify failed with error: ${err.code}, ${err.message}`);
  });
}
```

## addAssets

```TypeScript
addAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void
```

Adds image and video assets to a user album. Before the operation, ensure that the image and video assets to add and the album exist. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [addAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#addassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-addAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void--><!--Device-Album-addAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Array of the image and video assets to add. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function. If an image or video is added successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.System out of memory, please retry; <br>2.The object is not a valid instance; <br>3.The album is not a user album, only user albums support this operation; <br>4.The assets parameter must be an array; <br>5.The assets array is empty; <br>6.The array element must be a valid PhotoAsset object; <br>7.The number of parameters is invalid; <br>8.The array element is not a valid object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.System memory insufficient, please retry; <br>2.The assets array contains elements with invalid file type, each element must be IMAGE or VIDEO type; <br>3.IPC call failed, please retry and check logs; <br>4.The assets array contains elements that are not valid PhotoAsset objects; <br>5.Server returned a non-permission error code; <br>6.Failed to update album count, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>7.The assets parameter must be an array; <br>8.The assets array is empty; <br>9.The array element must be a valid PhotoAsset object. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('addAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('addAssetsDemoCallback asset is undefined');
      return;
    }
    album.addAssets([asset], (err) => {
      if (err === undefined) {
        console.info('album addAssets successfully');
      } else {
        console.error(`album addAssets failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`addAssetsDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

<a id="addassets-1"></a>

## addAssets

```TypeScript
addAssets(assets: Array<PhotoAsset>): Promise<void>
```

Adds image and video assets to a user album. Before the operation, ensure that the image and video assets to add and the album exist. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [addAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#addassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-addAssets(assets: Array<PhotoAsset>): Promise<void>--><!--Device-Album-addAssets(assets: Array<PhotoAsset>): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Array of the image and video assets to add. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum(); <br>2.The album instance is invalid; <br>3.The album is not a user album, only user albums support addAssets; <br>4.The assets parameter must be an array; <br>5.The assets array is empty; <br>6.The array element must be a valid PhotoAsset object; <br>7.The number of parameters is invalid, expected at least 1 parameter; <br>8.The array element is not a valid PhotoAsset object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The assets array contains no valid photo or video resources; <br>2.IPC call returned a non-permission error code; <br>3.Batch insert failed, database operation error, please retry; <br>4.Failed to update album count, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>5.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>6.The assets parameter must be an array; <br>7.The assets array is empty; <br>8.The array element must be a valid PhotoAsset object. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('addAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('addAssetsDemoPromise asset is undefined');
      return;
    }
    album.addAssets([asset]).then(() => {
      console.info('album addAssets successfully');
    }).catch((err: BusinessError) => {
      console.error(`album addAssets failed with error: ${err.code}, ${err.message}`);
    });
  } catch (err) {
    console.error(`addAssetsDemoPromise failed with error: ${err.code}, ${err.message}`);
  }
}
```

## removeAssets

```TypeScript
removeAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void
```

Removes image and video assets from a user album. The album and file resources must exist. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [removeAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#removeassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-removeAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void--><!--Device-Album-removeAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Array of the image and video assets to remove. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function. If an image or video is removed successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum(); <br>2.The album instance is invalid; <br>3.The album is not a user album, only user albums support removeAssets; <br>4.The assets parameter must be an array; <br>5.The assets array is empty; <br>6.The array element must be a valid PhotoAsset object; <br>7.The object is not a valid instance; <br>8.The array element is invalid. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The assets array is empty or contains no valid PhotoAsset elements; <br>2.IPC call returned a non-permission error code; <br>3.The assets array contains elements that are not valid PhotoAsset objects; <br>4.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>5.The assets parameter must be an array; <br>6.The assets array is empty; <br>7.The array element must be a valid PhotoAsset object. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('removeAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('removeAssetsDemoCallback asset is undefined');
      return;
    }
    album.removeAssets([asset], (err) => {
      if (err === undefined) {
        console.info('album removeAssets successfully');
      } else {
        console.error(`album removeAssets failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`removeAssetsDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

<a id="removeassets-1"></a>

## removeAssets

```TypeScript
removeAssets(assets: Array<PhotoAsset>): Promise<void>
```

Removes image and video assets from a user album. The album and file resources must exist. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [removeAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#removeassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-Album-removeAssets(assets: Array<PhotoAsset>): Promise<void>--><!--Device-Album-removeAssets(assets: Array<PhotoAsset>): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Array of the image and video assets to remove. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1.The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum(); <br>2.The album instance is invalid; <br>3.The album is not a user album, only user albums support removeAssets; <br>4.The assets parameter must be an array; <br>5.The assets array is empty; <br>6.The array element must be a valid PhotoAsset object; <br>7.The object is not a valid instance; <br>8.The array element is invalid. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1.The assets array is empty or contains no valid PhotoAsset elements; <br>2.IPC call returned a non-permission error code; <br>3.The assets array contains elements that are not valid PhotoAsset objects; <br>4.System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs; <br>5.The assets parameter must be an array; <br>6.The assets array is empty; <br>7.The array element must be a valid PhotoAsset object. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('removeAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    if (album === undefined) {
      console.error('removeAssetsPromise albums is undefined');
      return;
    }
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('removeAssetsPromise asset is undefined');
      return;
    }
    album.removeAssets([asset]).then(() => {
      console.info('album removeAssets successfully');
    }).catch((err: BusinessError) => {
      console.error(`album removeAssets failed with error: ${err.code}, ${err.message}`);
    });
  } catch (err) {
    console.error(`removeAssetsDemoPromise failed with error: ${err.code}, ${err.message}`);
  }
}
```

## imageCount

```TypeScript
readonly imageCount?: number
```

Number of images in the album.

**Type:** number

**Since:** 11

<!--Device-Album-readonly imageCount?: int--><!--Device-Album-readonly imageCount?: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## videoCount

```TypeScript
readonly videoCount?: number
```

Number of videos in the album.

**Type:** number

**Since:** 11

<!--Device-Album-readonly videoCount?: int--><!--Device-Album-readonly videoCount?: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
