# Interface (PhotoAsset)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=d036437fca9f1387f05ed5f1104d3980c50e5643 translatedAt=2026-11-03T07:13:30.549Z pushedAt=2026-11-04T03:11:19.979Z nl=1 -->

PhotoAsset provides APIs for encapsulating file asset attributes.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## Properties

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name                     | Type                    | Read-Only| Optional| Description                                                  |
| ------------------------- | ------------------------ | ---- | ---- | ------------------------------------------------------ |
| uri                       | string                   | Yes  | No  | Media asset URI, for example, **file://media/Photo/1/IMG_datetime_0001/displayName.jpg**. For details, see [Media File URI](../../file-management/user-file-uri-intro.md#media-file-uri).<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| photoType   | [PhotoType](arkts-apis-photoAccessHelper-e.md#phototype) | Yes  | No  | Type of the file.<br>**Atomic service API**: This API can be used in atomic services since API version 20.                                              |
| displayName               | string                   | Yes   | No   | Display file name, including the file extension. The string length ranges from 1 to 255 characters.<br>**Atomic service API:** Since API version 20, this API is supported in atomic services.         |

## get

get(member: string): MemberType

Obtains a **PhotoAsset** member parameter.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name     | Type                       | Mandatory  | Description   |
| -------- | ------------------------- | ---- | ----- |
| member | string | Yes | Member parameter name. When calling get, except for the four attributes 'uri', 'media_type', 'subtype', and 'display_name', all other attributes must be added to fetchColumns as the [PhotoKeys](arkts-apis-photoAccessHelper-e.md#photokeys) to obtain. For example, to obtain the title attribute, add ['title'] to fetchColumns. |

**Return value**

| Type               | Description                             |
| ------------------- | --------------------------------- |
| [MemberType](arkts-apis-photoAccessHelper-t.md#membertype) | **PhotoAsset** member parameter obtained.|

**Error codes**

For details about the error codes, see [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020     | Invalid argument.         |
| 14000014     | The provided member must be a property name of PhotoKey.         |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('photoAssetGetDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: ['title'],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let title: photoAccessHelper.PhotoKeys = photoAccessHelper.PhotoKeys.TITLE;
    let photoAssetTitle: photoAccessHelper.MemberType = photoAsset.get(title.toString());
    console.info('photoAsset Get photoAssetTitle = ', photoAssetTitle);
  } catch (err) {
    console.error(`release failed. error: ${err.code}, ${err.message}`);
  }
}
```

## set

set(member: string, value: string): void

Sets a **PhotoAsset** member parameter.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name     | Type                       | Mandatory  | Description   |
| -------- | ------------------------- | ---- | ----- |
| member | string | Yes | Name of the member parameter, for example, [PhotoKeys](arkts-apis-photoAccessHelper-e.md#photokeys).TITLE. The string length ranges from 1 to 255 characters. |
| value | string | Yes | Value of the member parameter to set. Only the value of [PhotoKeys](arkts-apis-photoAccessHelper-e.md#photokeys).TITLE can be modified. The title specifications are as follows:<br>- The file extension should not be included.<br>- The file name string length ranges from 1 to 255 characters (the asset file name is the title plus the file extension).<br>- The following illegal English characters are not allowed: . \ / : * ? " ' ` < > \| { } [ ] |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1. The number of parameters is invalid, expected 1 or 2 parameters.<br>2. The member parameter must be a string. |
| 14000014 | member not exist. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('photoAssetSetDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: ['title'],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let title: string = photoAccessHelper.PhotoKeys.TITLE.toString();
    photoAsset.set(title, 'newTitle');
  } catch (err) {
    console.error(`release failed. error: ${err.code}, ${err.message}`);
  }
}
```

## commitModify

commitModify(callback: AsyncCallback&lt;void&gt;): void

Commits the modification on the file metadata to the database. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name     | Type                       | Mandatory  | Description   |
| -------- | ------------------------- | ---- | ----- |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback function. If the file metadata is modified successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

Error code 14000001 indicates that the display name is invalid. For details about the format and length requirements of the file name, see the DISPLAY_NAME field in [PhotoKeys](arkts-apis-photoAccessHelper-e.md#photokeys).


| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. <br> Applicable versions: 11+ |
| 13900012     | Permission denied. <br> Applicable versions: 10         |
| 13900020 | Invalid parameter. Possible causes:<br>1. The number of parameters exceeds the maximum limit.<br>2. The member parameter must be a string. |
| 14000001 | Display name invalid. Possible causes:<br>1. Title is invalid.<br>2. Cannot modify displayName for burst photos.<br>3. Invalid displayName. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. IPC call failed, possible causes: <br>(1) Server internal error; <br>(2) Database operation failed. Please retry and check logs.<br>2. Database update failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('commitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: ['title'],
    predicates: predicates
  };
  // Obtain the photo asset collection.
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  // Obtain the first photo asset object.
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  if (photoAsset === undefined) {
    console.error('photoAsset is undefined');
    return;
  }
  let title: string = photoAccessHelper.PhotoKeys.TITLE.toString();
  // Obtain the current title value.
  let photoAssetTitle: photoAccessHelper.MemberType = photoAsset.get(title);
  console.info('photoAsset get photoAssetTitle = ', photoAssetTitle);
  photoAsset.set(title, 'newTitle2');
  photoAsset.commitModify((err) => {
    if (!err) {
      let newPhotoAssetTitle: photoAccessHelper.MemberType = photoAsset.get(title);
      console.info('photoAsset get newPhotoAssetTitle = ', newPhotoAssetTitle);
    } else {
      console.error(`commitModify failed, error: ${err.code}, ${err.message}`);
    }
  });
}
```

## commitModify

commitModify(): Promise&lt;void&gt;

Commits the modification on the file metadata to the database. This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value**

| Type                 | Description        |
| ------------------- | ---------- |
| Promise&lt;void&gt; |Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

If error code 14000001 is returned, refer to [PhotoKeys](arkts-apis-photoAccessHelper-e.md#photokeys) to learn about the format and length requirements of the file name.

In API version 13 and earlier versions, if the caller does not have the required permission, error code 13900012 is returned. Starting from API version 14, the same situation raises error code 201.

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. <br> Applicable versions: 11+ |
| 13900012     | Permission denied. <br> Applicable versions: 10         |
| 13900020 | Invalid parameter. Possible causes:<br>1. The number of parameters exceeds the maximum limit.<br>2. The member parameter must be a string. |
| 14000001 | Display name invalid. Possible causes:<br>1. Title is invalid.<br>2. Cannot modify displayName for burst photos.<br>3. Invalid displayName. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. IPC call failed, possible causes: <br>(1) Server internal error; <br>(2) Database operation failed. Please retry and check logs.<br>2. Database update failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('commitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: ['title'],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  if (photoAsset === undefined) {
    console.error('commitModifyPromise photoAsset is undefined');
    return;
  }
  let title: string = photoAccessHelper.PhotoKeys.TITLE.toString();
  let photoAssetTitle: photoAccessHelper.MemberType = photoAsset.get(title);
  console.info('photoAsset get photoAssetTitle = ', photoAssetTitle);
  photoAsset.set(title, 'newTitle3');
  try {
    await photoAsset.commitModify();
    let newPhotoAssetTitle: photoAccessHelper.MemberType = photoAsset.get(title);
    console.info('photoAsset get newPhotoAssetTitle = ', newPhotoAssetTitle);
  } catch (err) {
    console.error(`release failed. error: ${err.code}, ${err.message}`);
  }
}
```

## close<sup>(deprecated)</sup>

close(fd: number, callback: AsyncCallback&lt;void&gt;): void

Closes the current file. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [fileIo.close](../apis-core-file-kit/js-apis-file-fs.md#fileioclose-1) instead.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name     | Type                       | Mandatory  | Description   |
| -------- | ------------------------- | ---- | ----- |
| fd       | number                    | Yes   | FD of the file to close.|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback function. If the current file is closed successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>The member parameter is invalid, must be a valid member key. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The fd parameter is not a valid number, please check if it is a valid file descriptor returned by getReadOnlyFd().<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('closeDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let fd: number = await photoAsset.getReadOnlyFd();
    console.info('file fd', fd);
    photoAsset.close(fd, (err) => {
      if (err === undefined) {
        console.info('asset close succeed.');
      } else {
        console.error(`close failed, error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`close failed, error: ${err.code}, ${err.message}`);
  }
}
```

## close<sup>(deprecated)</sup>

close(fd: number): Promise&lt;void&gt;

Closes the current file. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [fileIo.close](../apis-core-file-kit/js-apis-file-fs.md#fileioclose) instead.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name | Type    | Mandatory  | Description   |
| ---- | ------ | ---- | ----- |
| fd   | number | Yes   | FD of the file to close.|

**Return value**

| Type                 | Description        |
| ------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1. Parameter count exceeds the limit, maximum 2 parameters.<br>2. Invalid parameter type. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The PhotoAsset object is not a valid PhotoAsset.<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>3. Failed to query the thumbnail, possible causes: <br>(1) Thumbnail does not exist; <br>(2) Database exception. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('closeDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let fd: number = await asset.getReadOnlyFd();
    console.info('file fd', fd);
    await asset.close(fd);
    console.info('asset close succeed.');
  } catch (err) {
    console.error(`close failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getThumbnail

