# MediaAnalysisAlbumChangeRequest (System API)

```TypeScript
class MediaAnalysisAlbumChangeRequest extends MediaAlbumChangeRequest
```

Provides APIs for managing the analysis album change request.

**Inheritance/Implementation:** MediaAnalysisAlbumChangeRequest extends [MediaAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md)

**Since:** 18

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## constructor

```TypeScript
constructor(album: Album)
```

Constructor.

**Since:** 18

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| album | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | Yes | **Highlights** album. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(context: Context) {
  console.info('MediaAnalysisAlbumChangeRequest constructorDemo');
  let helper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  let albumFetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: new dataSharePredicates.DataSharePredicates()
  };
  let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> =
    await helper.getAlbums(photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.HIGHLIGHT, albumFetchOption);
  if (albumFetchResult.getCount() === 0) {
    console.error('No album');
    return;
  }
  let highlightAlbum: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
  albumFetchResult.close();
  let changeRequest: photoAccessHelper.MediaAnalysisAlbumChangeRequest =
    new photoAccessHelper.MediaAnalysisAlbumChangeRequest(highlightAlbum);
}
```

<a id="createanalysisalbumrequest-1"></a>

## createAnalysisAlbumRequest

```TypeScript
static createAnalysisAlbumRequest(
      context:Context,
      name: string,
      subtype: AlbumSubtype
    ): MediaAnalysisAlbumChangeRequest
```

Creates a change request for the **Analysis** album.

> **NOTE:** 
> 
> The album name must meet the following requirements:
> 
> - The album name string length ranges from 1 to 255.
> 
> - The album name cannot contain any of the following characters:.. \ / : * ? " ' ` &lt;| { } [ ]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| name | string | Yes | Name of the album. |
| subtype | [AlbumSubtype](arkts-medialibrary-photoaccesshelper-albumsubtype-e.md) | Yes | Subtype of the album. |

**Return value:**

| Type | Description |
| --- | --- |
| [MediaAnalysisAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaanalysisalbumchangerequest-c-sys.md) | MediaAnalysisAlbumChangeRequest instance created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails.<br>Possible causes: <br>1. The input parameter is not within the valid range. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

