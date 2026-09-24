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

## getFaceId

```TypeScript
getFaceId(): Promise<string>
```

Obtains the face identifier on the cover of a portrait album or group photo album. This API uses a promise to return the result.

**Since:** 13

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return **tag_id** of the portrait album, **group_tag** of the group photo album, or an empty string if no face identifier is found. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| 14000011 | Internal system error |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [@ohos.file.sendablePhotoAccessHelper (Album Management Based on a Sendable Object)](arkts-medialibrary-file-sendablephotoaccesshelper.md).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { common } from '@kit.AbilityKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getFaceIdDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.equalTo("user_display_level", 1);
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult =
      await phAccessHelper.getAlbums(sendablePhotoAccessHelper.AlbumType.SMART,
        sendablePhotoAccessHelper.AlbumSubtype.PORTRAIT,
        fetchOptions);
    let album = await fetchResult?.getFirstObject();
    let faceId = await album?.getFaceId();
    console.info(`getFaceId successfully, faceId: ${faceId}`);
    fetchResult.close();
  } catch (err) {
    console.error(`getFaceId failed with err: ${err.code}, ${err.message}`);
  }
}
```
