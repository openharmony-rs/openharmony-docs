# AudioViewPicker

音频选择器对象，用来支撑选择和保存音频类文件等用户场景。在使用前，需要先创建AudioViewPicker实例。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

## constructor

```TypeScript
constructor()
```

创建AudioViewPicker对象，不推荐使用该构造函数，会出现概率性失败问题。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**示例：**

```TypeScript
let audioPicker = new picker.AudioViewPicker(); // 不推荐使用无参构造，会出现概率性拉起失败问题

```

## constructor

```TypeScript
constructor(context: Context)
```

创建AudioViewPicker对象，推荐使用该构造函数，获取context参考
[getHostContext](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#gethostcontext12)。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文（仅支持UIAbilityContext）。Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-depr-i.md)。 |

**示例：**

```TypeScript
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
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
          .onClick(()=>{
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // 请确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
            let audioPicker = new picker.AudioViewPicker(context);
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
save(option?: AudioSaveOptions): Promise<Array<string>>
```

通过保存模式拉起audioPicker界面（目前拉起的是documentPicker，audioPicker在规划中），
用户可以保存一个或多个音频文件。使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | AudioSaveOptions | 否 | audioPicker保存音频文件选项。若无此参数，则拉起audioPicker界面后需用户自行输入保存的文件名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象。返回audioPicker保存音频文件后的结果集。<br>**注意**： 此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[文档类uri的使用方式](../../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example16(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let audioSaveOptions = new picker.AudioSaveOptions();
    audioSaveOptions.newFileNames = ['AudioViewPicker01.mp3'];
    let audioPicker = new picker.AudioViewPicker(context);
    audioPicker.save(audioSaveOptions).then((audioSaveResult: Array<string>) => {
      console.info('AudioViewPicker.save successfully, audioSaveResult uri: ' + JSON.stringify(audioSaveResult))
    }).catch((err: BusinessError) => {
      console.error(`AudioViewPicker.save failed with err, code is: ${err.code}, message is: ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`AudioViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## save

```TypeScript
save(option: AudioSaveOptions, callback: AsyncCallback<Array<string>>): void
```

通过保存模式拉起audioPicker界面（目前拉起的是documentPicker，audioPicker在规划中），
用户可以保存一个或多个音频文件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | AudioSaveOptions | 是 | audioPicker保存音频文件选项。 |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | callback 返回audioPicker保存音频文件后的结果集。<br>**注意**： 此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[文档类uri的使用方式](../../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example17(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let audioSaveOptions = new picker.AudioSaveOptions();
    audioSaveOptions.newFileNames = ['AudioViewPicker02.mp3'];
    let audioPicker = new picker.AudioViewPicker(context);
    audioPicker.save(audioSaveOptions, (err: BusinessError, audioSaveResult: Array<string>) => {
      if (err) {
        console.error(`AudioViewPicker.save failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('AudioViewPicker.save successfully, audioSaveResult uri: ' + JSON.stringify(audioSaveResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`AudioViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## save

```TypeScript
save(callback: AsyncCallback<Array<string>>): void
```

通过保存模式拉起audioPicker界面（目前拉起的是documentPicker，audioPicker在规划中），
用户可以保存一个或多个音频文件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | callback 返回audioPicker保存音频文件后的结果集。<br>**注意**： 此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[文档类uri的使用方式](../../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example18(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let audioPicker = new picker.AudioViewPicker(context);
    audioPicker.save((err: BusinessError, audioSaveResult: Array<string>) => {
      if (err) {
        console.error(`AudioViewPicker.save failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('AudioViewPicker.save successfully, audioSaveResult uri: ' + JSON.stringify(audioSaveResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
        console.error(`AudioViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## select

```TypeScript
select(option?: AudioSelectOptions): Promise<Array<string>>
```

通过选择模式拉起audioPicker界面，用户可以选择一个或多个音频文件。使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | AudioSelectOptions | 否 | audioPicker音频选择选项。若无此参数，则默认拉起audioPicker主界面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象。返回audioPicker选择音频后的结果集。<br>**注意**： 此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[媒体类uri的使用方式](../../../../file-management/user-file-uri-intro.md#媒体文件uri介绍)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example13(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let audioSelectOptions = new picker.AudioSelectOptions();
    let audioPicker = new picker.AudioViewPicker(context);
    audioPicker.select(audioSelectOptions).then((audioSelectResult: Array<string>) => {
      console.info('AudioViewPicker.select successfully, audioSelectResult uri: ' + JSON.stringify(audioSelectResult));
    }).catch((err: BusinessError) => {
      console.error(`AudioViewPicker.select failed with err, code is: ${err.code}, message is: ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`AudioViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## select

```TypeScript
select(option: AudioSelectOptions, callback: AsyncCallback<Array<string>>): void
```

通过选择模式拉起audioPicker界面，用户可以选择一个或多个音频文件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | AudioSelectOptions | 是 | audioPicker音频选择选项。 |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | callback 返回audioPicker选择音频后的结果集。<br>**注意**： 此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[媒体类uri的使用方式](../../../../file-management/user-file-uri-intro.md#媒体文件uri介绍)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example14(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let audioSelectOptions = new picker.AudioSelectOptions();
    let audioPicker = new picker.AudioViewPicker(context);
    audioPicker.select(audioSelectOptions, (err: BusinessError, audioSelectResult: Array<string>) => {
      if (err) {
        console.error(`AudioViewPicker.select failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('AudioViewPicker.select successfully, audioSelectResult uri: ' + JSON.stringify(audioSelectResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`AudioViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## select

```TypeScript
select(callback: AsyncCallback<Array<string>>): void
```

通过选择模式拉起audioPicker界面，用户可以选择一个或多个音频文件。使用callback异步回调。
**系统能力**：SystemCapability.FileManagement.UserFileService

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | callback 返回audioPicker选择音频后的结果集。<br>**注意**： 此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[媒体类uri的使用方式](../../../../file-management/user-file-uri-intro.md#媒体文件uri介绍)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example15(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let audioPicker = new picker.AudioViewPicker(context);
    audioPicker.select((err: BusinessError, audioSelectResult: Array<string>) => {
      if (err) {
        console.error(`AudioViewPicker.select failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('AudioViewPicker.select successfully, audioSelectResult uri: ' + JSON.stringify(audioSelectResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`AudioViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

