# FileAsset (System API)

```TypeScript
interface FileAsset
```

Provides APIs for encapsulating file asset attributes.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [PhotoAsset](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userFileManager } from '@kit.CoreFileKit';
```

## close

```TypeScript
close(fd: number, callback: AsyncCallback<void>): void
```

Closes a file. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** close

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor of the file to close. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('closeDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
    const fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let fd: number = await fileAsset.open('rw');
    console.info('file fd', fd);
    fileAsset.close(fd, (err) => {
      if (err == undefined) {
        console.info('asset close succeed.');
      } else {
        console.error('close failed, message = ' + err);
      }
    });
  } catch (err) {
    console.error('close failed, message = ' + err);
  }
}
```

<a id="close-1"></a>

## close

```TypeScript
close(fd: number): Promise<void>
```

Closes this file. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** close

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor of the file to close. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('closeDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
    const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let fd: number = await asset.open('rw');
    console.info('file fd', fd);
    await asset.close(fd);
    console.info('asset close succeed.');
  } catch (err) {
    console.error('close failed, message = ' + err);
  }
}
```

## commitModify

```TypeScript
commitModify(callback: AsyncCallback<void>): void
```

Commits the modification on the file metadata to the database. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [commitModify](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#commitmodify)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('commitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  let displayName: string = userFileManager.ImageVideoKey.DISPLAY_NAME.toString();
  let fileAssetDisplayName: userFileManager.MemberType = fileAsset.get(displayName);
  console.info('fileAsset get fileAssetDisplayName = ', fileAssetDisplayName);
  let newFileAssetDisplayName = 'new' + fileAssetDisplayName;
  console.info('fileAsset newFileAssetDisplayName = ', newFileAssetDisplayName);
  fileAsset.set(displayName, newFileAssetDisplayName);
  fileAsset.commitModify((err) => {
    if (err == undefined) {
      let commitModifyDisplayName = fileAsset.get(displayName);
      console.info('fileAsset commitModify successfully, commitModifyDisplayName = ', commitModifyDisplayName);
    } else {
      console.error('commitModify failed, message =', err);
    }
  });
}
```

<a id="commitmodify-1"></a>

## commitModify

```TypeScript
commitModify(): Promise<void>
```

Commits the modification on the file metadata to the database. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [commitModify](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#commitmodify)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('commitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  let displayName = userFileManager.ImageVideoKey.DISPLAY_NAME.toString();
  let fileAssetDisplayName: userFileManager.MemberType = fileAsset.get(displayName);
  console.info('fileAsset get fileAssetDisplayName = ', fileAssetDisplayName);
  let newFileAssetDisplayName = 'new' + fileAssetDisplayName;
  console.info('fileAsset newFileAssetDisplayName = ', newFileAssetDisplayName);
  fileAsset.set(displayName, newFileAssetDisplayName);
  try {
    await fileAsset.commitModify();
    let commitModifyDisplayName = fileAsset.get(displayName);
    console.info('fileAsset commitModify successfully, commitModifyDisplayName = ', commitModifyDisplayName);
  } catch (err) {
    console.error('commitModify failed. message = ', err);
  }
}
```

## favorite

```TypeScript
favorite(isFavorite: boolean, callback: AsyncCallback<void>): void
```

Favorites or unfavorites a file. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [setFavorite](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#setfavorite)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFavorite | boolean | Yes | Whether to favorite or unfavorite the file. The value **true** means to favorite the file; the value **false** means the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('favoriteDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  asset.favorite(true, (err) => {
    if (err == undefined) {
      console.info('favorite successfully');
    } else {
      console.error('favorite failed with error:' + err);
    }
  });
}
```

<a id="favorite-1"></a>

## favorite

```TypeScript
favorite(isFavorite: boolean): Promise<void>
```

