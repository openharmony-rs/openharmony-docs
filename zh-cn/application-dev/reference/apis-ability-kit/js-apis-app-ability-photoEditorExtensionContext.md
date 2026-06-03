# PhotoEditorExtensionContext

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @liusu23-->
<!--Designer: @xukeke-->
<!--Tester: @lusq-->
<!--Adviser: @HelloCrease-->

PhotoEditorExtensionContext是PhotoEditorExtensionAbility的上下文，继承自ExtensionContext，提供PhotoEditorExtensionAbility的相关配置信息以及保存图片接口。
> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。
>
> 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

## 导入模块
```ts
import { common } from '@kit.AbilityKit';
```

## PhotoEditorExtensionContext.saveEditedContentWithUri

saveEditedContentWithUri(uri: string): Promise\<AbilityResult\>

传入编辑过的图片的uri并保存。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AppExtension.PhotoEditorExtension

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**
| 参数名  | 类型  | 必填  | 说明  |
| ------------ | ------------ | ------------ | ------------ |
| uri | string  | 是  | 编辑后图片的[uri](../apis-core-file-kit/js-apis-file-fileuri.md)，格式为file://\<bundleName>/\<sandboxPath>。  |

**返回值：**
|  类型 | 说明  |
| ------------ | ------------ |
| Promise\<AbilityResult\> | Promise对象，返回AbilityResult对象，编辑过的图片uri存在want.uri中，[uri](../apis-core-file-kit/js-apis-file-fileuri.md)格式为file://\<bundleName>/\<sandboxPath>。  |

**错误码：**

以下错误码详细介绍参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

|  错误码ID | 错误信息  |
| ------------ | ------------ |
| 401  | Params error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.  |
| 29600001  | Internal error. |
| 29600002  |  Image input error. |
| 29600003  |  Image too big. |

**示例：**

ArkTS-Dyn示例：