getThumbnail(callback: AsyncCallback&lt;image.PixelMap&gt;): void

Obtains the thumbnail of a file. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name     | Type                                 | Mandatory  | Description              |
| -------- | ----------------------------------- | ---- | ---------------- |
| callback | AsyncCallback&lt;[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt; | Yes   | Callback function. If the thumbnail of a file is successfully obtained, **err** is **undefined**, and **data** is the PixelMap of the thumbnail. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

If error code 13900012 is returned, follow the instructions provided in [Before You Start](../../media/medialibrary/photoAccessHelper-preparation.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900012     | Permission denied.         |
| 13900020     | Invalid argument.         |
| 14000011       | System inner fail.         |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getThumbnailDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  console.info('asset displayName = ', asset.displayName);
  asset.getThumbnail((err, pixelMap) => {
    if (!err) {
      console.info('getThumbnail successful ' + pixelMap);
    } else {
      console.error(`getThumbnail fail with error: ${err.code}, ${err.message}`);
    }
  });
}
```

## getThumbnail

getThumbnail(size: image.Size, callback: AsyncCallback&lt;image.PixelMap&gt;): void

Obtains the file thumbnail of the given size. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name     | Type                                 | Mandatory  | Description              |
| -------- | ----------------------------------- | ---- | ---------------- |
| size     | [image.Size](../apis-image-kit/arkts-apis-image-i.md#size) | Yes    | Thumbnail size. The width and height must be positive integers, in pixels (px). |
| callback | AsyncCallback&lt;[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt; | Yes   | Callback function. If the thumbnail of a file is successfully obtained, **err** is **undefined**, and **data** is the PixelMap of the thumbnail. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

If error code 13900012 is returned, follow the instructions provided in [Before You Start](../../media/medialibrary/photoAccessHelper-preparation.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900012     | Permission denied.         |
| 13900020 | Invalid parameter. Possible causes:<br>1. Parameter count exceeds the limit, maximum 2 parameters.<br>2. Invalid parameter type. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Invalid number of parameters, expected 0 to 2 parameters.<br>2. The PhotoAsset object is not a valid PhotoAsset.<br>3. The size parameter is not a valid image.Size object, please check if width and height are valid numbers.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>5. Failed to query the thumbnail, possible causes: <br>(1) Thumbnail does not exist; <br>(2) Database exception. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getThumbnailDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let size: image.Size = { width: 720, height: 720 };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset = await fetchResult.getFirstObject();
    console.info('asset displayName = ', asset.displayName);
    asset.getThumbnail(size, (err, pixelMap) => {
      if (!err) {
        console.info('getThumbnail successful ' + pixelMap);
      } else {
        console.error(`getThumbnail fail with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (error) {
    console.error(`Error fetching assets: ${error.message}`);
  }
}
```

## getThumbnail

getThumbnail(size?: image.Size): Promise&lt;image.PixelMap&gt;

Obtains the file thumbnail of the given size. This API uses a promise to return the result.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name | Type            | Mandatory  | Description   |
| ---- | -------------- | ---- | ----- |
| size | [image.Size](../apis-image-kit/arkts-apis-image-i.md#size) | No    | Thumbnail size. Value rule: width and height are positive integers. If not passed, the default size 256×256 is used. Unit: pixel (px). |

**Return value**

| Type                           | Description                   |
| ----------------------------- | --------------------- |
| Promise&lt;[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt; | Promise used to return the PixelMap of the thumbnail.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

If error code 13900012 is returned, follow the instructions provided in [Before You Start](../../media/medialibrary/photoAccessHelper-preparation.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900012     | Permission denied.         |
| 13900020 | Invalid parameter. Possible causes:<br>1. Parameter count exceeds the limit, maximum 2 parameters.<br>2. Invalid parameter type. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Invalid number of parameters, expected 0 to 2 parameters.<br>2. The PhotoAsset object is not a valid PhotoAsset.<br>3. The size parameter is not a valid image.Size object, please check if width and height are valid numbers.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>5. Failed to query the thumbnail, possible causes: <br>(1) Thumbnail does not exist; <br>(2) Database exception. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getThumbnailDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let size: image.Size = { width: 720, height: 720 };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  console.info('asset displayName = ', asset.displayName);
  asset.getThumbnail(size).then((pixelMap) => {
    console.info('getThumbnail successful ' + pixelMap);
  }).catch((err: BusinessError) => {
    console.error(`getThumbnail fail with error: ${err.code}, ${err.message}`);
  });
}
```

