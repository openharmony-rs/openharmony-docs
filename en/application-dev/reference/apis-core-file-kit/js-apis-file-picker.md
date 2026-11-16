# @ohos.file.picker (Picker)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang; @Dyylll-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=95dcc4309adc65b71e9913aa46db4e1af68b5ef1 translatedAt=2026-11-03T04:38:51.629Z pushedAt=2026-11-04T03:11:33.535Z nl=1 -->

The **Picker** module encapsulates APIs such as **DocumentViewPicker**, **AudioViewPicker**, and **PhotoViewPicker** to provide capabilities of selecting and saving files of different types. The **Picker** module can be used to start the system file selection page, where users can select or save files in a secure and controllable environment. Apps can use this module without requesting any permissions. An application can select the API as required. The APIs of this module must be called in UIAbility. Otherwise, the **FilePicker**, **AudioPicker**, or **PhotoPicker** cannot be started.

Chinese characters and non-digit characters in the URI are compiled into the corresponding ASCII code and concatenated to the URI returned by calling these APIs.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { picker } from '@kit.CoreFileKit';
```

## DocumentViewPicker

Provides APIs for selecting and saving documents in different formats. Before using the APIs of **DocumentViewPicker**, you need to create a **DocumentViewPicker** instance.

**System capability**: SystemCapability.FileManagement.UserFileService

### constructor<sup>12+</sup>

constructor(context: Context)

A constructor used to create a **DocumentViewPicker** instance. This constructor is recommended. For details about how to obtain the context, see [getHostContext](../apis-arkui/arkts-apis-uicontext-uicontext.md#gethostcontext12).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name | Type    | Mandatory | Description                                                         |
| --------- | ------- | --------- | ------------------------------------------------------------ |
| context | Context| Yes   | Application context (only **UIAbilityContext** is supported). For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |

**Example**

```ts
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

### constructor<sup>12+</sup>

constructor()

A constructor used to create a **DocumentViewPicker** instance. This constructor is not recommended due to the potential risk of operation failure.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Example**

```ts
let documentPicker = new picker.DocumentViewPicker(); // Not recommended to use the parameterless constructor, as it may cause probabilistic launch failures.
```

### constructor<sup>13+</sup>

constructor(context: Context, window: window.Window)

When a window is created by an app, a constructor is used to create a **DocumentViewPicker** object. In other scenarios, you are advised to use **constructor(context: Context)** to create a **DocumentViewPicker** object.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes | Application context (only **UIAbilityContext** is supported). For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| window | [window.Window](../apis-arkui/arkts-apis-window-Window.md) | Yes | Window instance created by the app. |

**Example**