Favorites or unfavorites this file asset. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [setFavorite](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#setfavorite)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFavorite | boolean | Yes | Whether to favorite or unfavorite the file. The value **true** means to favorite the file; the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('favoriteDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  asset.favorite(true).then(() => {
    console.info('favorite successfully');
  }).catch((err: BusinessError) => {
    console.error('favorite failed with error:' + err);
  });
}
```

## get

```TypeScript
get(member: string): MemberType
```

Obtains the value of a **FileAsset** parameter.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [get](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#get)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| member | string | Yes | Member parameter name, for example, **ImageVideoKey.DISPLAY_NAME**. You need to set **PhotoKeys** to be obtained in **fetchColumns** for all attributes except **uri**, **photoType**, and **displayName**. For example, **fetchColumns: ['title']**. |

**Return value:**

| Type | Description |
| --- | --- |
| [MemberType](arkts-corefile-userfilemanager-membertype-t-sys.md) | Returns the member parameter. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('fileAssetGetDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: ['title'],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let title: userFileManager.ImageVideoKey = userFileManager.ImageVideoKey.TITLE;
    let fileAssetTitle: userFileManager.MemberType = fileAsset.get(title.toString());
    console.info('fileAsset Get fileAssetTitle = ', fileAssetTitle);
  } catch (err) {
    console.error('release failed. message = ', err);
  }
}
```

## getExif

```TypeScript
getExif(callback: AsyncCallback<string>): void
```

Obtains the EXIF data from a JPG image and returns a JSON string. This API uses an asynchronous callback to return the result.

For details about the EXIF tags, see [image.PropertyKey](../../apis-image-kit/arkts-apis/arkts-image-image-propertykey-e.md).

| Key Value | Description |  
| --------------------------------------- | ----------------- |  
| BitsPerSample | Number of bits per sample.|
| Orientation | Image orientation.|
| ImageLength | Image length.|
| ImageWidth | Image width.|
| GPSLatitude | GPS latitude of the image.|
| GPSLongitude | GPS longitude of the image.|
| GPSLatitudeRef | Longitude reference, for example, W or E.|
| GPSLongitudeRef | Latitude reference, for example, N or S.|
| DateTimeOriginal | Shooting time.|
| ExposureTime | Exposure time.|
| [SceneType](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-scenetype-e.md) | Scene type.|
| ISOSpeedRatings | ISO sensitivity or speed.|
| FNumber | f-number.|
| DateTime | Modification time.|
| GPSTimeStamp | GPS timestamp.|
| GPSDateStamp | GPS date stamp.|
| ImageDescription | Image description.|
| Make | Manufacturer.|
| MakeNote | Manufacturer.|
| [Model](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-model-i.md) | Model.|
| PhotoMode | Photo mode.|
| SensitivityType | Sensitivity type.|
| StandardOutputSensitivity | Standard output sensitivity.|
| RecommendedExposureIndex | Recommended exposure index.|
| ApertureValue | Aperture value.|
| MeteringMode | Metering mode.|
| [LightSource](../../apis-arkui/arkts-components/arkts-arkui-common-comp-lightsource-i-sys.md) | Light source.|
| [Flash](../../apis-camera-kit/arkts-apis/arkts-camera-camera-flash-i.md) | Flash status.|
| FocalLength | Focal length.|
| UserComment | User comments.|
| PixelXDimension | Pixel X dimension.|
| PixelYDimension | Pixel Y dimension.|
| [WhiteBalance](../../apis-camera-kit/arkts-apis/arkts-camera-camera-whitebalance-i.md) | White balance.|
| FocalLengthIn35mmFilm | Focal length in 35 mm film.|
| ExposureBiasValue | Exposure compensation.|

