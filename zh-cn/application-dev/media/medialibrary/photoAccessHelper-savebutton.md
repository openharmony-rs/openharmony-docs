# 保存媒体库资源
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

保存图片、视频等用户文件到图库时，无需申请相册管理模块权限'ohos.permission.WRITE_IMAGEVIDEO'，应用可以通过[安全控件](#使用安全控件保存媒体库资源)或[授权弹窗](#使用弹窗授权保存媒体库资源)的方式，将用户指定的媒体资源保存到图库中。

> **注意：**
> Media Library Kit提供图片和视频的管理能力，当需要读取和保存音频文件时，请使用[AudioViewPicker（音频选择器对象）](../../reference/apis-core-file-kit/js-apis-file-picker.md#audioviewpicker)。

## 获取支持保存的资源格式

下面以获取支持保存的图片类型资源格式为例。

**开发步骤**

调用[phAccessHelper.getSupportedPhotoFormats](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getsupportedphotoformats18)接口获取支持保存的图片类型资源格式。

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State outputText: string = '支持的类型为：\n';

  build() {
    Row() {
      Button("example").onClick(async () => {
        let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
        let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
        example(phAccessHelper);
      }).width('100%')
    }
    .height('90%')
  }
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper){
  try {
    let outputText = '支持的类型为：\n';
    // 参数为1表示获取支持的图片类型格式，参数为2表示获取支持的视频类型格式。
    let imageFormat  = await phAccessHelper.getSupportedPhotoFormats(1);
    let result = "";
    for (let i = 0; i < imageFormat.length; i++) {
      result += imageFormat[i];
      if (i !== imageFormat.length - 1) {
        result += ', ';
      }
    }
    outputText += result;
    console.info('getSupportedPhotoFormats success, data is ' + outputText);
  } catch (error) {
    console.error('getSupportedPhotoFormats failed, errCode is', error);
  }
}
```

## 使用安全控件保存媒体库资源

安全控件的介绍可参考API[SaveButton](../../reference/apis-arkui/arkui-ts/ts-security-components-savebutton.md)。保存前可以通过调用[registerChange](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#registerchange)接口注册对默认URI（[DEFAULT_PHOTO_URI](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#defaultchangeuri)）的监听。资源保存成功后，根据接收到该资源的[NOTIFY_ADD](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#notifytype)通知完成后续业务。

下面以使用安全控件创建一张图片资源为例。

**开发步骤**

1. 设置安全控件按钮属性。
2. 创建安全控件按钮。
3. 调用[registerChange](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#registerchange)接口注册对默认URI（[DEFAULT_PHOTO_URI](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#defaultchangeuri)）的监听。
4. 调用[MediaAssetChangeRequest.createImageAssetRequest](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#createimageassetrequest11)和[PhotoAccessHelper.applyChanges](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#applychanges11)接口创建图片资源。
5. 调用[getAsset](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#getasset11)接口获取保存的资产，并获取资产URI。在接收到资产URI的[NOTIFY_ADD](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#notifytype)通知后，完成后续业务。

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { common } from '@kit.AbilityKit';
import { dataSharePredicates } from '@kit.ArkData';

@Entry
@Component
struct Index {
  uriString: string = '';
  saveButtonOptions: SaveButtonOptions = {
    icon: SaveIconStyle.FULL_FILLED,
    text: SaveDescription.SAVE_IMAGE,
    buttonType: ButtonType.Capsule
  } // 设置安全控件按钮属性。
  onCallback = (changeData: photoAccessHelper.ChangeData) => {
    for (let i = 0; i < changeData.uris.length; i++) {
      // 保存媒体库资源成功后，会监听到类型为NOTIFY_ADD的资产URI。
      if (changeData.uris[i] === this.uriString && changeData.type === photoAccessHelper.NotifyType.NOTIFY_ADD) {
        let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
        predicates.equalTo(photoAccessHelper.PhotoKeys.URI, changeData.uris[i]);
        let fetchOptions: photoAccessHelper.FetchOptions = {
          fetchColumns: [],
          predicates: predicates
        };

        let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
        let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
        phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
          if (fetchResult !== undefined) {
            let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
            if (photoAsset !== undefined) {
              console.info('getAssets successfully');
            }
          }
          phAccessHelper.unRegisterChange(photoAccessHelper.DefaultChangeUri.DEFAULT_PHOTO_URI);
        });
      }
    }
  }

  build() {
    Row() {
      Column() {
        SaveButton(this.saveButtonOptions)// 创建安全控件按钮。
          .onClick(async (event, result: SaveButtonOnClickResult) => {
            if (result == SaveButtonOnClickResult.SUCCESS) {
               try {
                let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
                let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

                // 注册默认监听。
 	              phAccessHelper.registerChange(
 	              photoAccessHelper.DefaultChangeUri.DEFAULT_PHOTO_URI, true, this.onCallback);

                // 需要确保fileUri对应的资源存在。
                let fileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.jpg';
                let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest =
                  photoAccessHelper.MediaAssetChangeRequest.createImageAssetRequest(context, fileUri);
                await phAccessHelper.applyChanges(assetChangeRequest);

                this.uriString = assetChangeRequest.getAsset().uri;
                console.info('createAsset successfully, uri: ' + this.uriString);
              } catch (err) {
                console.error(`create asset failed with error: ${err.code}, ${err.message}`);
              }
            } else {
              console.error('SaveButtonOnClickResult create asset failed');
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

除了上述通过fileUri从应用沙箱指定资源内容的方式，开发者还可以通过ArrayBuffer的方式添加资源内容，详情请参考[addResource](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#addresource11-1)接口。

## 使用弹窗授权保存媒体库资源

下面以弹窗授权的方式保存一张图片资源为例。

**开发步骤**

1. 指定待保存到媒体库的[应用文件](../../file-management/app-file-access.md)uri（需为应用沙箱路径）。
2. 指定待保存照片的创建选项，包括文件后缀和照片类型，标题和照片子类型可选。
3. 调用[showAssetsCreationDialog](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#showassetscreationdialog12)，基于弹窗授权的方式获取的目标[媒体文件](../../file-management/user-file-uri-intro.md#媒体文件uri)uri。

   弹框需要显示应用名称，无法直接获取应用名称，依赖于配置项的label和icon，因此调用此接口时请确保module.json5文件中的abilities标签中配置了label和icon项。当传入uri为沙箱路径时，可正常保存图片/视频，但无界面预览。
4. 将应用沙箱的照片内容写入媒体库的目标uri。

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { fileIo } from '@kit.CoreFileKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper){
  try {
    // 指定待保存到媒体库的位于应用沙箱的图片uri。
    let srcFileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.jpg';
    let srcFileUris: Array<string> = [
      srcFileUri
    ];
    // 指定待保存照片的创建选项，包括文件后缀和照片类型，标题和照片子类型可选。
    let photoCreationConfigs: Array<photoAccessHelper.PhotoCreationConfig> = [
      {
        title: 'test', // 可选。
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE,
        subtype: photoAccessHelper.PhotoSubtype.DEFAULT, // 可选。
      }
    ];
    // 基于弹窗授权的方式获取媒体库的目标uri。
    let desFileUris: Array<string> = await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
    // 将来源于应用沙箱的照片内容写入媒体库的目标uri。
    let desFile: fileIo.File = await fileIo.open(desFileUris[0], fileIo.OpenMode.WRITE_ONLY);
    let srcFile: fileIo.File = await fileIo.open(srcFileUri, fileIo.OpenMode.READ_ONLY);
    await fileIo.copyFile(srcFile.fd, desFile.fd);
    fileIo.closeSync(srcFile);
    fileIo.closeSync(desFile);
    console.info('create asset by dialog successfully');
  } catch (err) {
    console.error(`failed to create asset by dialog successfully errCode is: ${err.code}, ${err.message}`);
  }
}
```
