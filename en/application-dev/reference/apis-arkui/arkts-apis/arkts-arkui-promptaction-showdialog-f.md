# showDialog

## Modules to Import

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## showDialog

```TypeScript
function showDialog(options: ShowDialogOptions, callback: AsyncCallback<ShowDialogSuccessResponse>): void
```

Creates and displays a dialog box. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use showDialog instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **showDialog** can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
> 
> - Since API version 10, you can use the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object associated with the current UI context.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** showDialog

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md) | Yes | Dialog box configuration options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ShowDialogSuccessResponse](arkts-arkui-promptaction-showdialogsuccessresponse-i.md)&gt; | Yes | Callback used to return the result. On success, **err** is **undefined** and **data** contains the dialog box response. On failure, **err** provides error details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

showDialog(options: ShowDialogOptions, callback: AsyncCallback<ShowDialogSuccessResponse>):void

Creates and displays a dialog box. This API uses an asynchronous callback to return the result.

> NOTE
> 
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use showDialog instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using showDialog can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
> 
> Since API version 10, you can use the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object associated with the current UI context.

Atomic service API: This API can be used in atomic services since API version 11.

System capability: SystemCapability.ArkUI.ArkUI.Full

Parameters

Error codes

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md) and [API Call Error Codes](../errorcode-internal.md).

```TypeScript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  promptAction.showDialog({
    title: 'showDialog Title Info',
    message: 'Message Info',
    buttons: [
      {
        text: 'button1',
        color: '#000000'
      },
      {
        text: 'button2',
        color: '#000000'
      }
    ]
  }, (err, data) => {
    if (err) {
      console.info('showDialog err: ' + err);
      return;
    }
    console.info('showDialog success callback, click button: ' + data.index);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  let code = (error as BusinessError).code;
  console.error(`showDialog args error code is ${code}, message is ${message}`);
};
```



When the showInSubWindow attribute is set to true, the toast can be displayed outside the window.

```TypeScript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  promptAction.showDialog({
    title: 'showDialog Title Info',
    message: 'Message Info',
    isModal: true,
    showInSubWindow: true,
    buttons: [
      {
        text: 'button1',
        color: '#000000'
      },
      {
        text: 'button2',
        color: '#000000'
      }
    ]
  }, (err, data) => {
    if (err) {
      console.info('showDialog err: ' + err);
      return;
    }
    console.info('showDialog success callback, click button: ' + data.index);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  let code = (error as BusinessError).code;
  console.error(`showDialog args error code is ${code}, message is ${message}`);
};
```



This example demonstrates how to use the onDidAppear, onDidDisappear, onWillAppear, and onWillDisappear properties of ShowDialogOptions to implement the dialog box lifecycle callbacks, supported since API version 19.

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct DialogExample {
  @State log: string = 'Log information:';
  build() {
    Column() {
      Button('showDialog')
        .onClick(() => {
          this.showCustomDialog();
        })
      Text(this.log).fontSize(30).margin({ top: 200 })
    }.width('100%').margin({ top: 5 })
  }

  showCustomDialog() {
    try {
      this.getUIContext().getPromptAction().showDialog({
        title: 'Confirm',
        message: 'Are you sure you want to continue?',
        alignment: DialogAlignment.Bottom,
        buttons: [
          {
            text: 'Cancel',
            color: '#999999'
          },
          {
            text: 'OK',
            color: '#007DFF'
          }
        ],
        onDidAppear: () => {
          this.log += '# onDidAppear';
          console.info("showDialog,is onDidAppear!");
        },
        onDidDisappear: () => {
          this.log += '# onDidDisappear';
          console.info("showDialog,is onDidDisappear!");
        },
        onWillAppear: () => {
          this.log = 'Log information:#onWillAppear';
          console.info("showDialog,is onWillAppear!");
        },
        onWillDisappear: () => {
          this.log += '# onWillDisappear';
          console.info("showDialog,is onWillDisappear!");
        },
      })
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`Exception caught: ${err.code}, ${err.message}`);
    }
  }
}
```


<a id="showdialog-1"></a>

## showDialog

```TypeScript
function showDialog(options: ShowDialogOptions): Promise<ShowDialogSuccessResponse>
```

Creates and displays a dialog box in the given settings. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use showDialog instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **showDialog** can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
> 
> - Since API version 10, you can use the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object associated with the current UI context.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** showDialog

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md) | Yes | Dialog box configuration options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ShowDialogSuccessResponse](arkts-arkui-promptaction-showdialogsuccessresponse-i.md)&gt; | Promise that returns the dialog box response. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

showDialog(options: ShowDialogOptions): Promise<ShowDialogSuccessResponse>

Creates and displays a dialog box in the given settings. This API uses a promise to return the result.

> NOTE
> 
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use showDialog instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using showDialog can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
> 
> Since API version 10, you can use the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object associated with the current UI context.

Atomic service API: This API can be used in atomic services since API version 11.

System capability: SystemCapability.ArkUI.ArkUI.Full

Parameters

Return value

Error codes

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md) and [API Call Error Codes](../errorcode-internal.md).

```TypeScript
import { promptAction } from '@kit.ArkUI';

promptAction.showDialog({
  title: 'Title Info',
  message: 'Message Info',
  buttons: [
    {
      text: 'button1',
      color: '#000000'
    },
    {
      text: 'button2',
      color: '#000000'
    }
  ],
})
  .then(data => {
    console.info('showDialog success, click button: ' + data.index);
  })
  .catch((err: Error) => {
    console.info('showDialog error: ' + err);
  })
```
