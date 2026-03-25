# Saving Media Assets
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

To save images, videos, or similar files to Gallery, it is not necessary for the application to request the ohos.permission.WRITE_IMAGEVIDEO permission. Instead, the application can use the [SaveButton](#saving-media-assets-using-savebutton) or [authorization pop-up](#saving-a-media-asset-using-an-authorization-pop-up) to save the media assets to Gallery.

> **NOTE**
>
> Media Library Kit handles image and video management. If you need to read and save audio files, use [AudioViewPicker](../../reference/apis-core-file-kit/js-apis-file-picker.md#audioviewpicker).

## Obtaining Supported Resource Formats for Saving

The following describes how to obtain image resource formats that can be saved.

**How to Develop**

Call [phAccessHelper.getSupportedPhotoFormats](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getsupportedphotoformats18) to obtain the supported image formats that can be saved.

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State outputText: string = 'Supported formats:\n';

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
    let outputText = 'Supported formats:\n';
    // The value 1 means the supported image formats, and 2 means the supported video formats.
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

## Saving Media Assets Using SaveButton

For details about the SaveButton, see [SaveButton](../../reference/apis-arkui/arkui-ts/ts-security-components-savebutton.md) in the API reference. Before saving the media assets, you can call [registerChange](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#registerchange) to register a listener for the default URI ([DEFAULT_PHOTO_URI](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#defaultchangeuri)). After the media assets are saved successfully, complete the subsequent services based on the [NOTIFY_ADD](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#notifytype) notification received.

The following walks you through on how to create an image using the **SaveButton** security component.

**How to Develop**

1. Set the attributes of the security component.
2. Create a button with the security component.
3. Call [registerChange](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#registerchange) to register a listener for the default URI ([DEFAULT_PHOTO_URI](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#defaultchangeuri)).
4. Use [MediaAssetChangeRequest.createImageAssetRequest](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#createimageassetrequest11) and [PhotoAccessHelper.applyChanges](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#applychanges11) to create an image asset.
5. Call [getAsset](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#getasset11) to obtain the saved assets and asset URI. After receiving the [NOTIFY_ADD](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#notifytype) notification, complete the subsequent services.

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
  } // Set properties of SaveButton.
  onCallback = (changeData: photoAccessHelper.ChangeData) => {
    for (let i = 0; i < changeData.uris.length; i++) {
      // After the assets are saved to media library successfully, an asset URI of type NOTIFY_ADD will be detected by the listener.
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
        SaveButton(this.saveButtonOptions)// Create a security component button.
          .onClick(async (event, result: SaveButtonOnClickResult) => {
            if (result == SaveButtonOnClickResult.SUCCESS) {
               try {
                let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
                let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

                // Register the default listener.
 	              phAccessHelper.registerChange(
 	              photoAccessHelper.DefaultChangeUri.DEFAULT_PHOTO_URI, true, this.onCallback);

                // Ensure that the asset specified by fileUri exists.
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

In addition to specifying the asset in the application sandbox directory using **fileUri**, you can add the asset using ArrayBuffer. For details, see the [addResource](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#addresource11-1).

## Saving a Media Asset Using an Authorization Pop-Up

The following walks you through on how to save an image using an authorization pop-up.

**How to Develop**

1. Specify the URI of the [application file](../../file-management/app-file-access.md) to be saved to the media library. (The file must be in the application sandbox.)
2. Set parameters such as the file name extension, image file type, title (optional) and image subtype (optional) of the image to save.
3. Call [showAssetsCreationDialog](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#showassetscreationdialog12) to obtain the target [media file URI](../../file-management/user-file-uri-intro.md#media-file-uri) through an authorization pop-up.

   To display the application name in the dialog box, the API relies on the configuration of **label** and **icon** under **abilities** in the **module.json5** file. If they are not configured, no application name is displayed in the dialog box. If the passed URI is a sandbox path, images or videos can be saved but cannot be previewed.
4. Write the image content from the application sandbox directory to the file specified by the target URI in the media library.

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { fileIo } from '@kit.CoreFileKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper){
  try {
    // Specify the URI of the image in the application sandbox directory to be saved.
    let srcFileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.jpg';
    let srcFileUris: Array<string> = [
      srcFileUri
    ];
    // Set parameters such as the file name extension, image file type, title (optional) and image subtype (optional) of the image to save.
    let photoCreationConfigs: Array<photoAccessHelper.PhotoCreationConfig> = [
      {
        title: 'test', // This parameter is optional.
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE,
        subtype: photoAccessHelper.PhotoSubtype.DEFAULT, // This parameter is optional.
      }
    ];
    // Obtain the target URI in the media library based on pop-up authorization.
    let desFileUris: Array<string> = await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
    // Write the image content from the application sandbox directory to the file specified by the target URI in the media library.
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