## clone<sup>14+</sup>

clone(title: string): Promise&lt;PhotoAsset&gt;

Clones this asset. You can set the file name, but changing the file type is not supported. This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE\_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name       | Type     | Mandatory  | Description                                |
| ---------- | ------- | ---- | ---------------------------------- |
| title| string | Yes | Title of the cloned asset. The parameter specifications are as follows:<br>- It must not contain a file extension.<br>- The file name string length ranges from 1 to 255 characters (the asset file name consists of the title plus the file extension).<br>- The following illegal English characters are not allowed: . \ / : * ? " ' ` < > \| { } [ ] |

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt; | Promise object used to return the new [PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md) object generated after cloning. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID   | Error Message                             |
| :------- | :-------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { systemDateTime } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let title: string = systemDateTime.getTime().toString();
    let newAsset: photoAccessHelper.PhotoAsset = await photoAsset.clone(title);
    console.info('get new asset successfully');
  } catch (error) {
    console.error(`failed to get new asset. message =  ${error.code}, ${error.message}`);
  }
}
```

## getReadOnlyFd<sup>(deprecated)</sup>

getReadOnlyFd(callback: AsyncCallback&lt;number&gt;): void

Opens this file in read-only mode. This API uses an asynchronous callback to return the result.

The returned FD must be closed when it is not required.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [fileIo.open](../apis-core-file-kit/js-apis-file-fs.md#fileioopen-1) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name     | Type                         | Mandatory  | Description                                 |
| -------- | --------------------------- | ---- | ----------------------------------- |
| callback | AsyncCallback&lt;number&gt; | Yes   | Callback function. If the current file is opened successfully, **err** is **undefined**, and **data** is the file descriptor. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

In API version 13 and earlier versions, if the caller does not have the required permission, error code 13900012 is returned. Starting from API version 14, the same situation raises error code 201.

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 13900020 | Invalid parameter. Possible causes:<br>1. Parameter count exceeds the limit or invalid PhotoAsset object.<br>2. The PhotoAsset is not a valid PhotoAsset object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>2. Failed to open the file, please check if the file exists and the application has permission to access it. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getReadOnlyFdDemo');
  // Ensure that there are images and video files in the device.
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let assetResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let photoAsset: photoAccessHelper.PhotoAsset = await assetResult.getFirstObject();
  photoAsset.getReadOnlyFd((err, fd) => {
    if (!err) {
      console.info('File fd' + fd);
      photoAsset.close(fd);
    } else {
      console.error(`getReadOnlyFd err: ${err.code}, ${err.message}`);
    }
  });
}
```

