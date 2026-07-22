# PhotoViewPicker

图库选择器对象，用来支撑选择图片/视频和保存图片/视频等用户场景。选择文件推荐使用[PhotoAccessHelper的PhotoViewPicker](@ohos.file.photoAccessHelper:photoAccessHelper)。在使用前，需要先创建PhotoViewPicker实例。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** PhotoViewPicker

<!--Device-picker-class PhotoViewPicker--><!--Device-picker-class PhotoViewPicker-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

## 导入模块

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## constructor

```TypeScript
constructor()
```

**起始版本：** 12

**废弃版本：** 18

**替代接口：** PhotoViewPicker

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoViewPicker-constructor()--><!--Device-PhotoViewPicker-constructor()-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**示例：**

```TypeScript
let photoPicker = new picker.PhotoViewPicker(); // 不推荐使用无参构造，会出现概率性拉起失败问题

```

## constructor

```TypeScript
constructor(context: Context)
```

**起始版本：** 12

**废弃版本：** 18

**替代接口：** PhotoViewPicker

<!--Device-PhotoViewPicker-constructor(context: Context)--><!--Device-PhotoViewPicker-constructor(context: Context)-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文（仅支持UIAbilityContext）。Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-t.md)。 |

**示例：**

```TypeScript
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
@Entry
@Component
struct Index {
  @State message: string = 'hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // 请确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
            let photoPicker = new picker.PhotoViewPicker(context);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

## save

```TypeScript
save(option?: PhotoSaveOptions): Promise<Array<string>>
```

通过保存模式拉起photoPicker界面，用户可以保存一个或多个图片/视频。接口采用Promise异步返回形式，传入可选参数PhotoSaveOptions对象，返回保存文件的uri数组。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** SaveButton

<!--Device-PhotoViewPicker-save(option?: PhotoSaveOptions): Promise<Array<string>>--><!--Device-PhotoViewPicker-save(option?: PhotoSaveOptions): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [PhotoSaveOptions](arkts-corefile-picker-photosaveoptions-c.md) | 否 | photoPicker保存图片或视频文件选项。若无此参数，则拉起photoPicker界面后需用户自行输入保存的文件名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象。返回photoPicker保存图片或视频文件后的结果集。<br>**注意**：此接口会将文件保存在文件管理器，而不是图库。返回的uri数组的具体使用方式参见用户文件uri介绍中的[文档类uri的使用方式](../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example04(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let photoSaveOptions = new picker.PhotoSaveOptions();
    photoSaveOptions.newFileNames = ['PhotoViewPicker01.jpg', 'PhotoViewPicker01.mp4'];
    let photoPicker = new picker.PhotoViewPicker(context);
    photoPicker.save(photoSaveOptions).then((photoSaveResult: Array<string>) => {
      console.info('PhotoViewPicker.save successfully, photoSaveResult uri: ' + JSON.stringify(photoSaveResult));
    }).catch((err: BusinessError) => {
      console.error(`PhotoViewPicker.save failed with err, code is: ${err.code}, message is: ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## save

```TypeScript
save(option: PhotoSaveOptions, callback: AsyncCallback<Array<string>>): void
```

通过保存模式拉起photoPicker界面，用户可以保存一个或多个图片/视频。接口采用callback异步返回形式，传入参数PhotoSaveOptions对象，返回保存文件的uri数组。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** SaveButton