```ts
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
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // Ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
            let windowClass: window.Window | undefined = undefined;
            windowClass = window.findWindow('test'); // Ensure that the window has been created. Here 'test' is the name parameter used when creating the window.
            let documentPicker = new picker.DocumentViewPicker(context, windowClass);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### select

select(option?: DocumentSelectOptions): Promise&lt;Array&lt;string&gt;&gt;

Starts a **documentPicker** page for the user to select one or more documents. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| option | [DocumentSelectOptions](#documentselectoptions) | No   | Selection option of documentPicker, used for configuration of file selection parameters (such as the maximum number of files to select, file extension filtering, etc.). If this parameter is absent, the documentPicker main interface is launched by default. |

**Return value**

| Type                            | Description    |
| ----------------------------- | :---- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the result set after documentPicker selection.<br> **Note:** For details about how to use the returned URI array, see [Using a Document URI](../../file-management/user-file-uri-intro.md#using-a-document-uri).  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example07(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext
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

### select

select(option: DocumentSelectOptions, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Starts a **documentPicker** page for the user to select one or more documents. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------- | ---- | -------------------------- |
| option | [DocumentSelectOptions](#documentselectoptions) | Yes | DocumentPicker selection option, used for configuring file selection parameters (such as the maximum number of files to select, file extension filtering, etc.). |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes | Callback returns the result set after documentPicker selection.<br>**Note**: For the specific usage of the URI array returned by this interface, see [Document URI Usage](../../file-management/user-file-uri-intro.md#using-a-document-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example08(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext
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

### select

select(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Starts a **documentPicker** page for the user to select one or more documents. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt;      | Yes   | Callback returns the result set selected by documentPicker.<br>**Note**: For the specific usage of the URI array returned by this interface, see [Usage of Document URIs](../../file-management/user-file-uri-intro.md#using-a-document-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
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

### save

save(option?: DocumentSaveOptions): Promise&lt;Array&lt;string&gt;&gt;

Starts a **documentPicker** page for the user to save one or more documents. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| option | [DocumentSaveOptions](#documentsaveoptions) | No   | Save options of the documentPicker, used to configure the parameters for saving files (such as the file name, default save path, and file extension). If this parameter is absent, after the documentPicker interface is launched, the user needs to enter the file name to save. |

**Return value**

| Type                            | Description    |
| ----------------------------- | :---- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the result set after the documentPicker saves. If the call fails, **reject** throws **BusinessError**.<br>**Note:** For details about how to use the returned URI array, see [Using a Document URI](../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example10(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext
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

### save

save(option: DocumentSaveOptions, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Starts a **documentPicker** page for the user to save one or more documents. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------- | ---- | -------------------------- |
| option | [DocumentSaveOptions](#documentsaveoptions) | Yes | Save options of documentPicker, used for configuring file saving parameters (such as the saved file name, default save path, file extension, etc.). |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes | Callback returns the result set after documentPicker saves.<br>**Note**: For the specific usage of the URI array returned by this interface, see [Usage of Document URIs](../../file-management/user-file-uri-intro.md#using-a-document-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
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

### save

save(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Starts a **documentPicker** page for the user to save one or more documents. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt;      | Yes   | Callback returns the result set after documentPicker saves.<br>**Note**: For the specific usage of the URI array returned by this interface, see [Usage of Document URIs](../../file-management/user-file-uri-intro.md#using-a-document-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
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

### getSelectedIndex<sup>14+</sup>

getSelectedIndex(): number

Obtains the index of the file suffix type of the file saved.

This method takes effect only when used with [save](#save).

This method can be used only after [DocumentSaveOptions.fileSuffixChoices](#documentsaveoptions) is configured.

The index (number) returned by this method indicates the location of the file suffix specified in [DocumentSaveOptions.fileSuffixChoices](#documentsaveoptions). If no file suffix is specified, **getSelectedIndex()** returns **-1**. Before using the return value as the array index, check whether the return value is greater than or equal to 0 to avoid out-of-bounds array access.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.FileManagement.UserFileService.FolderSelection

**Return value**

| Type                            | Description    |
| ----------------------------- | :---- |
| number| Returns the subscript (number) of the selected extension type in [DocumentSaveOptions.fileSuffixChoices](#documentsaveoptions). The default value is **-1**. |

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function exampleIndex(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
  try {
    let documentSaveOptions = new picker.DocumentSaveOptions();
    // Name of the file to save.
    documentSaveOptions.newFileNames = ['DocumentViewPicker01'];
    // Extension type of the file to save.
    documentSaveOptions.fileSuffixChoices = ['txt', 'mp4', 'pdf'];
    let documentPicker = new picker.DocumentViewPicker(context);
    documentPicker.save(documentSaveOptions).then((documentSaveResult: Array<string>) => {
      if (documentSaveOptions.fileSuffixChoices != undefined && documentSaveResult != undefined) {
        // Obtain the subscript of the extension type of the file to save.
        let index = documentPicker.getSelectedIndex();
        // Obtain the extension type of the file to save.
        let selectedSuffix = documentSaveOptions.fileSuffixChoices[index];
        console.info('DocumentViewPicker.save selectedSuffix is ' + selectedSuffix);
      }
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

## AudioViewPicker

Provides APIs for selecting and saving audio clips. Before using the APIs of **AudioViewPicker**, you need to create an **AudioViewPicker** instance.

**System capability**: SystemCapability.FileManagement.UserFileService

### constructor<sup>12+</sup>

constructor(context: Context)

A constructor used to create an **AudioViewPicker** instance. This constructor is recommended. For details about how to obtain the context, see [getHostContext](../apis-arkui/arkts-apis-uicontext-uicontext.md#gethostcontext12).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name    | Type    | Mandatory | Description                                                         |
| ------- | ------- | --------- | ------------------------------------------------------------ |
| context | Context | Yes       | Application context (only **UIAbilityContext** is supported). For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |

**Example**

```ts
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
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // Ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
            let audioPicker = new picker.AudioViewPicker(context);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### constructor<sup>12+</sup>

