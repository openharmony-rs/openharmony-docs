# showActionMenu

## Modules to Import

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## showActionMenu

```TypeScript
function showActionMenu(options: ActionMenuOptions, callback: AsyncCallback<ActionMenuSuccessResponse>): void
```

Displays the menu.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** showActionMenu

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ActionMenuOptions](arkts-arkui-prompt-actionmenuoptions-i.md) | Yes | Options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ActionMenuSuccessResponse](arkts-arkui-prompt-actionmenusuccessresponse-i.md)&gt; | Yes |  |

**Examples**

```TypeScript
import prompt from '@ohos.prompt'
prompt.showActionMenu({
  title: 'Title Info',
  buttons: [
    {
      text: 'item1',
      color: '#666666'
    },
    {
      text: 'item2',
      color: '#000000'
    },
  ]
}, (err, data) => {
  if (err) {
    console.info('showActionMenu err: ' + err);
    return;
  }
  console.info('showActionMenu success callback, click button: ' + data.index);
})
```


<a id="showactionmenu-1"></a>

## showActionMenu

```TypeScript
function showActionMenu(options: ActionMenuOptions): Promise<ActionMenuSuccessResponse>
```

Displays the menu.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** showActionMenu

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ActionMenuOptions](arkts-arkui-prompt-actionmenuoptions-i.md) | Yes | Options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ActionMenuSuccessResponse](arkts-arkui-prompt-actionmenusuccessresponse-i.md)&gt; |  |

**Examples**

```TypeScript
import prompt from '@ohos.prompt'
prompt.showActionMenu({
  title: 'showActionMenu Title Info',
  buttons: [
    {
      text: 'item1',
      color: '#666666'
    },
    {
      text: 'item2',
      color: '#000000'
    },
  ]
})
  .then(data => {
    console.info('showActionMenu success, click button: ' + data.index);
  })
  .catch((err:Error) => {
    console.info('showActionMenu error: ' + err);
  })
```
