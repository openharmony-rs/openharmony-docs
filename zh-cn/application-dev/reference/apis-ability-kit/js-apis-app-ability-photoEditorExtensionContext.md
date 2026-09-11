# PhotoEditorExtensionContext

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @liusu23-->
<!--Designer: @xukeke-->
<!--Tester: @lusq-->
<!--Adviser: @HelloCrease-->

PhotoEditorExtensionContext是PhotoEditorExtensionAbility的上下文，继承自ExtensionContext，提供PhotoEditorExtensionAbility的配置信息以及保存图片接口。
> **说明：**
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

传入编辑过的图片的沙箱路径以保存编辑后的图片。使用Promise异步回调。适用于将编辑后的图片已保存到沙箱路径的场景。此接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AppExtension.PhotoEditorExtension

**参数：**
| 参数名  | 类型  | 必填  | 说明  |
| ------------ | ------------ | ------------ | ------------ |
| uri | string  | 是  | 编辑后图片的沙箱路径。  |

**返回值：**
|  类型 | 说明  |
| ------------ | ------------ |
| Promise\<AbilityResult\> | Promise对象，返回AbilityResult对象，编辑后图片的uri存在want.uri中，[uri](../apis-core-file-kit/js-apis-file-fileuri.md)格式为file://\<bundleName>/\<sandboxPath>。  |

**错误码：**

以下错误码详细介绍参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

|  错误码ID | 错误信息  |
| ------------ | ------------ |
| 401  | Params error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.  |
| 29600001  | Internal error. |
| 29600002  | Image input error. |
| 29600003  | Image too big. |

**示例：**
```ts
import { common, Want } from '@kit.AbilityKit';
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
            imagePackerApi.packToData(this.originalImage, packOpts).then(async (data: ArrayBuffer) => {
              let context = this.getUIContext().getHostContext() as common.PhotoEditorExtensionContext;
              let filePath = context.filesDir + '/edited.jpg';
              let file: fileIo.File | undefined;
              try {
                file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE
                | fileIo.OpenMode.CREATE | fileIo.OpenMode.TRUNC);
                let writeLen = fileIo.writeSync(file.fd, data);
                hilog.info(0x0000, TAG, 'write data to file succeed and size is:'
                  + writeLen);
                let result = await context.saveEditedContentWithUri(filePath);
                hilog.info(0x0000, TAG,
                  `saveContentEditingWithUri result: ${JSON.stringify(result)}`);
              } catch (err) {
                hilog.error(0x0000, TAG, `writeImage failed:${err}`);
              } finally {
                fileIo.closeSync(file);
              }
            }).catch((error: BusinessError) => {
              hilog.error(0x0000, TAG,
                `Failed to pack the image. Code: ${error.code}, message: ${error.message}`);
            });
          })
        }).margin({ top: 10 })
      }
    }
  }
}
```
## PhotoEditorExtensionContext.saveEditedContentWithImage

saveEditedContentWithImage(pixelMap: image.PixelMap, option: image.PackingOption): Promise\<AbilityResult\>

传入编辑过的图片的PixelMap对象以保存编辑后的图片。使用Promise异步回调。适用于立即保存PixelMap对象的场景。此接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AppExtension.PhotoEditorExtension

**参数：**
| 参数名  | 类型  | 必填  | 说明  |
| ------------ | ------------ | ------------ | ------------ |
| pixelMap | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)  | 是  | 编辑过的图片image.PixelMap。  |
| option  | [image.PackingOption](../apis-image-kit/arkts-apis-image-i.md#packingoption)  |  是 | 设置图片打包参数，包含format（图片格式）和quality（图片质量）等配置项。  |

**返回值：**
|  类型 | 说明  |
| ------------ | ------------ |
| Promise\<AbilityResult\> | Promise对象，返回AbilityResult对象，编辑后图片的uri存在want.uri中，[uri](../apis-core-file-kit/js-apis-file-fileuri.md)格式为file://\<bundleName>/\<sandboxPath>。  |

**错误码：**

以下错误码详细介绍参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

|  错误码ID | 错误信息  |
| ------------ | ------------ |
| 401  | Params error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types.  |
| 29600001  | Internal error. |
| 29600002  | Image input error. |
| 29600003  | Image too big. |

**示例：**
```ts
import { common, Want } from '@kit.AbilityKit';
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
                }).catch((error: BusinessError) => {
                  hilog.error(0x0000, TAG, `saveEditedContentWithImage failed: ${error.message}`);
                });
            } catch (e) {
              hilog.error(0x0000, TAG, `saveEditedContentWithImage failed:${e}`);
              return;
            }
          }).catch((error: BusinessError) => {
            hilog.error(0x0000, TAG, `rotate failed: ${error.message}`);
          });
        }).margin({ top: 10 })
      }
    }
  }
}
```