## getReadOnlyFd<sup>(deprecated)</sup>

getReadOnlyFd(): Promise&lt;number&gt;

Opens this file asset in read-only mode. This API uses a promise to return the result.

The returned FD must be closed when it is not required.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [fileIo.open](../apis-core-file-kit/js-apis-file-fs.md#fileioopen) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value**

| Type                   | Description           |
| --------------------- | ------------- |
| Promise&lt;number&gt; | Promise used to return the FD of the file opened.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

In API version 13 and earlier versions, if the caller does not have the required permission, error code 13900012 is returned. Starting from API version 14, the same situation raises error code 201.

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 13900020 | Invalid parameter. Possible causes:<br>1. Parameter count exceeds the limit or invalid PhotoAsset object.<br>2. The PhotoAsset is not a valid PhotoAsset object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>2. Failed to open the file, please check if the file exists and the application has permission to access it. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getReadOnlyFdDemo');
  try {
    // Ensure that there are images and video files in the device.
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let assetResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await assetResult.getFirstObject();
    if (photoAsset === undefined) {
      console.error('photoAsset is undefined');
      return;
    }
    let fd: number = await photoAsset.getReadOnlyFd();
    if (!err) {
      console.info('File fd' + fd);
      photoAsset.close(fd);
    } else {
      console.error('getReadOnlyFd fail');
    }
  } catch (err) {
    console.error(`getReadOnlyFd demo err: ${err.code}, ${err.message}`);
  }
}
```