```ts
import { common, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { fileIo } from '@kit.CoreFileKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG = '[ExamplePhotoEditorAbility]';

@Entry
@Component
struct Index {
  // 原始图片
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
ArkTS-Sta示例：

```ts
import { common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { fileIo } from '@kit.CoreFileKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Entry, Component, State, Row, Column, Button, PixelMap } from '@kit.ArkUI';

const TAG = '[ExamplePhotoEditorAbility]';

@Entry
@Component
struct Index {
  @State originalImage: PixelMap | null = null;

  build() {
    Row() {
      Column() {
        Button('RotateAndSaveImg').onClick(() => {
          if (!this.originalImage) {
            hilog.error(0x0000, TAG, `Original image is null.`);
            return;
          }
          hilog.info(0x0000, TAG, `Start to edit image and save.`);
          this.myFun();
        }).margin({ top: 10 })
      }
    }
  }

  private async myFun(): Promise<void> { // 显式声明返回类型
    const sourceImage = this.originalImage;
    if (!sourceImage) {
      hilog.warn(0x0000, TAG, `Source image is invalid during execution.`);
      return; // 显式返回
    }

    try {

      sourceImage.rotate(90);

      const imageToPack: PixelMap = sourceImage;

      const imagePackerApi: image.ImagePacker = image.createImagePacker();
      const packOpts: image.PackingOption = { format: 'image/jpeg', quality: 98 };

      const data: ArrayBuffer = await imagePackerApi.packToData(imageToPack, packOpts);
      hilog.info(0x0000, TAG, `Image packed successfully, size: ${data.byteLength}`);

      const context = this.getUIContext().getHostContext() as common.PhotoEditorExtensionContext;
      const fileName = 'edited.jpg';
      const filePath = context.filesDir + '/' + fileName;
      const fileUri = `file://${filePath}`;

      let file: fileIo.File | undefined = undefined;

      try {
        file = fileIo.openSync(filePath,
          fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE | fileIo.OpenMode.TRUNC);

        const writeLen = fileIo.writeSync(file.fd, data);
        hilog.info(0x0000, TAG, `Write data to file succeed, size: ${writeLen}`);

        fileIo.closeSync(file);
        file = undefined;

        await context.saveEditedContentWithUri(fileUri);
        hilog.info(0x0000, TAG, `Save edited content success.`);

        return; // 显式返回成功路径

      } catch (ioErr) {
        hilog.error(0x0000, TAG, `File IO failed: ${JSON.stringify(ioErr)}`);
        throw ioErr;
      } finally {
        if (file) {
          try {
            fileIo.closeSync(file);
          } catch (e) {
            hilog.error(0x0000, TAG, `Process failed: ${JSON.stringify(e)}`);
          }
        }
      }
    } catch (error) {
      hilog.error(0x0000, TAG, `Process failed: ${JSON.stringify(error)}`);
      return; // 显式返回错误路径
    }

    return; // 显式返回函数末尾
  }
}
```

## PhotoEditorExtensionContext.saveEditedContentWithImage

saveEditedContentWithImage(pixeMap: image.PixelMap, option: image.PackingOption): Promise\<AbilityResult\>

传入编辑过的图片的PixelMap对象并保存。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AppExtension.PhotoEditorExtension

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**
| 参数名  | 类型  | 必填  | 说明  |
| ------------ | ------------ | ------------ | ------------ |
| pixeMap | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)  | 是  | 编辑过的图片image.PixelMap。  |
| option  | [image.PackingOption](..//apis-image-kit/arkts-apis-image-i.md#packingoption)  |  是 | 设置打包参数。  |

**返回值：**
|  类型 | 说明  |
| ------------ | ------------ |
| Promise\<AbilityResult\> | Promise对象，返回AbilityResult对象，编辑过的图片uri存在want.uri中，[uri](../apis-core-file-kit/js-apis-file-fileuri.md)格式为file://\<bundleName>/\<sandboxPath>。  |

**错误码：**

以下错误码详细介绍参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

|  错误码ID | 错误信息  |
| ------------ | ------------ |
| 401  | Params error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.  |
| 29600001  | Internal error. |
| 29600002  |  Image input error. |
| 29600003  |  Image too big. |

**示例：**

ArkTS-Dyn示例：

```ts
import { common, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { image } from '@kit.ImageKit';

const TAG = '[ExamplePhotoEditorAbility]';

@Entry
@Component
struct Index {
  // 原始图片
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

ArkTS-Sta示例：

```ts
import { common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { fileIo } from '@kit.CoreFileKit';
import { image } from '@kit.ImageKit';
import { Entry, Component, State, Row, Column, Button, PixelMap } from '@kit.ArkUI';

const TAG = '[ExamplePhotoEditorAbility]';

@Entry
@Component
struct Index {
  @State originalImage: PixelMap | null = null;

  build() {
    Row() {
      Column() {
        Button('RotateAndSaveImg').onClick(() => {
          hilog.info(0x0000, TAG, `Start to edit image and save.`);
          this.handleRotateAndSave();
        }).margin({ top: 10 })
      }
    }
  }

  private async handleRotateAndSave(): Promise<void> {
    const sourceImage = this.originalImage;
    if (!sourceImage) {
      hilog.error(0x0000, TAG, `Original image is null.`);
      return;
    }

    try {
      sourceImage.rotate(90);
      hilog.info(0x0000, TAG, `Image rotated successfully (in-place).`);

      const packOpts: image.PackingOption = { format: 'image/jpeg', quality: 98 };

      const context = this.getUIContext().getHostContext() as common.PhotoEditorExtensionContext;


      try {
        await context.saveEditedContentWithImage(sourceImage, packOpts);
        hilog.info(0x0000, TAG, `Save edited content success via API.`);
        return; // 成功则直接返回
      } catch (apiErr) {
        hilog.warn(0x0000, TAG, `API save failed, falling back to manual save: ${JSON.stringify(apiErr)}`);
        // 如果 API 调用失败（例如签名不匹配），执行手动打包保存逻辑
        await this.manualSaveImage(sourceImage, packOpts, context);
      }

    } catch (error) {
      hilog.error(0x0000, TAG, `Process failed: ${JSON.stringify(error)}`);
    }

    return;
  }

  private async manualSaveImage(imageToSave: PixelMap, packOpts: image.PackingOption,
    context: common.PhotoEditorExtensionContext): Promise<void> {
    const imagePackerApi: image.ImagePacker = image.createImagePacker();

    // 打包数据
    const data: ArrayBuffer = await imagePackerApi.packToData(imageToSave, packOpts);
    hilog.info(0x0000, TAG, `Image packed manually, size: ${data.byteLength}`);

    const fileName = 'edited_manual.jpg';
    const filePath = context.filesDir + '/' + fileName;
    const fileUri = `file://${filePath}`;

    let file: fileIo.File | undefined = undefined;
    try {
      file = fileIo.openSync(filePath,
        fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE | fileIo.OpenMode.TRUNC);
      fileIo.writeSync(file.fd, data);
      fileIo.closeSync(file);
      file = undefined;

      await context.saveEditedContentWithUri(fileUri);
      hilog.info(0x0000, TAG, `Manual save success.`);
    } catch (ioErr) {
      hilog.error(0x0000, TAG, `Manual save IO failed: ${JSON.stringify(ioErr)}`);
      if (file) {
        try {
          fileIo.closeSync(file);
        } catch (e) {
        }
      }
      throw ioErr;
    }
  }
}
```
