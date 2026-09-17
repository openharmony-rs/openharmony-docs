# showDialog

## Modules to Import

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## showDialog

```TypeScript
function showDialog(options: ShowDialogOptions, callback: AsyncCallback<ShowDialogSuccessResponse>): void
```

Displays the dialog box.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** showDialog

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowDialogOptions](arkts-arkui-prompt-showdialogoptions-i.md) | Yes | Options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ShowDialogSuccessResponse](arkts-arkui-prompt-showdialogsuccessresponse-i.md)&gt; | Yes |  |

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


## showDialog

```TypeScript
function showDialog(options: ShowDialogOptions): Promise<ShowDialogSuccessResponse>
```

Displays the dialog box.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** showDialog

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowDialogOptions](arkts-arkui-prompt-showdialogoptions-i.md) | Yes | Options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ShowDialogSuccessResponse](arkts-arkui-prompt-showdialogsuccessresponse-i.md)&gt; |  |

**Examples**

See [showDialog](#showdialog)