constructor()

A constructor used to create an **AudioViewPicker** instance. This constructor is not recommended due to the potential risk of operation failure.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Example**

```ts
let audioPicker = new picker.AudioViewPicker(); // Not recommended to use the parameterless constructor, as it may cause probabilistic launch failure
```

### select

select(option?: AudioSelectOptions): Promise&lt;Array&lt;string&gt;&gt;

Starts an **audioPicker** page for the user to select one or more audio clips. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| option | [AudioSelectOptions](#audioselectoptions) | No   | Audio selection option of the audioPicker, used for configuration of audio file selection parameters (such as the maximum number of files to select). If this parameter is absent, the audioPicker main interface is launched by default. |

**Return value**

| Type                            | Description    |
| ----------------------------- | :---- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the URIs of the audio clips selected. If the call fails, **reject** throws **BusinessError**. <br>**Note:** For details about how to use the returned URIs, see [Using a Media File URI](../../file-management/user-file-uri-intro.md#using-a-media-file-uri). |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example13(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

### select

select(option: AudioSelectOptions, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Starts an **audioPicker** page for the user to select one or more audio clips. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| option | [AudioSelectOptions](#audioselectoptions) | Yes   | Audio selection option of audioPicker, used for configuration of audio file selection parameters (such as the maximum number of files to select). |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt;      | Yes   | callback returns the result set after audioPicker selects audio. <br>**Note**: For the specific usage of the URI array returned by this interface, see [Usage of Media File URI](../../file-management/user-file-uri-intro.md#using-a-media-file-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example14(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

### select

select(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Starts an **audioPicker** page for the user to select one or more audio clips. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt;      | Yes   | Callback used to return the result set after audioPicker selects audio. <br>**Note**: For the specific usage of the URI array returned by this interface, see [Usage of Media File URIs](../../file-management/user-file-uri-intro.md#using-a-media-file-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example15(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

### save

save(option?: AudioSaveOptions): Promise&lt;Array&lt;string&gt;&gt;

Starts an **audioPicker** page (currently, a **documentPicker** page is displayed) for the user to save one or more audio clips. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| option | [AudioSaveOptions](#audiosaveoptions) | No   | Options for the audioPicker to save audio files. If this parameter is absent, after the audioPicker interface is launched, the user needs to enter the file name to save. |

**Return value**

| Type                            | Description    |
| ----------------------------- | :---- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the result set after the audioPicker saves the audio files. If the operation fails, an error message is thrown through reject with a BusinessError object. <br>**Note:** For details about how to use the returned URIs, see [Using a Document URI](../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example16(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
  try {
    let audioSaveOptions = new picker.AudioSaveOptions();
    audioSaveOptions.newFileNames = ['AudioViewPicker01.mp3'];
    let audioPicker = new picker.AudioViewPicker(context);
    audioPicker.save(audioSaveOptions).then((audioSaveResult: Array<string>) => {
      console.info('AudioViewPicker.save successfully, audioSaveResult uri: ' + JSON.stringify(audioSaveResult));
    }).catch((err: BusinessError) => {
      console.error(`AudioViewPicker.save failed with err, code is: ${err.code}, message is: ${err.message}`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`AudioViewPicker failed with err, code is: ${err.code}, message is: ${err.message}`);
  }
}
```

### save

save(option: AudioSaveOptions, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Starts an **audioPicker** page (currently, a **documentPicker** page is displayed) for the user to save one or more audio clips. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| option | [AudioSaveOptions](#audiosaveoptions) | Yes   | Audio saving options for audioPicker, used for configuration of audio file saving parameters (such as the saved file name). |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt;      | Yes   | Callback returns the result set after audioPicker saves the audio file. <br>**Note**: For the specific usage of the URI array returned by this interface, see [Usage of document URIs](../../file-management/user-file-uri-intro.md#using-a-document-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example17(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

### save

save(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Starts an **audioPicker** page (currently, a **documentPicker** page is displayed) for the user to save one or more audio clips. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt;      | Yes   | Callback returns the result set after audioPicker saves the audio file. <br>**Note**: For the specific usage of the URI array returned by this interface, see [Usage of document URIs](../../file-management/user-file-uri-intro.md#using-a-document-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example18(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext
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

## DocumentSelectMode<sup>11+</sup>

Enumerates the types of documents selected.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService.FolderSelection

| Name  |  Value |  Description |
| ----- |  ---- | ---- |
| FILE  | 0  | File type (default type). |
| FOLDER | 1  | Folder type.  |
| MIXED | 2  | Mixed type of files and folders.<br>**Device behavior differences**: This parameter can be used on 2-in-1 devices but has no effect on other devices.|

## DocumentSelectOptions

Defines the options for selecting documents.

| Name                    | Type                                          | Read-Only | Optional | Description                                       |
| :---------------------- |---------------------------------------------| ---- | ---- | ------------------------------------------|
| maxSelectNumber<sup>10+</sup>       | number                                      | No   | Yes | Maximum number of files that can be selected.<br>In API version 20 and earlier, the maximum number of files that can be selected at a time is 500, and the default value is also 500. The directory selection function is available only on devices with this system capability, and at most one directory can be selected at a time.<br>In API version 21 and later, the limit on the number of files that can be selected is removed. Due to system capability limitations, selecting too many files may cause functional exceptions or poor processing performance. It is recommended that the number of files selected at a time not exceed 10,000.<br>In API version 23 and later, the limit on the number of directories that can be selected is removed.<br>**Device behavior differences**: This parameter does not support selecting multiple directories on smartphones.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.FileManagement.UserFileService   |
| defaultFilePathUri<sup>10+</sup>    | string                                      | No   |  Yes | URI of the selected file or directory. The default value is empty (the recently visited page is displayed). To improve user experience, FilePicker remembers the last location navigated to by the user and prefers this path as the start path, instead of always using the path specified by **defaultFilePathUri**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.FileManagement.UserFileService          |
| fileSuffixFilters<sup>10+</sup>     | Array&lt;string&gt;                         | No   |  Yes | File extension types of the files to be selected. Pass in a string array, where each item represents one extension option. Each item is internally divided into two parts by "\|\": the first part is the description, and the second part is the filtering extension. If there is no "\|\", there is no description, and the entire item is a filtering extension. Each filtering extension can contain multiple extension names, and each extension name is separated by an English comma. The length of the passed-in array cannot exceed 100. For example: ['Image(.png, .jpg)\|\.png,.jpg', 'Document \|\.txt', 'Video \|\.mp4', '.pdf'].<br>By default, no filtering is performed, that is, all files are displayed. In addition, 2-in-1 devices support the wildcard mode ['All files (\*.\*)\|\.*'] (Note: Since API version 17, smartphones support this configuration), which means all files are displayed.<br>This parameter is available only on devices with this system capability.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.FileManagement.UserFileService   |
| selectMode<sup>11+</sup>         | [DocumentSelectMode](#documentselectmode11) | No   |  Yes | Document type selected by Picker. The default value is **FILE** (file type).<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.FileManagement.UserFileService.FolderSelection  |
| authMode<sup>12+</sup>    | boolean                              | No   |  Yes | Whether to start the authorization Picker. The default value is **false** (non-authorization mode). When **authMode** is **true**, the authorization mode is enabled, and **defaultFilePathUri** is mandatory, indicating the URI to be authorized.<br>**Device behavior differences**: This parameter can be used on 2-in-1 devices but has no effect on other devices.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.FileManagement.UserFileService.FolderSelection  |
|multiAuthMode<sup>15+</sup>  | boolean                             |No    |  Yes | Whether to enable the batch authorization mode. The default value is **false** (non-batch authorization mode). When **multiAuthMode** is **true**, the batch authorization mode is enabled. When **multiAuthMode** is **true**, only the **multiUriArray** parameter takes effect, and other parameters do not take effect.<br> **Device behavior differences**: This parameter can be used on smartphones but has no effect on other devices.<br>**Atomic service API**: This API can be used in atomic services since API version 15.<br>**System capability**: SystemCapability.FileManagement.UserFileService |
|multiUriArray<sup>15+</sup>  | Array&lt;string&gt;                             |No    |  Yes | URI array to be authorized in batch (only files are supported; folders do not take effect). Use it together with **multiAuthMode**. When **multiAuthMode** is **false**, configuring this parameter does not take effect. The default value is empty (the effect is that the files displayed after the batch authorization page is launched are empty).<br> **Device behavior differences**: This parameter can be used on smartphones but has no effect on other devices.<br>**Atomic service API**: This API can be used in atomic services since API version 15.<br>**System capability**: SystemCapability.FileManagement.UserFileService|
|mergeMode<sup>15+</sup>  | [MergeTypeMode](#mergetypemode15)                             |No    |  Yes | Enables the aggregate view mode, which supports launching the aggregate view of the file management application. The default value is **DEFAULT**, which means this parameter does not take effect and the non-aggregate view is used. When this parameter is set to a value other than **DEFAULT**, other parameters do not take effect.<br>In API version 26.0.0 and later, when this parameter is set to a value other than **DEFAULT**, only the **fileSuffixFilters** parameter takes effect, and other parameters do not take effect. This parameter is not recommended to be used together with **multiAuthMode**.<br> **Device behavior differences**: This parameter can be used on smartphones but has no effect on other devices.<br>**Atomic service API**: This API can be used in atomic services since API version 15.<br>**System capability**: SystemCapability.FileManagement.UserFileService|
|isEncryptionSupported<sup>19+</sup>    | boolean |No    |  Yes | Whether encryption is supported (only files are supported; folders do not take effect). The default value is **false**. When this parameter is **true**, files can be encrypted on the Picker page.<br>**Atomic service API**: This API can be used in atomic services since API version 19.<br> **System capability**: SystemCapability.FileManagement.UserFileService |
| allowsMulFolderSelection       | boolean                                      | No   | Yes | Whether multiple folders can be selected. The value **true** indicates that multiple folders can be selected, and the value **false** indicates the opposite. The default value is **false**.<br>This parameter must be used together with **selectMode**. When **selectMode** is set to **FOLDER** or **MIXED** and **allowsMulFolderSelection** is set to **true**, the function of selecting multiple folders takes effect.<br>**Since**: 26.0.0<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.<br>**Model restriction**: This API can be used only in the stage model.<br> **System capability**: SystemCapability.FileManagement.UserFileService.FolderSelection |

## DocumentPickerMode<sup>12+</sup>

Enumerates the modes for saving documents.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

| Name  |  Value |  Description |
| ----- |  ---- | ---- |
| DEFAULT  | 0  | Standard mode, which is applicable to saving common files. You can customize the saving behavior by setting parameters such as **newFileNames**, **defaultFilePathUri**, and **fileSuffixChoices**. |
| DOWNLOAD | 1  | Download mode, which simplifies the saving process for file download. You can save files without specifying the file name and extension. <br>**Note:** The directories created in DOWNLOAD mode are used only to save files. There is no access isolation between directories. You are advised not to save sensitive app data. |

## MergeTypeMode<sup>15+</sup>

Enumerates file aggregation types.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.FileManagement.UserFileService

**Device behavior differences**: This API can be called on mobile phones but has no effect on other devices.

| Name  |  Value |  Description |
| ----- | ---- | ---- |
| DEFAULT  | 0  | Default mode, indicating that this parameter does not take effect. |
| AUDIO | 1  | Audio file mode, where the aggregated view displays files by audio file type. |
| VIDEO  | 2  | Video file mode, where the aggregated view displays files by video file type. |
| DOCUMENT | 3  | Document file mode, where the aggregated view displays files by document file type. |
| PICTURE  | 4  | Picture file mode, where the aggregated view displays files by picture file type. |

## DocumentSaveOptions

Defines the options for saving documents.

| Name                    | Type                                          | Read-Only | Optional | Description                                       |
| :---------------------- |---------------------------------------------| ---- | ---- | ------------------------------------------|
| newFileNames            | Array&lt;string&gt;   | No | Yes   | Name of the document to save when launching documentPicker. If this parameter is absent, the user needs to enter the file name by default.<br>**Atomic service API**: This interface supports use in atomic services since API version 12.<br>**System capability**: SystemCapability.FileManagement.UserFileService  |
| defaultFilePathUri<sup>10+</sup>    | string  | No| Yes    | URI of the file or directory to save. The default value is empty.<br>**Atomic service API**: This interface supports use in atomic services since API version 12.<br>**System capability**: SystemCapability.FileManagement.UserFileService  |
| fileSuffixChoices<sup>10+</sup>     | Array&lt;string&gt; | No| Yes    | Extension type of the file to save. Pass in a string array, where each item represents one extension option. Each item is internally divided into two parts by "\|\", with the first part being the description and the second part being the extension to save. If there is no "\|\", there is no description, and the item as a whole is an extension to save. By default, there is no extension type.<br>**Atomic service API**: This interface supports use in atomic services since API version 12.<br>**System capability**: SystemCapability.FileManagement.UserFileService |
| pickerMode<sup>12+</sup>     | [DocumentPickerMode](#documentpickermode12) | No| Yes    | Type of the picker to launch. The default value is DEFAULT. When pickerMode is set to DOWNLOAD, the parameters newFileNames, defaultFilePathUri, and fileSuffixChoices configured by the user will not take effect.<br>**Atomic service API**: This interface supports use in atomic services since API version 12.<br>**System capability**: SystemCapability.FileManagement.UserFileService |
| autoCreateEmptyFile<sup>23+</sup> | boolean | No | Yes | When saving a file, the application decides whether to pre-create an empty file. The default value is true, in which case the Picker pre-creates an empty file and returns an array of the file URIs. If it is set to false, no empty file is pre-created, and only an array of the file URIs is returned.<br>**Model restriction**: This interface can be used only in the stage model.<br>**System capability**: SystemCapability.FileManagement.UserFileService.FolderSelection |

## AudioSelectOptions

Defines the options for selecting audio clips.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

| Name                    | Type                                          | Read-Only | Optional | Description                                       |
| :---------------------- |---------------------------------------------| ---- | ---- | ------------------------------------------|
| maxSelectNumber<sup>12+</sup>       | number                                   | No     | Yes   | Maximum number of files to select. The default value is 1, the upper limit is 500, and the valid value range is 1-500. |

## AudioSaveOptions

Defines the options for saving audio clips.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

| Name                    | Type                                          | Read-Only | Optional | Description                                       |
| ---------------------- |---------------------------------------------| ---- | ---- | ------------------------------------------|
| newFileNames              | Array&lt;string&gt;   | No | Yes | File name used to launch audioPicker to save audio resources. If this parameter is absent, the user needs to input it by default. |

## PhotoViewPicker<sup>(deprecated)</sup>

Provides APIs for selecting and saving images or videos. You are advised to use [PhotoViewPicker](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoViewPicker.md) of **PhotoAccessHelper** to select a file. Before using the APIs of **PhotoViewPicker**, you need to create a **PhotoViewPicker** instance.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [photoAccessHelper.PhotoViewPicker](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoViewPicker.md) instead.

**System capability**: SystemCapability.FileManagement.UserFileService

### constructor<sup>(deprecated)</sup>

constructor(context: Context)

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name | Type    | Mandatory | Description                                                         |
| --------- | ------- | --------- | ------------------------------------------------------------ |
| context   | Context | Yes       | Application context (only **UIAbilityContext** is supported). For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |

A constructor used to create a **PhotoViewPicker** instance. This constructor is recommended. For details about how to obtain the context, see [getHostContext](../apis-arkui/arkts-apis-uicontext-uicontext.md#gethostcontext12).

> **NOTE**
>
> This API is supported since API version 12 and deprecated since API version 18. You are advised to use [photoAccessHelper.PhotoViewPicker](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoViewPicker.md) instead.

**Example**

```ts
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
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext; // Ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
            let photoPicker = new picker.PhotoViewPicker(context);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### constructor<sup>(deprecated)</sup>

constructor()

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.UserFileService

A constructor used to create a **PhotoViewPicker** instance. This constructor is not recommended due to the potential risk of operation failure.

> **NOTE**
>
> This API is supported since API version 12 and deprecated since API version 18. You are advised to use [photoAccessHelper.PhotoViewPicker](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoViewPicker.md) instead.

**Example**

```ts
let photoPicker = new picker.PhotoViewPicker(); // Not recommended to use the parameterless constructor, as it may cause probabilistic launch failures.
```

### select<sup>(deprecated)</sup>

select(option?: PhotoSelectOptions): Promise&lt;PhotoSelectResult&gt;

Starts a **photoPicker** page for the user to select one or more images or videos. This API uses a promise to return the result. You can pass in **PhotoSelectOptions** to specify the type and maximum number of the files to select.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [photoAccessHelper.PhotoViewPicker#select](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoViewPicker.md#select) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| option | [PhotoSelectOptions](#photoselectoptionsdeprecated) | No   | Selection option of photoPicker, used for configuration of image/video selection parameters (such as media file type, maximum number of selections, etc.). If this parameter is absent, the media file types selected by default are image and video. The default maximum number of media files that can be selected is 50. |

**Return value**

| Type                            | Description    |
| ----------------------------- | :---- |
| Promise&lt;[PhotoSelectResult](#photoselectresultdeprecated)&gt; | Promise used to return the result set selected by photoPicker. If the call fails, **reject** throws **BusinessError**. <br>**Note:** The **photoUris** in the **PhotoSelectResult** object returned by this API can be used only by calling [photoAccessHelper.getAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets) through temporary authorization. For details, see [Using a Media File URI](../../file-management/user-file-uri-intro.md#using-a-media-file-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example01(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext
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

### select<sup>(deprecated)</sup>

select(option: PhotoSelectOptions, callback: AsyncCallback&lt;PhotoSelectResult&gt;): void

Starts a **photoPicker** page for the user to select one or more images or videos. This API uses an asynchronous callback to return the result. You can pass in **PhotoSelectOptions** to specify the type and maximum number of the files to select.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [photoAccessHelper.PhotoViewPicker#select](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoViewPicker.md#select-1) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| option | [PhotoSelectOptions](#photoselectoptionsdeprecated) | Yes   | Photo picker selection option, used for configuring image/video selection parameters (such as media file type, maximum selection quantity, etc.). |
| callback | AsyncCallback&lt;[PhotoSelectResult](#photoselectresultdeprecated)&gt;      | Yes   | Callback returns the result set after photo picker selection.<br>**NOTE**: The photoUris in the PhotoSelectResult object returned by this interface can only be used by calling [photoAccessHelper.getAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets) through temporary authorization. For specific usage, see [media file URI usage](../../file-management/user-file-uri-intro.md#using-a-media-file-uri) in the user file URI introduction. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example02(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext
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

### select<sup>(deprecated)</sup>

select(callback: AsyncCallback&lt;PhotoSelectResult&gt;): void

Starts a **photoPicker** page for the user to select one or more images or videos. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [photoAccessHelper.PhotoViewPicker#select](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoViewPicker.md#select-2) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------- | ---- | -------------------------- |
| callback | AsyncCallback&lt;[PhotoSelectResult](#photoselectresultdeprecated)&gt; | Yes | Callback used to return the result set after photoPicker selection.<br>**NOTE**: The photoUris in the PhotoSelectResult object returned by this interface can be used only by calling [photoAccessHelper.getAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets) through temporary authorization. For details, see [Usage of Media File URIs](../../file-management/user-file-uri-intro.md#using-a-media-file-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example03(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

### save<sup>(deprecated)</sup>

save(option?: PhotoSaveOptions): Promise&lt;Array&lt;string&gt;&gt;

Starts a **photoPicker** page for the user to save one or more images or videos. This API uses a promise to return the result. You can pass in **PhotoSaveOptions** to specify the URIs of the images or videos to save.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. Use [SaveButton](../apis-arkui/arkui-ts/ts-security-components-savebutton.md) instead.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| option | [PhotoSaveOptions](#photosaveoptionsdeprecated) | No   | Options for saving images or videos with photoPicker, used for configuration of image/video saving parameters (such as the saved file name). If this parameter is absent, after the photoPicker interface is launched, the user needs to enter the saved file name. |

**Return value**

| Type                            | Description    |
| ----------------------------- | :---- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the result set after photoPicker saves images or videos. If the call fails, **reject** throws **BusinessError**.<br>**Note:** This API saves files in **Files**, not in **Gallery**. For details about how to use the returned URI array, see [Using a Document URI](../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example04(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

### save<sup>(deprecated)</sup>

save(option: PhotoSaveOptions, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Starts a **photoPicker** page for the user to save one or more images or videos. This API uses an asynchronous callback to return the result. You can pass in **PhotoSaveOptions** to specify the URIs of the images or videos to save.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. Use [SaveButton](../apis-arkui/arkui-ts/ts-security-components-savebutton.md) instead.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| option | [PhotoSaveOptions](#photosaveoptionsdeprecated) | Yes   | Options for saving image or video files with photoPicker, used to configure the parameters for saving images/videos (such as the saved file name). |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt;      | Yes   | Callback that returns the result set after photoPicker saves image or video files.<br>**NOTE**: This interface saves files to the file manager instead of the gallery. For details about how to use the returned URI array, see [Usage of Document URIs](../../file-management/user-file-uri-intro.md#using-a-document-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example05(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

### save<sup>(deprecated)</sup>

save(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Starts a **photoPicker** page for the user to save one or more images or videos. This API uses an asynchronous callback to return the URIs of the images or videos to save.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. Use [SaveButton](../apis-arkui/arkui-ts/ts-security-components-savebutton.md) instead.

**System capability**: SystemCapability.FileManagement.UserFileService

**Parameters**

| Name  | Type    | Mandatory | Description                       |
| ------- | ------- | ---- | -------------------------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt;      | Yes   | Callback used to return the result set after photoPicker saves an image or video file.<br>**NOTE**: This interface saves the file to the file manager instead of the gallery. For details about how to use the returned URI array, see [Usage of Document URIs](../../file-management/user-file-uri-intro.md#using-a-document-uri) in the introduction to user file URIs. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { picker } from '@kit.CoreFileKit';
async function example06(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

## PhotoViewMIMETypes<sup>(deprecated)</sup>

Enumerates the media file types.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [photoAccessHelper.PhotoViewMIMETypes](../apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#photoviewmimetypes) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.UserFileService

| Name  |  Value |  Description |
| ----- |  ---- | ---- |
| IMAGE_TYPE  |  'image/*' | Image type.<br>**NOTE**: This API is supported since API version 9 and deprecated since API version 18.  |
| VIDEO_TYPE |  'video/*' | Video type. <br>**NOTE**: This API is supported since API version 9 and deprecated since API version 18. |
| IMAGE_VIDEO_TYPE |  '\*/*' | Image and video type.<br>**NOTE**: This API is supported since API version 9 and deprecated since API version 18.  |

## PhotoSelectOptions<sup>(deprecated)</sup>

Defines the options for selecting images or videos.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [photoAccessHelper.PhotoSelectOptions](../apis-media-library-kit/arkts-apis-photoAccessHelper-class.md#photoselectoptions) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.UserFileService

| Name                    | Type                                          | Read-Only | Optional | Description                                       |
| :---------------------- |---------------------------------------------| ---- | ---- | ------------------------------------------|
| MIMEType              | [PhotoViewMIMETypes](#photoviewmimetypesdeprecated)  | No  | Yes   | Selectable media file types. If this parameter is absent, the default is image and video types.<br>**NOTE**<br>This API is supported since API version 9 and deprecated since API version 18.  |
| maxSelectNumber       | number  | No | Yes   | Maximum number of selectable media files. The default value is 50, and the valid range is [1, 500]. If the value is out of range, the passed value does not take effect and the default value is used.<br>**NOTE**<br>This API is supported since API version 9 and deprecated since API version 18.      |

## PhotoSelectResult<sup>(deprecated)</sup>

Defines information about the images or videos selected.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [photoAccessHelper.PhotoSelectResult](../apis-media-library-kit/arkts-apis-photoAccessHelper-class.md#photoselectresult) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.UserFileService

| Name                    | Type                                          | Read-Only | Optional | Description                                       |
| :---------------------- |---------------------------------------------| ---- | ---- | ------------------------------------------|
| photoUris        | Array&lt;string&gt;    | No | No  | URIs of the media files selected. This URI array can be used only by [photoAccessHelper.getAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets). For details, see [Using a Media File URI](../../file-management/user-file-uri-intro.md#using-a-media-file-uri).<br>**Note**: This API is supported since API version 9 and deprecated since API version 18.  |
| isOriginalPhoto        | boolean   | No  | No   | Whether the media file selected is the original photo. The value **true** means the original photo, and **false** means not the original photo.<br>**Note**: This API is supported since API version 9 and deprecated since API version 18.  |

## PhotoSaveOptions<sup>(deprecated)</sup>

Defines the options for saving images or videos.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. Use [SaveButtonOptions](../apis-arkui/arkui-ts/ts-security-components-savebutton.md#savebuttonoptions) instead.

**System capability**: SystemCapability.FileManagement.UserFileService

| Name                    | Type                                          | Read-Only | Optional | Description                                       |
| :---------------------- |---------------------------------------------| ---- | ---- | ------------------------------------------|
| newFileNames              | Array&lt;string&gt;    | No | Yes  | File names for saving images or video resources when launching photoPicker. If this parameter is absent, the user needs to enter the file names by default.<br>**NOTE**<br>This API is supported since API version 9 and deprecated since API version 18. |
