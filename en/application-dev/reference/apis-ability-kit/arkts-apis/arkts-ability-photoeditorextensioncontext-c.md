# PhotoEditorExtensionContext

The context of Photo Editor extension. It allows access to PhotoEditorExtension-specific resources.

@extends ExtensionContext

**Inheritance/Implementation:** PhotoEditorExtensionContext extends [ExtensionContext](arkts-ability-extensioncontext-c.md)

**Since:** 12

**System capability:** SystemCapability.Ability.AppExtension.PhotoEditorExtension

## saveEditedContentWithImage

```TypeScript
saveEditedContentWithImage(pixeMap: image.PixelMap, option: image.PackingOption): Promise<AbilityResult>
```

Save image data by image pixmap.

**Since:** 12

**System capability:** SystemCapability.Ability.AppExtension.PhotoEditorExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pixeMap | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | Image pixmap. |
| option | [image.PackingOption](../../apis-image-kit/arkts-apis/arkts-image-image-packingoption-i.md) | Yes | Option for image packing. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Returns the result of save. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Params error. Possible causes: 1.Mandatory parameters are left unspecified.<br>2.Incorrect parameter types. |
| [29600001](../errorcode-ability.md#29600001-internal-error-during-image-editing) | Internal error. |
| [29600002](../errorcode-ability.md#29600002-image-input-error) | Image input error. |
| [29600003](../errorcode-ability.md#29600003-image-too-large) | Image too big. |

**Examples**

```TypeScript
import { common, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { image } from '@kit.ImageKit';

const TAG = '[ExamplePhotoEditorAbility]';

@Entry
@Component
struct Index {
  // Original image
  @State originalImage: PixelMap | null = null;

  build() {
    Row() {
      Column() {
        Button('RotateAndSaveImg').onClick(event => {
          hilog.info(0x0000, TAG, `Start to edit image and save.`);

          this.originalImage?.rotate(90).then(() => {
            let packOpts: image.PackingOption = { format: 'image/jpeg', quality: 98 };
            try {
              let context = this.getUIContext().getHostContext() as common.PhotoEditorExtensionContext;
              context.saveEditedContentWithImage(this.originalImage as image.PixelMap,
                packOpts).then(data => {
                  hilog.info(0x0000, TAG,
                    `saveContentEditingWithImage result: ${JSON.stringify(data)}`);
                });
            } catch (e) {
              hilog.error(0x0000, TAG, `saveContentEditingWithImage failed:${e}`);
              return;
            }
          })
        }).margin({ top: 10 })
      }
    }
  }
}
```

## saveEditedContentWithUri

```TypeScript
saveEditedContentWithUri(uri: string): Promise<AbilityResult>
```

Save image data by uri.

**Since:** 12

**System capability:** SystemCapability.Ability.AppExtension.PhotoEditorExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Image editing URI. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Returns the result of save. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Params error. Possible causes: 1.Mandatory parameters are left unspecified.<br>2.Incorrect parameter types. |
| [29600001](../errorcode-ability.md#29600001-internal-error-during-image-editing) | Internal error. |
| [29600002](../errorcode-ability.md#29600002-image-input-error) | Image input error. |
| [29600003](../errorcode-ability.md#29600003-image-too-large) | Image too big. |

**Examples**

```TypeScript
import { common, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { fileIo } from '@kit.CoreFileKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG = '[ExamplePhotoEditorAbility]';

@Entry
@Component
struct Index {
  // Original image
  @State originalImage: PixelMap | null = null;

  build() {
    Row() {
      Column() {
        Button('RotateAndSaveImg').onClick(event => {
          hilog.info(0x0000, TAG, `Start to edit image and save.`);

          this.originalImage?.rotate(90).then(() => {
            const imagePackerApi: image.ImagePacker = image.createImagePacker();
            let packOpts: image.PackingOption = { format: 'image/jpeg', quality: 98 };
            imagePackerApi.packToData(this.originalImage, packOpts).then((data: ArrayBuffer) => {
              let context = this.getUIContext().getHostContext() as common.PhotoEditorExtensionContext;
              let filePath = context.filesDir + '/edited.jpg';
              let file: fileIo.File | undefined;
              try{
                file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE
                | fileIo.OpenMode.CREATE | fileIo.OpenMode.TRUNC);
                let writeLen = fileIo.writeSync(file.fd, data);
                hilog.info(0x0000, TAG, 'write data to file succeed and size is:'
                  + writeLen);
                fileIo.closeSync(file);
                context.saveEditedContentWithUri(filePath).then
                  (data => {
                    hilog.info(0x0000, TAG,
                      `saveContentEditingWithUri result: ${JSON.stringify(data)}`);
                  });
              } catch (e) {
                hilog.info(0x0000, TAG, `writeImage failed:${e}`);
              } finally {
                fileIo.close(file);
              }
            }).catch((error: BusinessError) => {
              hilog.error(0x0000, TAG,
                'Failed to pack the image. And the error is: ' + String(error));
            })
          })
        }).margin({ top: 10 })
      }
    }
  }
}
```
