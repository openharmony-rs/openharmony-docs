# DocumentViewPicker

```TypeScript
class DocumentViewPicker
```

Provides APIs for selecting and saving documents in different formats. Before using the APIs of **DocumentViewPicker**, you need to create a **DocumentViewPicker** instance.

**Since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

## Modules to Import

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **DocumentViewPicker** instance. This constructor is not recommended due to the potential risk of operation failure.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

**Examples**

```TypeScript
let documentPicker = new picker.DocumentViewPicker(); // Construction without parameter is not recommended. There is a possibility that the DocumentViewPicker instance fails to start.
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(context: Context)
```

A constructor used to create a **DocumentViewPicker** instance. This constructor is recommended. For details about how to obtain the context, see [getHostContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#gethostcontext).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context (only **UIAbilityContext** is supported). For details about the application context of the stage model, see Context. |

**Examples**

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
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // Ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
            let documentPicker = new picker.DocumentViewPicker(context);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

<a id="constructor-2"></a>

## constructor

```TypeScript
constructor(context: Context, window: window.Window)
```

A constructor used to create a **DocumentViewPicker** object in a window created by an application. In other scenarios, you are advised to use **constructor(context: Context)** to create a **DocumentViewPicker** object.

> **NOTE:** 
> 
> This method is supported on 2-in-1 devices and tablets since API version 19.

**Since:** 13

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context (only **UIAbilityContext** is supported). For details about the application context of the stage model, see Context. |
| window | [window.Window](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md) | Yes | Window instance created by the application. |

**Examples**

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
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // Ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
            let windowClass: window.Window | undefined = undefined;
            windowClass = window.findWindow('test'); // Ensure that the window has been created. Here, 'test' is the value of the name parameter when the window is created.
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

Obtains the index of the file suffix type of the file saved. This method takes effect only when used with [save()](#save). This method can be used only after [DocumentSaveOptions.fileSuffixChoices](arkts-corefile-picker-documentsaveoptions-c.md) is configured. The index (number) returned by this method indicates the location of the file suffix specified in [DocumentSaveOptions.fileSuffixChoices](arkts-corefile-picker-documentsaveoptions-c.md). If no file suffix is specified, **getSelectedIndex()** returns **-1**.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.FileManagement.UserFileService.FolderSelection

**Return value:**

| Type | Description |
| --- | --- |
| number | Subscript (number) of the selected suffix type in [DocumentSaveOptions.fileSuffixChoices](arkts-corefile-picker-documentsaveoptions-c.md). The default value is **-1**. |

## save

```TypeScript
save(option?: DocumentSaveOptions): Promise<Array<string>>
```

Starts a **documentPicker** page for the user to save one or more documents. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [DocumentSaveOptions](arkts-corefile-picker-documentsaveoptions-c.md) | No | Options for saving the documents. If this parameter is not specified, a **documentPicker** page will be displayed for the user to enter the names of the documents to save. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the URIs of the documents saved. <br>**Note:**  For details about how to use the returned URIs, see [Using a Document URI](../../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example10(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

<a id="save-1"></a>

## save

```TypeScript
save(option: DocumentSaveOptions, callback: AsyncCallback<Array<string>>): void
```

Starts a **documentPicker** page for the user to save one or more documents. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [DocumentSaveOptions](arkts-corefile-picker-documentsaveoptions-c.md) | Yes | Options for saving the documents. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback invoked to return the URIs of the documents saved. <br>**Note:**  For details about how to use the returned URIs, see [Using a Document URI](../../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example11(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

<a id="save-2"></a>

## save

```TypeScript
save(callback: AsyncCallback<Array<string>>): void
```

Starts a **documentPicker** page for the user to save one or more documents. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback invoked to return the URIs of the documents saved. <br>**Note:**  For details about how to use the returned URIs, see [Using a Document URI](../../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example12(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

Starts a **documentPicker** page for the user to select one or more documents. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [DocumentSelectOptions](arkts-corefile-picker-documentselectoptions-c.md) | No | Options for selecting documents. If this parameter is not specified, the **documentPicker** page is displayed by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the URIs of the documents selected. <br> **Note:**  For details about how to use the returned URIs, see [Using a Document URI](../../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example07(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

<a id="select-1"></a>

## select

```TypeScript
select(option: DocumentSelectOptions, callback: AsyncCallback<Array<string>>): void
```

Starts a **documentPicker** page for the user to select one or more documents. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [DocumentSelectOptions](arkts-corefile-picker-documentselectoptions-c.md) | Yes | Options for selecting documents. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback invoked to return the URIs of the documents selected. <br>**Note:**  For details about how to use the returned URIs, see [Using a Document URI](../../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example08(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

<a id="select-2"></a>

## select

```TypeScript
select(callback: AsyncCallback<Array<string>>): void
```

Starts a **documentPicker** page for the user to select one or more documents. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback invoked to return the URIs of the documents selected. <br>**Note:**  For details about how to use the returned URIs, see [Using a Document URI](../../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example09(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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
