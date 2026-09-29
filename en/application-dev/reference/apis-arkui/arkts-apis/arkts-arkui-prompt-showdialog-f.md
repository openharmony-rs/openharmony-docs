# showDialog

## Modules to Import

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## showDialog

```TypeScript
function showDialog(options: ShowDialogOptions, callback: AsyncCallback<ShowDialogSuccessResponse>): void
```

Shows a dialog box. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** showDialog

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-prompt-function showDialog(options: ShowDialogOptions, callback: AsyncCallback<ShowDialogSuccessResponse>): void--><!--Device-prompt-function showDialog(options: ShowDialogOptions, callback: AsyncCallback<ShowDialogSuccessResponse>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowDialogOptions](arkts-arkui-prompt-showdialogoptions-i.md) | Yes | Dialog box options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ShowDialogSuccessResponse](arkts-arkui-prompt-showdialogsuccessresponse-i.md)&gt; | Yes | Callback used to return the dialog box response result. |

**Examples**

```TypeScript
import prompt from '@ohos.prompt'
prompt.showDialog({
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
```


<a id="showdialog-1"></a>

## showDialog

```TypeScript
function showDialog(options: ShowDialogOptions): Promise<ShowDialogSuccessResponse>
```

Shows a dialog box. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** showDialog

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-prompt-function showDialog(options: ShowDialogOptions): Promise<ShowDialogSuccessResponse>--><!--Device-prompt-function showDialog(options: ShowDialogOptions): Promise<ShowDialogSuccessResponse>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowDialogOptions](arkts-arkui-prompt-showdialogoptions-i.md) | Yes | Dialog box options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ShowDialogSuccessResponse](arkts-arkui-prompt-showdialogsuccessresponse-i.md)&gt; | Promise used to return the dialog box response result. |

**Examples**

```TypeScript
import prompt from '@ohos.prompt'
prompt.showDialog({
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
  .catch((err:Error) => {
    console.info('showDialog error: ' + err);
  })
```