For details about how to create a photoAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('createAlbumRequestDemo');
  try {
    let albumName: string = 'newAlbumName' + new Date().getTime();
    let albumChangeRequest: photoAccessHelper.MediaAnalysisAlbumChangeRequest = photoAccessHelper.MediaAnalysisAlbumChangeRequest.createAnalysisAlbumRequest(context, albumName, photoAccessHelper.AlbumSubtype.PORTRAIT);
    await phAccessHelper.applyChanges(albumChangeRequest);
    console.info('apply createAlbumRequest successfully');
  } catch (err) {
    console.error(`createAlbumRequestDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setDefaultCoverUri

```TypeScript
setDefaultCoverUri(coverUri: string): void
```

Sets the default cover image for the smart album.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| coverUri | string | Yes | URI of the file to be set as the default cover image of the smart album. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails.<br>Possible causes: <br>1. The input parameter is not within the valid range. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(context: Context) {
  console.info('setDefaultCoverUri');
  try {
    let helper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
    let albumFetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> =
      await helper.getAlbums(photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.PORTRAIT, albumFetchOption);
    if (albumFetchResult.getCount() === 0) {
      console.error('No album');
      return;
    }
    let portraitAlbum: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    albumFetchResult.close();
    // Obtain resources from the album.
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> =
      await portraitAlbum.getAssets(fetchOption);
    if (fetchResult.getCount() === 0) {
      console.error('No asset in album');
      fetchResult.close();
      return;
    }
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let coverUri: string = asset.uri;
    fetchResult.close();
    // Set the default cover.
    let changeRequest: photoAccessHelper.MediaAnalysisAlbumChangeRequest =
      new photoAccessHelper.MediaAnalysisAlbumChangeRequest(portraitAlbum);
    changeRequest.setDefaultCoverUri(coverUri);
    await helper.applyChanges(changeRequest);
    console.info('setDefaultCoverUri success');
  } catch (err) {
    console.error(`setDefaultCoverUri error: ${err}`);
  }
}
```

## setOrderPosition

```TypeScript
setOrderPosition(assets: Array<PhotoAsset>, position: Array<number>): void
```

Sets the sequence of assets in the **Analysis** album.

**Since:** 18

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Assets in the album for which the sequence needs to be set. |
| position | Array&lt;number&gt; | Yes | Sequence of assets in the album. |

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

async function example(context: Context) {
  try {
    console.info('setOrderPosition');
    let helper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
    let albumFetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = 
      await helper.getAlbums(photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.HIGHLIGHT, albumFetchOption);
    if (albumFetchResult.getCount() === 0) {
      console.error('No album');
      return;
    }
    let highlightAlbum: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    albumFetchResult.close();
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    const fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> =
      await highlightAlbum.getAssets(fetchOption);
    let assets: photoAccessHelper.PhotoAsset[] = await fetchResult.getAllObjects();
    let indexes: number[] = [];
    for (let i = 0; i < assets.length; i++) {
      indexes.push(i);
    }
    let changeRequest: photoAccessHelper.MediaAnalysisAlbumChangeRequest =
      new photoAccessHelper.MediaAnalysisAlbumChangeRequest(highlightAlbum);
    changeRequest.setOrderPosition(assets, indexes);
    await helper.applyChanges(changeRequest);
    console.info(`setOrderPosition ${indexes}`);
  } catch (err) {
    console.error(`setOrderPosition error: ${err}`);
  }
}
```

## setRelationship

```TypeScript
setRelationship(relationship: string): Promise<void>
```

Sets the relationships of a person in the portrait album.

The supported relationship names include:

| Unique ID | Description |  
| ---------- | ------- |  
| me | Me|
| son | Son|
| daughter | Daughter|
| wife | Wife|
| husband | Husband|
| father | Father|
| mother | Mother|
| colleague | Colleague|
| friend | Friend|
| classmate | Classmate|
| best_friend_female | Best female friend|
| boyfriend | Boyfriend|
| girlfriend | Girlfriend|
| family | Family|
| maternal_grandfather | Maternal grandfather|
| maternal_grandmother | Maternal grandmother|
| paternal_grandfather | Paternal grandfather|
| paternal_grandmother | Paternal grandmother|
| older_brother | Older brother|
| older_sister | Older sister|
| younger_brother | Younger brother|
| younger_sister | Younger sister|
| relative | Relative|
| other | [Other](../../apis-arkweb/arkts-components/arkts-arkweb-web-comp-contextmenuinputfieldtype-e.md) |

**Since:** 21

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| relationship | string | Yes | Name of the relationship to set.<br>You can set it to an empty string to remove the current relationship setting. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails.<br>Possible causes: <br>1. The input parameter is not within the valid range. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function SetRelationshipExample(context: Context, relationship: string) {
  try {
    console.info('setRelationship');
    let helper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
    let albumFetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> =
      await helper.getAlbums(photoAccessHelper.AlbumType.SMART, photoAccessHelper.AlbumSubtype.PORTRAIT, albumFetchOption);
    if (albumFetchResult.getCount() === 0) {
      console.error('No album');
      return;
    }
    let portraitAlbum: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    albumFetchResult.close();
    let changeRequest: photoAccessHelper.MediaAnalysisAlbumChangeRequest =
      new photoAccessHelper.MediaAnalysisAlbumChangeRequest(portraitAlbum);
    changeRequest.setRelationship(relationship);
    await helper.applyChanges(changeRequest);
    console.info(`setRelationship ${relationship}`);
  } catch (err) {
    console.error(`setRelationship error: ${err}`);
  }
}
```
