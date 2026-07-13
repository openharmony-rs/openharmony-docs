# DocumentViewPicker

文件选择器对象，用来支撑选择和保存各种格式文档。在使用前，需要先创建DocumentViewPicker实例。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

## constructor

```TypeScript
constructor()
```

创建DocumentViewPicker对象，不推荐使用该构造函数，会出现概率性失败问题。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**示例：**

```TypeScript
let documentPicker = new picker.DocumentViewPicker(); // 不推荐使用无参构造，会出现概率性拉起失败问题

```

## constructor

```TypeScript
constructor(context: Context)
```

创建DocumentViewPicker对象，推荐使用该构造函数，获取context参考
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
            let documentPicker = new picker.DocumentViewPicker(context);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

## constructor

```TypeScript
constructor(context: Context, window: window.Window)
```

应用自行创建窗口中，可用通过该构造函数创建DocumentViewPicker对象。一般场景推荐使用constructor(context: Context)方法
创建DocumentViewPicker对象。

> **说明：**
>
> 从API version 19开始，2in1和Tablet设备支持该方法。

**起始版本：** 13

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文（仅支持UIAbilityContext）。Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-depr-i.md)。 |
| window | window.Window | 是 | 应用创建的窗口实例。 |

**示例：**

```TypeScript
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
import { window } from '@kit.ArkUI';
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
            let windowClass: window.Window | undefined = undefined;
            windowClass = window.findWindow('test'); // 请确保window已创建，此处的'test'为window创建时的name参数
            let documentPicker = new picker.DocumentViewPicker(context, windowClass);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

## getSelectedIndex

```TypeScript
getSelectedIndex(): number
```

获取保存成功后的文件后缀类型的下标。
该方法只在调用 [save()](arkts-corefile-documentviewpicker-c.md#save-1)时使用生效，
其他场景下不适用。该方法需要配置参数[DocumentSaveOptions.fileSuffixChoices](arkts-corefile-documentsaveoptions-c.md)。
该方法返回的是所选后缀类型的下标(number)。所选的后缀类型是开发者所传的参数
[DocumentSaveOptions.fileSuffixChoices](arkts-corefile-documentsaveoptions-c.md)里的某个后缀类型。
如果没有传参，并且调用了getSelectedIndex()方法，返回值为-1。

**起始版本：** 14

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService.FolderSelection

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回所选后缀类型在[DocumentSaveOptions.fileSuffixChoices](arkts-corefile-documentsaveoptions-c.md)里的下标(number)。默认返回-1。 |

## save

```TypeScript
save(option?: DocumentSaveOptions): Promise<Array<string>>
```

通过保存模式拉起documentPicker界面，用户可以保存一个或多个文件。使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | DocumentSaveOptions | 否 | documentPicker保存选项。若无此参数，则拉起documentPicker界面后需用户自行输入保存的文件名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象。返回documentPicker保存后的结果集。<br>**注意**：此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[文档类uri的使用方式](../../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example10(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let documentSaveOptions = new picker.DocumentSaveOptions();
    documentSaveOptions.newFileNames = ['DocumentViewPicker01.txt'];
    let documentPicker = new picker.DocumentViewPicker(context);
    documentPicker.save(documentSaveOptions).then((documentSaveResult: Array<string>) => {
      console.info('DocumentViewPicker.save successfully, documentSaveResult uri: ' + JSON.stringify(documentSaveResult));
    }).catch((err: BusinessError) => {
      console.error(`DocumentViewPicker.save failed with err, code is: ${err.code}, message is: ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`DocumentViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## save

```TypeScript
save(option: DocumentSaveOptions, callback: AsyncCallback<Array<string>>): void
```

通过保存模式拉起documentPicker界面，用户可以保存一个或多个文件。使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | DocumentSaveOptions | 是 | documentPicker保存选项。 |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | callback 返回documentPicker保存后的结果集。<br>**注意**：此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[文档类uri的使用方式](../../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example11(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let documentSaveOptions = new picker.DocumentSaveOptions();
    documentSaveOptions.newFileNames = ['DocumentViewPicker02.txt'];
    let documentPicker = new picker.DocumentViewPicker(context);
    documentPicker.save(documentSaveOptions, (err: BusinessError, documentSaveResult: Array<string>) => {
      if (err) {
        console.error(`DocumentViewPicker.save failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('DocumentViewPicker.save successfully, documentSaveResult uri: ' + JSON.stringify(documentSaveResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`DocumentViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## save

```TypeScript
save(callback: AsyncCallback<Array<string>>): void
```

通过保存模式拉起documentPicker界面，用户可以保存一个或多个文件。使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | callback 返回documentPicker保存后的结果集。<br>**注意**：此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[文档类uri的使用方式](../../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example12(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let documentPicker = new picker.DocumentViewPicker(context);
    documentPicker.save((err: BusinessError, documentSaveResult: Array<string>) => {
      if (err) {
        console.error(`DocumentViewPicker.save failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('DocumentViewPicker.save successfully, documentSaveResult uri: ' + JSON.stringify(documentSaveResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`DocumentViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## select

```TypeScript
select(option?: DocumentSelectOptions): Promise<Array<string>>
```

通过选择模式拉起documentPicker界面，用户可以选择一个或多个文件。使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | DocumentSelectOptions | 否 | documentPicker选择选项。若无此参数，则默认拉起documentPicker主界面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象。返回documentPicker选择后的结果集。<br>**注意**：此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[文档类uri的使用方式](../../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example07(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let documentSelectOptions = new picker.DocumentSelectOptions();
    let documentPicker = new picker.DocumentViewPicker(context);
    documentPicker.select(documentSelectOptions).then((documentSelectResult: Array<string>) => {
      console.info('DocumentViewPicker.select successfully, documentSelectResult uri: ' + JSON.stringify(documentSelectResult));
    }).catch((err: BusinessError) => {
      console.error(`DocumentViewPicker.select failed with err, code is: ${err.code}, message is: ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`DocumentViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## select

```TypeScript
select(option: DocumentSelectOptions, callback: AsyncCallback<Array<string>>): void
```

通过选择模式拉起documentPicker界面，用户可以选择一个或多个文件。使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | DocumentSelectOptions | 是 | documentPicker选择选项。 |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | callback 返回documentPicker选择后的结果集。<br>**注意**：此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[文档类uri的使用方式](../../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example08(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let documentSelectOptions = new picker.DocumentSelectOptions();
    let documentPicker = new picker.DocumentViewPicker(context);
    documentPicker.select(documentSelectOptions, (err: BusinessError, documentSelectResult: Array<string>) => {
      if (err) {
        console.error(`DocumentViewPicker.select failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('DocumentViewPicker.select successfully, documentSelectResult uri: ' + JSON.stringify(documentSelectResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`DocumentViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

## select

```TypeScript
select(callback: AsyncCallback<Array<string>>): void
```

通过选择模式拉起documentPicker界面，用户可以选择一个或多个文件。使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | callback 返回documentPicker选择后的结果集。<br>**注意**：此接口返回的URI数组的具体使用方式参见用户文件URI介绍中的[文档类uri的使用方式](../../../../file-management/user-file-uri-intro.md#文档类uri的使用方式)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example09(context: common.UIAbilityContext) { // 需确保 context 由 UIAbilityContext 转换而来
  try {
    let documentPicker = new picker.DocumentViewPicker(context);
    documentPicker.select((err: BusinessError, documentSelectResult: Array<string>) => {
      if (err) {
        console.error(`DocumentViewPicker.select failed with err, code is: ${err.code}, message is: ${err.message}`);
        return;
      }
      console.info('DocumentViewPicker.select successfully, documentSelectResult uri: ' + JSON.stringify(documentSelectResult));
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`DocumentViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}

```