<!--Device-PhotoViewPicker-save(option: PhotoSaveOptions, callback: AsyncCallback<Array<string>>): void--><!--Device-PhotoViewPicker-save(option: PhotoSaveOptions, callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [PhotoSaveOptions](arkts-corefile-picker-photosaveoptions-c.md) | 是 | photoPicker保存图片或视频文件选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | callback 返回photoPicker保存图片或视频文件后的结果集。<br>**注意**：此接口会将文件保存在文件管理器，而不是图库。返回的uri数组的具体使用方式参见用户文件uri介绍中的[文档类uri的使用方式](../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example05(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let photoSaveOptions = new picker.PhotoSaveOptions();
    photoSaveOptions.newFileNames = ['PhotoViewPicker02.jpg', 'PhotoViewPicker02.mp4'];
    let photoPicker = new picker.PhotoViewPicker(context);
    photoPicker.save(photoSaveOptions, (err: BusinessError, photoSaveResult: Array<string>) => {
      if (err) {
        console.error(`PhotoViewPicker.save failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('PhotoViewPicker.save successfully, photoSaveResult uri: ' + JSON.stringify(photoSaveResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## save

```TypeScript
save(callback: AsyncCallback<Array<string>>): void
```

通过保存模式拉起photoPicker界面，用户可以保存一个或多个图片/视频。接口采用callback异步返回形式，返回保存文件的uri数组。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** SaveButton

<!--Device-PhotoViewPicker-save(callback: AsyncCallback<Array<string>>): void--><!--Device-PhotoViewPicker-save(callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | callback 返回photoPicker保存图片或视频文件后的结果集。<br>**注意**：此接口会将文件保存在文件管理器，而不是图库。返回的uri数组的具体使用方式参见用户文件uri介绍中的[文档类uri的使用方式](../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example06(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let photoPicker = new picker.PhotoViewPicker(context);
    photoPicker.save((err: BusinessError, photoSaveResult: Array<string>) => {
      if (err) {
        console.error(`PhotoViewPicker.save failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('PhotoViewPicker.save successfully, photoSaveResult uri: ' + JSON.stringify(photoSaveResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## select

```TypeScript
select(option?: PhotoSelectOptions): Promise<PhotoSelectResult>
```

通过选择模式拉起photoPicker界面，用户可以选择一个或多个图片/视频。接口采用Promise异步返回形式，传入可选参数PhotoSelectOptions对象，返回PhotoSelectResult对象。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** select(option?:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoViewPicker-select(option?: PhotoSelectOptions): Promise<PhotoSelectResult>--><!--Device-PhotoViewPicker-select(option?: PhotoSelectOptions): Promise<PhotoSelectResult>-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [PhotoSelectOptions](arkts-corefile-picker-photoselectoptions-c.md) | 否 | photoPicker选择选项。若无此参数，则默认选择媒体文件类型为图片和视频类型。选择媒体文件数量的默认最大值为50。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PhotoSelectResult&gt; | Promise对象。返回photoPicker选择后的结果集。<br>**注意**：此接口返回的PhotoSelectResult对象中的photoUris只能通过临时授权的方式调用接口[photoAccessHelper.getAssets](@ohos.file.photoAccessHelper:photoAccessHelper.PhotoAccessHelper.getAssets(options: FetchOptions, callback: AsyncCallback&lt;FetchResult<PhotoAsset>&gt;))去使用，具体使用方式参见用户文件URI介绍中的[媒体文件URI的使用方式](../../../file-management/user-file-uri-intro.md#媒体文件uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example01(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let photoSelectOptions = new picker.PhotoSelectOptions();
    photoSelectOptions.MIMEType = picker.PhotoViewMIMETypes.IMAGE_TYPE;
    photoSelectOptions.maxSelectNumber = 5;
    let photoPicker = new picker.PhotoViewPicker(context);
    photoPicker.select(photoSelectOptions).then((photoSelectResult: picker.PhotoSelectResult) => {
      console.info('PhotoViewPicker.select successfully, photoSelectResult uri: ' + JSON.stringify(photoSelectResult));
    }).catch((err: BusinessError) => {
      console.error(`PhotoViewPicker.select failed with err, code is: ${err.code}, message is: ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## select

```TypeScript
select(option: PhotoSelectOptions, callback: AsyncCallback<PhotoSelectResult>): void
```

通过选择模式拉起photoPicker界面，用户可以选择一个或多个图片/视频。接口采用callback异步返回形式，传入参数PhotoSelectOptions对象，返回PhotoSelectResult对象。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** select(option:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoViewPicker-select(option: PhotoSelectOptions, callback: AsyncCallback<PhotoSelectResult>): void--><!--Device-PhotoViewPicker-select(option: PhotoSelectOptions, callback: AsyncCallback<PhotoSelectResult>): void-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [PhotoSelectOptions](arkts-corefile-picker-photoselectoptions-c.md) | 是 | photoPicker选择选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;PhotoSelectResult&gt; | 是 | callback返回photoPicker选择后的结果集。<br>**注意**：此接口返回的PhotoSelectResult对象中的photoUris只能通过临时授权的方式调用接口[photoAccessHelper.getAssets](@ohos.file.photoAccessHelper:photoAccessHelper.PhotoAccessHelper.getAssets(options: FetchOptions, callback: AsyncCallback&lt;FetchResult<PhotoAsset>&gt;))去使用，具体使用方式参见用户文件URI介绍中的[媒体文件URI的使用方式](../../../file-management/user-file-uri-intro.md#媒体文件uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example02(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let photoSelectOptions = new picker.PhotoSelectOptions();
    photoSelectOptions.MIMEType = picker.PhotoViewMIMETypes.IMAGE_TYPE;
    photoSelectOptions.maxSelectNumber = 5;
    let photoPicker = new picker.PhotoViewPicker(context);
    photoPicker.select(photoSelectOptions, (err: BusinessError, photoSelectResult: picker.PhotoSelectResult) => {
      if (err) {
        console.error(`PhotoViewPicker.select failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('PhotoViewPicker.select successfully, photoSelectResult uri: ' + JSON.stringify(photoSelectResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## select

```TypeScript
select(callback: AsyncCallback<PhotoSelectResult>): void
```

通过选择模式拉起photoPicker界面，用户可以选择一个或多个图片/视频。接口采用callback异步返回形式，返回PhotoSelectResult对象。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** select(callback:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoViewPicker-select(callback: AsyncCallback<PhotoSelectResult>): void--><!--Device-PhotoViewPicker-select(callback: AsyncCallback<PhotoSelectResult>): void-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;PhotoSelectResult&gt; | 是 | callback返回photoPicker选择后的结果集。<br>**注意**：此接口返回的PhotoSelectResult对象中的photoUris只能通过临时授权的方式调用接口[photoAccessHelper.getAssets](@ohos.file.photoAccessHelper:photoAccessHelper.PhotoAccessHelper.getAssets(options: FetchOptions, callback: AsyncCallback&lt;FetchResult<PhotoAsset>&gt;))去使用，具体使用方式参见用户文件URI介绍中的[媒体文件URI的使用方式](../../../file-management/user-file-uri-intro.md#媒体文件uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example03(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let photoPicker = new picker.PhotoViewPicker(context);
    photoPicker.select((err: BusinessError, photoSelectResult: picker.PhotoSelectResult) => {
      if (err) {
        console.error(`PhotoViewPicker.select failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('PhotoViewPicker.select successfully, photoSelectResult uri: ' + JSON.stringify(photoSelectResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`PhotoViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

