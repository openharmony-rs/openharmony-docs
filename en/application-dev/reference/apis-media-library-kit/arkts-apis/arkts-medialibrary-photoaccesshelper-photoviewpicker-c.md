# PhotoViewPicker

```TypeScript
class PhotoViewPicker
```

PhotoViewPicker provides APIs for the user to select images and videos. Before using the APIs of PhotoViewPicker, you need to create a PhotoViewPicker instance.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## select

```TypeScript
select(option?: PhotoSelectOptions): Promise<PhotoSelectResult>
```

Starts a **photoPicker** page for the user to select one or more images or videos. This API uses a promise to return the result. You can pass in **PhotoSelectOptions** to specify the type and maximum number of the files to select. A **PhotoSelectResult** object is returned.

> **NOTE:** 
> 
> **photoUris** in the PhotoSelectResult object returned by this API has permanent authorization and can be used
> only by calling
> [photoAccessHelper.getAssets](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getassets)
> . For details, see
> [Using a Media File URI](../../../file-management/user-file-uri-intro.md#using-a-media-file-uri).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [PhotoSelectOptions](arkts-medialibrary-photoaccesshelper-photoselectoptions-c.md) | No | Options for selecting files. If this parameter is not specified, up to 50 images and videos are selected by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PhotoSelectResult](arkts-medialibrary-photoaccesshelper-photoselectresult-c.md)&gt; | Promise used to return information about the images or videos selected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900042 | Unknown error |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scene parameters validate failed, possible causes:<br>1. An illegal enumeration value was passed to PhotoSelectOptions.globalMovingPhotoState. Only MOVING_PHOTO_ENABLED and MOVING_PHOTO_DISABLED are supported for configuration; <br>2. An illegal enumeration value was passed to PhotoSelectOptions.assetCompatibleAbility.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example01(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let photoSelectOptions = new photoAccessHelper.PhotoSelectOptions();
    photoSelectOptions.MIMEType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_TYPE;
    photoSelectOptions.maxSelectNumber = 5;
    let photoPicker = new photoAccessHelper.PhotoViewPicker();
    photoPicker.select(photoSelectOptions).then((photoSelectResult: photoAccessHelper.PhotoSelectResult) => {
      console.info('PhotoViewPicker.select successfully, photoSelectResult uri: ' + JSON.stringify(photoSelectResult));
    }).catch((err: BusinessError) => {
      console.error(`PhotoViewPicker.select failed with err: ${err.code}, ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err: ${err.code}, ${err.message}`);
  }
}
```

<a id="select-1"></a>

## select

```TypeScript
select(option: PhotoSelectOptions, callback: AsyncCallback<PhotoSelectResult>): void
```

Starts a **photoPicker** page for the user to select one or more images or videos. This API uses an asynchronous callback to return the result. You can pass in **PhotoSelectOptions** to specify the media file type and the maximum number of files to select.

> **NOTE:** 
> 
> **photoUris** in the PhotoSelectResult object returned by this API has permanent authorization and can be used
> only by calling
> [photoAccessHelper.getAssets](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getassets)
> . For details, see
> [Using a Media File URI](../../../file-management/user-file-uri-intro.md#using-a-media-file-uri).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [PhotoSelectOptions](arkts-medialibrary-photoaccesshelper-photoselectoptions-c.md) | Yes | Options for selecting images or videos. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PhotoSelectResult](arkts-medialibrary-photoaccesshelper-photoselectresult-c.md)&gt; | Yes | Callback used to return information about the images or videos selected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900042 | Unknown error |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scene parameters validate failed, possible causes:<br>1. An illegal enumeration value was passed to PhotoSelectOptions.globalMovingPhotoState. Only MOVING_PHOTO_ENABLED and MOVING_PHOTO_DISABLED are supported for configuration;<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example02(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let photoSelectOptions = new photoAccessHelper.PhotoSelectOptions();
    photoSelectOptions.MIMEType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_TYPE;
    photoSelectOptions.maxSelectNumber = 5;
    let photoPicker = new photoAccessHelper.PhotoViewPicker();
    photoPicker.select(photoSelectOptions, (err: BusinessError, photoSelectResult: photoAccessHelper.PhotoSelectResult) => {
      if (err) {
        console.error(`PhotoViewPicker.select failed with err: ${err.code}, ${err.message}`);
        return;
      }
      console.info('PhotoViewPicker.select successfully, photoSelectResult uri: ' + JSON.stringify(photoSelectResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err: ${err.code}, ${err.message}`);
  }
}
```

<a id="select-2"></a>

## select

```TypeScript
select(callback: AsyncCallback<PhotoSelectResult>): void
```

Starts a **photoPicker** page for the user to select one or more images or videos. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> **photoUris** in the PhotoSelectResult object returned by this API has permanent authorization and can be used
> only by calling
> [photoAccessHelper.getAssets](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getassets)
> . For details, see
> [Using a Media File URI](../../../file-management/user-file-uri-intro.md#using-a-media-file-uri).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PhotoSelectResult](arkts-medialibrary-photoaccesshelper-photoselectresult-c.md)&gt; | Yes | Callback used to return information about the images or videos selected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 13900042 | Unknown error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example01(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let photoSelectOptions = new photoAccessHelper.PhotoSelectOptions();
    photoSelectOptions.MIMEType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_TYPE;
    photoSelectOptions.maxSelectNumber = 5;
    let photoPicker = new photoAccessHelper.PhotoViewPicker();
    photoPicker.select(photoSelectOptions).then((photoSelectResult: photoAccessHelper.PhotoSelectResult) => {
      console.info('PhotoViewPicker.select successfully, photoSelectResult uri: ' + JSON.stringify(photoSelectResult));
    }).catch((err: BusinessError) => {
      console.error(`PhotoViewPicker.select failed with err: ${err.code}, ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err: ${err.code}, ${err.message}`);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example02(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let photoSelectOptions = new photoAccessHelper.PhotoSelectOptions();
    photoSelectOptions.MIMEType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_TYPE;
    photoSelectOptions.maxSelectNumber = 5;
    let photoPicker = new photoAccessHelper.PhotoViewPicker();
    photoPicker.select(photoSelectOptions, (err: BusinessError, photoSelectResult: photoAccessHelper.PhotoSelectResult) => {
      if (err) {
        console.error(`PhotoViewPicker.select failed with err: ${err.code}, ${err.message}`);
        return;
      }
      console.info('PhotoViewPicker.select successfully, photoSelectResult uri: ' + JSON.stringify(photoSelectResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err: ${err.code}, ${err.message}`);
  }
}
```
