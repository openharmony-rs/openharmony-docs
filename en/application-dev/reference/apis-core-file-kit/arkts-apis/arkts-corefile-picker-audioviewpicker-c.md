# AudioViewPicker

```TypeScript
class AudioViewPicker
```

Provides APIs for selecting and saving audio clips. Before using the APIs of **AudioViewPicker**, you need to create an **AudioViewPicker** instance.

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

A constructor used to create an **AudioViewPicker** instance. This constructor is not recommended due to the potential risk of operation failure.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

**Examples**

```TypeScript
let audioPicker = new picker.AudioViewPicker(); // Construction without parameter is not recommended. There is a possibility that the AudioViewPicker instance fails to start.
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(context: Context)
```

A constructor used to create an **AudioViewPicker** instance. This constructor is recommended. For details about how to obtain the context, see [getHostContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#gethostcontext).

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

Starts an **audioPicker** page (currently, a **documentPicker** page is displayed) for the user to save one or more audio clips. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [AudioSaveOptions](arkts-corefile-picker-audiosaveoptions-c.md) | No | Options for saving audio clips. If this parameter is not specified, an **audioPicker** page will be displayed for the user to enter the names of the files to save. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the URIs of the audio clips saved. <br>**Note:**  For details about how to use the returned URIs, see [Using a Document URI](../../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example16(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

<a id="save-1"></a>

## save

```TypeScript
save(option: AudioSaveOptions, callback: AsyncCallback<Array<string>>): void
```

Starts an **audioPicker** page (currently, a **documentPicker** page is displayed) for the user to save one or more audio clips. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [AudioSaveOptions](arkts-corefile-picker-audiosaveoptions-c.md) | Yes | Options for saving audio clips. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback invoked to return the URIs of the audio clips saved. <br>**Note:**  For details about how to use the returned URIs, see [Using a Document URI](../../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
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

<a id="save-2"></a>

## save

```TypeScript
save(callback: AsyncCallback<Array<string>>): void
```

Starts an **audioPicker** page (currently, a **documentPicker** page is displayed) for the user to save one or more audio clips. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback invoked to return the URIs of the audio clips saved. <br>**Note:**  For details about how to use the returned URIs, see [Using a Document URI](../../../file-management/user-file-uri-intro.md#using-a-document-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
async function example18(context: common.UIAbilityContext) { // Ensure that context is converted from UIAbilityContext.
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

Starts an **audioPicker** page for the user to select one or more audio clips. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [AudioSelectOptions](arkts-corefile-picker-audioselectoptions-c.md) | No | Options for selecting audio clips. If this parameter is not specified, the **audioPicker** page is displayed by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the URIs of the audio clips selected. <br>**Note:**  For details about how to use the returned URIs, see [Using a Media File URI](../../../file-management/user-file-uri-intro.md#using-a-media-file-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
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

<a id="select-1"></a>

## select

```TypeScript
select(option: AudioSelectOptions, callback: AsyncCallback<Array<string>>): void
```

Starts an **audioPicker** page for the user to select one or more audio clips. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [AudioSelectOptions](arkts-corefile-picker-audioselectoptions-c.md) | Yes | Options for selecting audio clips. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback invoked to return the URIs of the audio clips selected. <br>**Note:**  For details about how to use the returned URIs, see [Using a Media File URI](../../../file-management/user-file-uri-intro.md#using-a-media-file-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
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

<a id="select-2"></a>

## select

```TypeScript
select(callback: AsyncCallback<Array<string>>): void
```

Starts an **audioPicker** page for the user to select one or more audio clips. This API uses an asynchronous callback to return the result. **System capability**: SystemCapability.FileManagement.UserFileService

**Since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback invoked to return the URIs of the audio clips selected. <br>**Note:**  For details about how to use the returned URIs, see [Using a Media File URI](../../../file-management/user-file-uri-intro.md#using-a-media-file-uri). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import  { picker } from '@kit.CoreFileKit';
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