> **NOTE:** 
> 
> This API returns a JSON string that contains EXIF tags. The complete Exif information consists of all_exif and
> [ImageVideoKey](arkts-corefile-userfilemanager-imagevideokey-e-sys.md).USER_COMMENT. The two fields need to be passed to
> **fetchColumns**.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [getExif](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i-sys.md#getexif)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback that returns the EXIF data, in JSON strings. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('getExifDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.isNotNull('all_exif')
    let fetchOptions: userFileManager.FetchOptions = {
      fetchColumns: ['all_exif', userFileManager.ImageVideoKey.USER_COMMENT.toString()],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    if (fileAsset === undefined) {
      console.error('getExif fileAsset is undefined');
      fetchResult.close();
      return;
    }
    console.info('getExifDemo fileAsset displayName: ' + JSON.stringify(fileAsset.displayName));
    let userCommentKey: string = 'UserComment';
    fileAsset.getExif((err, exifMessage) => {
      if (exifMessage != undefined) {
        let userComment: string = JSON.stringify(JSON.parse(exifMessage), [userCommentKey]);
        console.info('getExifDemo userComment: ' + JSON.stringify(userComment));
      } else {
        console.error('getExif failed, message = ', err);
      }
    });
    fetchResult.close();
  } catch (err) {
    console.error('getExifDemoCallback failed with error: ' + err);
  }
}
```

<a id="getexif-1"></a>

## getExif

```TypeScript
getExif(): Promise<string>
```

Obtains the EXIF data from a JPG image and returns a JSON string. This API uses a promise to return the result.

For details about the EXIF tags, see [image.PropertyKey](../../apis-image-kit/arkts-apis/arkts-image-image-propertykey-e.md).

| Key Value | Description |  
| --------------------------------------- | ----------------- |  
| BitsPerSample | Number of bits per sample.|
| Orientation | Image orientation.|
| ImageLength | Image length.|
| ImageWidth | Image width.|
| GPSLatitude | GPS latitude of the image.|
| GPSLongitude | GPS longitude of the image.|
| GPSLatitudeRef | Longitude reference, for example, W or E.|
| GPSLongitudeRef | Latitude reference, for example, N or S.|
| DateTimeOriginal | Shooting time.|
| ExposureTime | Exposure time.|
| [SceneType](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-scenetype-e.md) | Scene type.|
| ISOSpeedRatings | ISO sensitivity or speed.|
| FNumber | f-number.|
| DateTime | Modification time.|
| GPSTimeStamp | GPS timestamp.|
| GPSDateStamp | GPS date stamp.|
| ImageDescription | Image description.|
| Make | Manufacturer.|
| MakeNote | Manufacturer.|
| [Model](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-model-i.md) | Model.|
| PhotoMode | Photo mode.|
| SensitivityType | Sensitivity type.|
| StandardOutputSensitivity | Standard output sensitivity.|
| RecommendedExposureIndex | Recommended exposure index.|
| ApertureValue | Aperture value.|
| MeteringMode | Metering mode.|
| [LightSource](../../apis-arkui/arkts-components/arkts-arkui-common-comp-lightsource-i-sys.md) | Light source.|
| [Flash](../../apis-camera-kit/arkts-apis/arkts-camera-camera-flash-i.md) | Flash status.|
| FocalLength | Focal length.|
| UserComment | User comments.|
| PixelXDimension | Pixel X dimension.|
| PixelYDimension | Pixel Y dimension.|
| [WhiteBalance](../../apis-camera-kit/arkts-apis/arkts-camera-camera-whitebalance-i.md) | White balance.|
| FocalLengthIn35mmFilm | Focal length in 35 mm film.|
| ExposureBiasValue | Exposure compensation.|

> **NOTE:** 
> 
> This API returns a JSON string that contains EXIF tags. The complete Exif information consists of all_exif and
> [ImageVideoKey](arkts-corefile-userfilemanager-imagevideokey-e-sys.md).USER_COMMENT. The two fields need to be passed to
> **fetchColumns**.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [getExif](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i-sys.md#getexif)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise that returns the EXIF data, in JSON strings. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('getExifDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.isNotNull('all_exif')
    let fetchOptions: userFileManager.FetchOptions = {
      fetchColumns: ['all_exif', userFileManager.ImageVideoKey.USER_COMMENT.toString()],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    console.info('getExifDemo fileAsset displayName: ' + JSON.stringify(fileAsset.displayName));
    let exifMessage: string = await fileAsset.getExif();
    let userCommentKey: string = 'UserComment';
    let userComment: string = JSON.stringify(JSON.parse(exifMessage), [userCommentKey]);
    console.info('getExifDemo userComment: ' + JSON.stringify(userComment));
    fetchResult.close();
  } catch (err) {
    console.error('getExifDemoCallback failed with error: ' + err);
  }
}
```

