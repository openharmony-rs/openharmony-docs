# showActionMenu

## Modules to Import

```TypeScript
import { prompt } from '@kit.ArkUI';
```

<a id="showactionmenu1"></a>

## showActionMenu

```TypeScript
function showActionMenu(options: ActionMenuOptions, callback: AsyncCallback<ActionMenuSuccessResponse>): void
```

Shows an action menu. This API uses a callback to return the result asynchronously.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [showActionMenu](arkts-arkui-arkui-uicontext-promptaction-c.md#showactionmenu)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-prompt-function showActionMenu(options: ActionMenuOptions, callback: AsyncCallback<ActionMenuSuccessResponse>): void--><!--Device-prompt-function showActionMenu(options: ActionMenuOptions, callback: AsyncCallback<ActionMenuSuccessResponse>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ActionMenuOptions](arkts-arkui-prompt-actionmenuoptions-i.md) | Yes | Action menu options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ActionMenuSuccessResponse](arkts-arkui-prompt-actionmenusuccessresponse-i.md)&gt; | Yes | Callback used to return the action menu response result. |

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


<a id="showactionmenu2"></a>

## showActionMenu

```TypeScript
function showActionMenu(options: ActionMenuOptions): Promise<ActionMenuSuccessResponse>
```

Shows an action menu. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [showActionMenu](arkts-arkui-arkui-uicontext-promptaction-c.md#showactionmenu)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-prompt-function showActionMenu(options: ActionMenuOptions): Promise<ActionMenuSuccessResponse>--><!--Device-prompt-function showActionMenu(options: ActionMenuOptions): Promise<ActionMenuSuccessResponse>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ActionMenuOptions](arkts-arkui-prompt-actionmenuoptions-i.md) | Yes | Action menu options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ActionMenuSuccessResponse](arkts-arkui-prompt-actionmenusuccessresponse-i.md)&gt; | Promise used to return the action menu response result. |

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
