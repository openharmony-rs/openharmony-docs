# Class (PhotoViewPicker)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xuchangda-->
<!--Designer: @guxinggang-->
<!--Tester: @wangbeibei-->
<!--Adviser: @w_Machine_cc-->

PhotoViewPicker是图库选择器对象，用于拉起系统图库选择界面，支持选择一个或多个图片、视频等媒体文件。用户可以自定义选择媒体类型和数量限制，适用于需要从图库中选择图片或视频的应用场景。使用前需先创建PhotoViewPicker实例。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 如果需要重复拉起PhotoViewPicker，需要先销毁前一个PhotoViewPicker实例，可通过NavDestination销毁或等待进程销毁。

## 导入模块

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## select

select(option?: PhotoSelectOptions) : Promise&lt;PhotoSelectResult&gt;

通过选择模式拉起图库选择器界面，用户可以选择一个或多个图片/视频。使用Promise异步回调。传入可选参数PhotoSelectOptions对象，返回PhotoSelectResult对象。

> **注意：**
>
> 此接口返回的PhotoSelectResult对象中的photoUris具有永久授权，可通过调用接口[photoAccessHelper.getAssets](arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets)去使用。具体操作请参考[媒体文件URI的使用方式](../../file-management/user-file-uri-intro.md#媒体文件uri的使用方式)。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名  | 类型    | 必填 | 说明                       |
| ------- | ------- | ---- | -------------------------- |
| option | [photoAccessHelper.PhotoSelectOptions](arkts-apis-photoAccessHelper-class.md#photoselectoptions) | 否   | photoPicker选择选项，若无此参数，则默认选择媒体文件类型为图片和视频类型，默认选择媒体文件数量的最大值为50。 |

**返回值：**

| 类型                            | 说明    |
| ----------------------------- | :---- |
| Promise&lt;[photoAccessHelper.PhotoSelectResult](arkts-apis-photoAccessHelper-class.md#photoselectresult)&gt; | Promise对象。返回PhotoSelectResult对象，包含photoUris（选择的图片/视频URI数组）和isOriginal（是否原图）等字段。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)、[文件管理错误码](../apis-core-file-kit/errorcode-filemanagement.md)和[媒体库错误码](errorcode-medialibrary.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. | 
| 13900042      | Unknown error.         |
| 23800151      |  Scene parameters validate failed, possible causes: 1. An illegal enumeration value was passed to PhotoSelectOptions.globalMovingPhotoState. Only MOVING_PHOTO_ENABLED and MOVING_PHOTO_DISABLED are supported for configuration;<br>2. An illegal enumeration value was passed to PhotoSelectOptions.assetCompatibleAbility.<br>适用版本：12|

**示例：**

```ts
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

通过选择模式拉起图库选择器界面，用户可以选择一个或多个图片/视频。接口采用callback异步返回形式，必须传入参数PhotoSelectOptions对象，返回PhotoSelectResult对象。

> **注意：**
>
> 此接口返回的PhotoSelectResult对象中的photoUris具有永久授权，可通过调用接口[photoAccessHelper.getAssets](arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets)去使用。具体操作请参考[媒体文件URI的使用方式](../../file-management/user-file-uri-intro.md#媒体文件uri的使用方式)。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名  | 类型    | 必填 | 说明                       |
| ------- | ------- | ---- | -------------------------- |
| option | [photoAccessHelper.PhotoSelectOptions](arkts-apis-photoAccessHelper-class.md#photoselectoptions) | 是   | photoPicker选择选项，若无此参数，则默认选择媒体文件类型为图片和视频类型，默认选择媒体文件数量的最大值为50。 |
| callback | AsyncCallback&lt;[photoAccessHelper.PhotoSelectResult](arkts-apis-photoAccessHelper-class.md#photoselectresult)&gt;      | 是   | callback 返回PhotoPicker选择后的结果集，包含photoUris（选择的图片/视频URI数组）和isOriginal（是否原图）等字段。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)、[文件管理错误码](../apis-core-file-kit/errorcode-filemanagement.md)和[媒体库错误码](errorcode-medialibrary.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. | 
| 13900042      | Unknown error.         |
| 23800151      | Scene parameters validate failed, possible causes: 1. An illegal enumeration value was passed to PhotoSelectOptions.globalMovingPhotoState. Only MOVING_PHOTO_ENABLED and MOVING_PHOTO_DISABLED are supported for configuration; <br>适用版本：12|

**示例：**

```ts
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

通过选择模式拉起图库选择器界面，用户可以选择一个或多个图片/视频。接口采用callback异步返回形式，返回PhotoSelectResult对象。默认选择媒体文件类型为图片和视频类型，默认选择媒体文件数量的最大值为50。

> **注意：**
>
> 此接口返回的PhotoSelectResult对象中的photoUris具有永久授权，可通过调用接口[photoAccessHelper.getAssets](arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets)去使用。具体操作请参考[媒体文件URI的使用方式](../../file-management/user-file-uri-intro.md#媒体文件uri的使用方式)。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名  | 类型    | 必填 | 说明                       |
| ------- | ------- | ---- | -------------------------- |
| callback | AsyncCallback&lt;[photoAccessHelper.PhotoSelectResult](arkts-apis-photoAccessHelper-class.md#photoselectresult)&gt;      | 是   | callback 返回PhotoPicker选择后的结果集，包含photoUris（选择的图片/视频URI数组）和isOriginal（是否原图）等字段。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](../apis-core-file-kit/errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401    | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 13900042      | Unknown error.         |

**示例：**

```ts
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