## getThumbnail

```TypeScript
getThumbnail(callback: AsyncCallback<image.PixelMap>): void
```

Obtains the thumbnail of a file. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getThumbnail](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#getthumbnail)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the PixelMap of the thumbnail. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getThumbnailDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  console.info('asset displayName = ', asset.displayName);
  asset.getThumbnail((err, pixelMap) => {
    if (err == undefined) {
      console.info('getThumbnail successful ' + pixelMap);
    } else {
      console.error('getThumbnail fail', err);
    }
  });
}
```

<a id="getthumbnail-1"></a>

## getThumbnail

```TypeScript
getThumbnail(size: image.Size, callback: AsyncCallback<image.PixelMap>): void
```

Obtains the file thumbnail of the given size. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getThumbnail](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#getthumbnail)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [image.Size](../../apis-image-kit/arkts-apis/arkts-image-image-size-i.md) | Yes | Size of the thumbnail. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the PixelMap of the thumbnail. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getThumbnailDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let size: image.Size = { width: 720, height: 720 };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  console.info('asset displayName = ', asset.displayName);
  asset.getThumbnail(size, (err, pixelMap) => {
    if (err == undefined) {
      console.info('getThumbnail successful ' + pixelMap);
    } else {
      console.error('getThumbnail fail', err);
    }
  });
}
```

<a id="getthumbnail-2"></a>

## getThumbnail

```TypeScript
getThumbnail(size?: image.Size): Promise<image.PixelMap>
```

Obtains the file thumbnail of the given size. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getThumbnail](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#getthumbnail)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [image.Size](../../apis-image-kit/arkts-apis/arkts-image-image-size-i.md) | No | Size of the thumbnail. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise that returns the PixelMap of the thumbnail. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getThumbnailDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let size: image.Size = { width: 720, height: 720 };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  console.info('asset displayName = ', asset.displayName);
  asset.getThumbnail(size).then((pixelMap) => {
    console.info('getThumbnail successful ' + pixelMap);
  }).catch((err: BusinessError) => {
    console.error('getThumbnail fail' + err);
  });
}
```

## open

```TypeScript
open(mode: string, callback: AsyncCallback<number>): void
```

Opens this file asset. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The write operations are mutually exclusive. After a write operation is complete, you must call **close** to
> close the file.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** open

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO or ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | string | Yes | Mode of opening the file, for example, **'r'** (read-only), **'w'** (write-only), and **'rw'** (read-write). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the file descriptor of the file opened. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
async function example(mgr: userFileManager.UserFileManager) {
  console.info('openDemo');
   let testFileName: string = 'testFile' + Date.now() + '.jpg';
  const fileAsset: userFileManager.FileAsset = await mgr.createPhotoAsset(testFileName);
  fileAsset.open('rw', (err, fd) => {
    if (fd != undefined) {
      console.info('File fd' + fd);
      fileAsset.close(fd);
    } else {
      console.error('File err' + err);
    }
  });
}
```

<a id="open-1"></a>

## open

```TypeScript
open(mode: string): Promise<number>
```

Opens this file asset. This API uses a promise to return the result.

> **NOTE:** 
> 
> The write operations are mutually exclusive. After a write operation is complete, you must call **close** to
> close the file.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** open

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO or ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | string | Yes | File open mode, which can be **r** (read-only), **w** (write-only), or **rw** (read- write). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise that returns the file descriptor of the file opened. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
async function example(mgr: userFileManager.UserFileManager) {
  console.info('openDemo');
  try {
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    const fileAsset: userFileManager.FileAsset = await mgr.createPhotoAsset(testFileName);
    let fd: number = await fileAsset.open('rw');
    if (fd != undefined) {
      console.info('File fd' + fd);
      fileAsset.close(fd);
    } else {
      console.error(' open File fail');
    }
  } catch (err) {
    console.error('open Demo err' + err);
  }
}
```

## set

```TypeScript
set(member: string, value: string): void
```

Sets a **FileAsset** parameter.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [set](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#set)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| member | string | Yes | Member parameter name, for example, **ImageVideoKey.DISPLAY_NAME**. |
| value | string | Yes | Value to set. Only the values of **DISPLAY_NAME** and **TITLE** can be changed. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('fileAssetSetDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let displayName: string = userFileManager.ImageVideoKey.DISPLAY_NAME.toString();
    fileAsset.set(displayName, 'newDisplayName1');
  } catch (err) {
    console.error('release failed. message = ', err);
  }
}
```

