# Album

```TypeScript
interface Album extends AbsAlbum
```

Provides APIs to manage albums.

**Inheritance/Implementation:** Album extends [AbsAlbum](arkts-medialibrary-sendablephotoaccesshelper-absalbum-i.md)

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## commitModify

```TypeScript
commitModify(): Promise<void>
```

Commits the modification on the album attributes to the database. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| 14000011 | Internal system error |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in sendablePhotoAccessHelper.getPhotoAccessHelper.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('albumCommitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.Album> = await phAccessHelper.getAlbums(sendablePhotoAccessHelper.AlbumType.USER, sendablePhotoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  let album: sendablePhotoAccessHelper.Album = await albumList.getFirstObject();
  album.albumName = 'hello';
  album.commitModify().then(() => {
    console.info('commitModify successfully');
  }).catch((err: BusinessError) => {
    console.error(`commitModify failed with error: ${err.code}, ${err.message}`);
  });
}
```

## convertToPhotoAlbum

```TypeScript
convertToPhotoAlbum(): photoAccessHelper.Album
```

Converts this Sendable album to a non-Sendable album.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| [photoAccessHelper.Album](arkts-medialibrary-photoaccesshelper-album-i.md) | Album of the non-Sendable type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| 14000011 | Internal system error |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in sendablePhotoAccessHelper.getPhotoAccessHelper.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  console.info('convertToPhotoAlbumDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.Album> = await phAccessHelper.getAlbums(sendablePhotoAccessHelper.AlbumType.USER, sendablePhotoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  let sendableAlbum: sendablePhotoAccessHelper.Album = await albumList.getFirstObject();
  let album: photoAccessHelper.Album = sendableAlbum.convertToPhotoAlbum();
  album.getAssets(fetchOption).then((albumFetchResult) => {
    console.info('convertToPhotoAlbum successfully, getCount: ' + albumFetchResult.getCount());
  }).catch((err: BusinessError) => {
    console.error(`convertToPhotoAlbum failed with error: ${err.code}, ${err.message}`);
  });
}
```

## imageCount

```TypeScript
readonly imageCount?: number
```

Number of image assets in the album

**Type:** number

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## videoCount

```TypeScript
readonly videoCount?: number
```

Number of video assets in the album

**Type:** number

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
