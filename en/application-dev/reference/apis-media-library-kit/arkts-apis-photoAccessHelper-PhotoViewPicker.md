# Class (PhotoViewPicker)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xuchangda-->
<!--Designer: @guxinggang-->
<!--Tester: @wangbeibei-->
<!--Adviser: @w_Machine_cc-->

The **PhotoViewPicker** class is a photo picker object used to start the system gallery selection screen, where users can select one or more media files such as images and videos. Users can customize the media type and quantity limit. This class is applicable to scenarios where images or videos need to be selected from the gallery, such as uploading profile pictures in social apps, uploading product images in e-commerce platforms, and selecting media materials in content creation apps. Before using the APIs of **PhotoViewPicker**, you need to create a **PhotoViewPicker** instance.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - To start PhotoViewPicker again, you need to destroy the previous PhotoViewPicker instance through NavDestination or the process.

## Modules to Import

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## select

select(option?: PhotoSelectOptions) : Promise&lt;PhotoSelectResult&gt;

Starts a photo picker page for the user to select one or more images or videos. This API uses a promise to return the result.

You can pass in **PhotoSelectOptions** to specify the type and maximum number of the files to select. A **PhotoSelectResult** object is returned.

> **NOTE**
>
> **photoUris** in the PhotoSelectResult object returned by this API has permanent authorization and can be used only by calling [photoAccessHelper.getAssets](arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets). For details, see [Using a Media File URI](../../file-management/user-file-uri-intro.md#using-a-media-file-uri).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name | Type   | Mandatory| Description                      |
| ------- | ------- | ---- | -------------------------- |
| option | [PhotoSelectOptions](arkts-apis-photoAccessHelper-class.md#photoselectoptions) | No  | Options for selecting files. If this parameter is not specified, up to 50 images and videos are selected by default.|

**Return value**

| Type                           | Description   |
| ----------------------------- | :---- |
| Promise&lt;[PhotoSelectResult](arkts-apis-photoAccessHelper-class.md#photoselectresult)&gt; | Promise used to return information about the images or videos selected.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md), and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900042      | Unknown error.         |
| 23800151      |  Scene parameters validate failed, possible causes: <br>1. An illegal enumeration value was passed to PhotoSelectOptions.globalMovingPhotoState. Only MOVING_PHOTO_ENABLED and MOVING_PHOTO_DISABLED are supported for configuration;<br>2. An illegal enumeration value was passed to PhotoSelectOptions.assetCompatibleAbility.<br>Applicable version: 12|

**Example**

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function openBindSheet01() {
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

## select

select(option: PhotoSelectOptions, callback: AsyncCallback&lt;PhotoSelectResult&gt;) : void

Starts a photo picker page for the user to select one or more images or videos. This API uses an asynchronous callback to return the result.

Pass in **PhotoSelectOptions**. A **PhotoSelectResult** object is returned through the callback.

> **NOTE**
>
> **photoUris** in the PhotoSelectResult object returned by this API has permanent authorization and can be used only by calling [photoAccessHelper.getAssets](arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets). For details, see [Using a Media File URI](../../file-management/user-file-uri-intro.md#using-a-media-file-uri).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name | Type   | Mandatory| Description                      |
| ------- | ------- | ---- | -------------------------- |
| option | [PhotoSelectOptions](arkts-apis-photoAccessHelper-class.md#photoselectoptions) | Yes  | Photo picker selection options.|
| callback | AsyncCallback&lt;[PhotoSelectResult](arkts-apis-photoAccessHelper-class.md#photoselectresult)&gt;      | Yes  | Callback used to return the result. When a user successfully selects an image or video using the photo picker, **err** is **undefined**, and **data** is the result set returned by the photo picker.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md), and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900042      | Unknown error.         |
| 23800151      | Scene parameters validate failed, possible causes: An illegal enumeration value was passed to PhotoSelectOptions.globalMovingPhotoState. Only MOVING_PHOTO_ENABLED and MOVING_PHOTO_DISABLED are supported for configuration. <br>Applicable version: 12|

**Example**

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function openBindSheet02() {
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

## select

select(callback: AsyncCallback&lt;PhotoSelectResult&gt;) : void

Starts a photo picker page for the user to select one or more images or videos. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> **photoUris** in the PhotoSelectResult object returned by this API has permanent authorization and can be used only by calling [photoAccessHelper.getAssets](arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets). For details, see [Using a Media File URI](../../file-management/user-file-uri-intro.md#using-a-media-file-uri).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name | Type   | Mandatory| Description                      |
| ------- | ------- | ---- | -------------------------- |
| callback | AsyncCallback&lt;[PhotoSelectResult](arkts-apis-photoAccessHelper-class.md#photoselectresult)&gt;      | Yes  | Callback used to return the result. When a user successfully selects an image or video using the photo picker, **err** is **undefined**, and **data** is the result set returned by the photo picker.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900042      | Unknown error.         |

**Example**

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function openBindSheet03() {
  try {
    let photoPicker = new photoAccessHelper.PhotoViewPicker();
    photoPicker.select((err: BusinessError, photoSelectResult: photoAccessHelper.PhotoSelectResult) => {
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