## setHidden

```TypeScript
setHidden(hiddenState: boolean, callback: AsyncCallback<void>): void
```

Sets a file to hidden state. This API uses an asynchronous callback to return the result.

The private files set to hidden state are located in the private album (in hidden state) and are not open to third-party applications. After obtaining private files from the private album, users can set **hiddenState** to **false** to remove them from the private album.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [setHidden](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#sethidden)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hiddenState | boolean | Yes | Whether to hide the file. The value **true** means to hide the file; the value **false** means the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| 13900020 | if parameter is invalid |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('setHiddenDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  asset.setHidden(true, (err) => {
    if (err == undefined) {
      console.info('setHidden successfully');
    } else {
      console.error('setHidden failed with error:' + err);
    }
  });
}
```

<a id="sethidden-1"></a>

## setHidden

```TypeScript
setHidden(hiddenState: boolean): Promise<void>
```

Sets this file asset to the hidden state. This API uses a promise to return the result.

The private files set to hidden state are located in the private album (in hidden state) and are not open to third-party applications. After obtaining private files from the private album, users can set **hiddenState** to **false** to remove them from the private album.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [setHidden](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#sethidden)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hiddenState | boolean | Yes | Whether to hide the file. The value **true** means to hide the file; the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| 13900020 | if parameter is invalid |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  // Restore a file from a hidden album. Before the operation, ensure that the file exists in the hidden album.
  console.info('setHiddenDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.SYSTEM, userFileManager.AlbumSubType.HIDDEN);
  const album: userFileManager.Album = await albumList.getFirstObject();
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await album.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  asset.setHidden(false).then(() => {
    console.info('setHidden successfully');
  }).catch((err: BusinessError) => {
    console.error('setHidden failed with error:' + err);
  });
}
```

## setUserComment

```TypeScript
setUserComment(userComment: string, callback: AsyncCallback<void>): void
```

Sets user comment information of an image or video. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API can only be used to set user comment information of an image or video.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [setUserComment](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#setusercomment)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userComment | string | Yes | User comment information to set, which cannot exceed 140 characters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('setUserCommentDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let userComment: string = 'test_set_user_comment';
    fileAsset.setUserComment(userComment, (err) => {
      if (err === undefined) {
        console.info('setUserComment successfully');
      } else {
        console.error('setUserComment failed with error: ' + err);
      }
    });
  } catch (err) {
    console.error('setUserCommentDemoCallback failed with error: ' + err);
  }
}
```

<a id="setusercomment-1"></a>

## setUserComment

```TypeScript
setUserComment(userComment: string): Promise<void>
```

Sets user comment information of an image or video. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can only be used to set user comment information of an image or video.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [setUserComment](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#setusercomment)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userComment | string | Yes | User comment information to set, which cannot exceed 140 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('setUserCommentDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let userComment: string = 'test_set_user_comment';
    await fileAsset.setUserComment(userComment);
  } catch (err) {
    console.error('setUserCommentDemoCallback failed with error: ' + err);
  }
}
```

## displayName

```TypeScript
displayName: string
```

File name, including the file name extension, to display.

**Type:** string

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [displayName](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#displayname)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## fileType

```TypeScript
readonly fileType: FileType
```

Type of the file.

**Type:** [FileType](arkts-corefile-userfilemanager-filetype-e-sys.md)

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [photoType](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#phototype)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## uri

```TypeScript
readonly uri: string
```

Media asset URI, for example, **file://media/Photo/1/IMG_datetime_0001/displayName.jpg**. For details, see [Media File URI](../../../file-management/user-file-uri-intro.md#media-file-uri).

**Type:** string

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [uri](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md#uri)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.
