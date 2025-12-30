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

<!-- @[Supported_Resource_Formats](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MediaLibraryKit/SaveButtonSample/entry/src/main/ets/pages/Scene1.ets) -->

``` TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { common } from '@kit.AbilityKit';

@Entry({ routeName : 'Scene1' })
@Component
export struct Scene1 {
  @State outputText: string = 'Supported formats:\n';

  build() {
    NavDestination() {
      Column({ space: 20 }) {
        // ...

        Button('example')
          .width('80%')
          .height(50)
          .fontSize(16)
          .onClick(async () => {
            let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
            let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
            this.outputText = await example(phAccessHelper);
          })

        // ...
      }
      .width('100%')
      .height('100%')
    }
    .title('Supported Formats')
  }
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper): Promise<string> {
  try {
    let outputText = 'Supported formats:\n';
    // The value 1 means the supported image formats, and 2 means the supported video formats.
    let imageFormat = await phAccessHelper.getSupportedPhotoFormats(1);
    let result = '';
    for (let i = 0; i < imageFormat.length; i++) {
      result += imageFormat[i];
      if (i !== imageFormat.length - 1) {
        result += ', ';
      }
    }
    outputText += result;
    console.info('getSupportedPhotoFormats success, data is ' + outputText);
    return 'getSupportedPhotoFormats success, data is\n' + outputText;
  } catch (error) {
    console.error('getSupportedPhotoFormats failed, errCode is', error);
    return 'getSupportedPhotoFormats failed, errCode is\n' + JSON.stringify(error);
  }
}
```

## 使用安全控件保存媒体库资源

安全控件的介绍可参考[安全控件的保存控件](../../reference/apis-arkui/arkui-ts/ts-security-components-savebutton.md)。

下面以使用安全控件创建一张图片资源为例。

**开发步骤**

1. 设置安全控件按钮属性。
2. 创建安全控件按钮。
3. 调用[MediaAssetChangeRequest.createImageAssetRequest](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#createimageassetrequest11)和[PhotoAccessHelper.applyChanges](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#applychanges11)接口创建图片资源。

<!-- @[Creating_Media_Asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MediaLibraryKit/SaveButtonSample/entry/src/main/ets/pages/Scene2.ets) -->

``` TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { common } from '@kit.AbilityKit';
// ...
@Entry({ routeName : 'Scene2' })
@Component
export struct Scene2 {
  @State statusMessage: string = '';
  @State imageSource: string = '';

  saveButtonOptions: SaveButtonOptions = {
    icon: SaveIconStyle.FULL_FILLED,
    text: SaveDescription.SAVE_IMAGE,
    buttonType: ButtonType.Capsule
  }// Set properties of SaveButton.

 // ...

  build() {
    NavDestination() {
      Column({ space: 20 }) {
        // ...

        SaveButton(this.saveButtonOptions) // Create a button with SaveButton.
          .onClick(async (event, result: SaveButtonOnClickResult) => {
            if (result == SaveButtonOnClickResult.SUCCESS) {
              try {
                let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
                let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
                
                // 需要确保fileUri对应的资源存在。
                let fileUri = 'file://' + context.filesDir + '/test.jpg';
                let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest =
                  photoAccessHelper.MediaAssetChangeRequest.createImageAssetRequest(context, fileUri);

                await phAccessHelper.applyChanges(assetChangeRequest);

                let resultUri = assetChangeRequest.getAsset().uri;
                this.statusMessage = 'createAsset successfully, uri: ' + resultUri;
                console.info('createAsset successfully, uri: ' + resultUri);
              } catch (err) {
                this.statusMessage = `create asset failed with error: ${err.code}, ${err.message}`;
                console.error(`create asset failed with error: ${err.code}, ${err.message}`);
              }
            } else {
              this.statusMessage = 'SaveButtonOnClickResult create asset failed';
              console.error('SaveButtonOnClickResult create asset failed');
            }
          })

        // ...
      }
      .width('100%')
      .height('100%')
    }
    .title('SaveButton Example')
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

<!-- @[Saving_MediaAsset_Using_Authorization_Popup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MediaLibraryKit/SaveButtonSample/entry/src/main/ets/pages/Scene3.ets) -->

``` TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
// ...
import { fileIo } from '@kit.CoreFileKit';

// ...

async function example(
  phAccessHelper: photoAccessHelper.PhotoAccessHelper,
  context: common.UIAbilityContext
): Promise<string> {
  try {
    // Specify the URI of the image in the application sandbox directory to be saved.
    let srcFileUri = context.filesDir + '/test.jpg';
    let srcFileUris: string[] = [
      srcFileUri
    ];
    //Set parameters for the image to save: file extension, image type, title and subtype (both optional)
    let photoCreationConfigs: photoAccessHelper.PhotoCreationConfig[] = [
      {
        title: 'test', // This parameter is optional.
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE,
        subtype: photoAccessHelper.PhotoSubtype.DEFAULT,
      }
    ];

    console.info('Source URI: ' + srcFileUri);
    // Obtain the target URI in the media library based on pop-up authorization.
    let desFileUris: string[] = 
      await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
    console.info('Destination URIs: ' + JSON.stringify(desFileUris));
    // Write image from sandbox directory to target URI in media library.
    let desFile: fileIo.File = await fileIo.open(desFileUris[0], fileIo.OpenMode.WRITE_ONLY);
    let srcFile: fileIo.File = await fileIo.open(srcFileUri, fileIo.OpenMode.READ_ONLY);
    await fileIo.copyFile(srcFile.fd, desFile.fd);
    fileIo.closeSync(srcFile);
    fileIo.closeSync(desFile);
    console.info('create asset by dialog successfully');
    return 'create asset by dialog successfully';
  } catch (err) {
    console.error(`failed to create asset by dialog successfully errCode is: ${err.code}, ${err.message}`);
    return `failed to create asset by dialog successfully errCode is: ${err.code}, ${err.message}`;
  }
}
```
