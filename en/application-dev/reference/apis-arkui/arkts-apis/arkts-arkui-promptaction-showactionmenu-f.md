# showActionMenu

## Modules to Import

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## showActionMenu

```TypeScript
function showActionMenu(options: ActionMenuOptions, callback: AsyncCallback<ActionMenuSuccessResponse>): void
```

Creates and displays an action menu. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use showActionMenu instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **showActionMenu** can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
> 
> - Since API version 11, you can use the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object associated with the current UI context.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** showActionMenu

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | Yes | Action menu options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md)&gt; | Yes | Callback used to return the result. On success, **err** is **undefined** and **data** contains the action menu response. On failure, **err** provides error details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

showActionMenu(options: ActionMenuOptions, callback: AsyncCallback<ActionMenuSuccessResponse>):void

Creates and displays an action menu. This API uses an asynchronous callback to return the result.

> NOTE
> 
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use showActionMenu instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using showActionMenu can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
> 
> Since API version 11, you can use the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object associated with the current UI context.

Atomic service API: This API can be used in atomic services since API version 11.

System capability: SystemCapability.ArkUI.ArkUI.Full

Parameters

Error codes

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md) and [API Call Error Codes](../errorcode-internal.md).

Example 1

```TypeScript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  promptAction.showActionMenu({
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
} catch (error) {
  let message = (error as BusinessError).message
  let code = (error as BusinessError).code
  console.error(`showActionMenu args error code is ${code}, message is ${message}`);
};
```



Example 2

This example demonstrates how to use the onDidAppear, onDidDisappear, onWillAppear, and onWillDisappear properties of ActionMenuOptions to implement the action menu lifecycle callbacks, supported since API version 19.

```TypeScript
import { promptAction } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State isShown: boolean = false
  @State textColor: Color = Color.Black
  @State blueColor: Color = Color.Blue

  @State onWillAppear: boolean = false
  @State onDidAppear: boolean = false
  @State onWillDisappear: boolean = false
  @State onDidDisappear: boolean = false
  build() {
    Column({ space: 50 }) {
      Text('onWillAppear').fontColor(this.onWillAppear ? this.blueColor : this.textColor)
      Text('onDidAppear').fontColor(this.onDidAppear ? this.blueColor : this.textColor)
      Text('onWillDisappear').fontColor(this.onWillDisappear ? this.blueColor : this.textColor)
      Text('onDidDisappear').fontColor(this.onDidDisappear ? this.blueColor : this.textColor)
      Button('click')
        .width(200)
        .height(100)
        .margin(100)
        .fontColor(this.textColor)
        .onClick(() => {
          promptAction.showActionMenu({
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
            ],
            onWillAppear:() => {
              console.info("promptAction menu cycle life onWillAppear");
              this.onWillAppear = true;
            },
            onDidAppear:() => {
              console.info("promptAction menu cycle life onDidAppear");
              this.onDidAppear = true;
            },
            onWillDisappear:() => {
              this.isShown = false;
              console.info("promptAction menu cycle life onWillDisappear");
              this.onWillDisappear = true;
            },
            onDidDisappear:() => {
              console.info("promptAction menu cycle life onDidDisappear");
              this.onDidDisappear = true;
            }
          })
            .then(data => {
              console.info('showActionMenu success, click button: ' + data.index);
            })
            .catch((err: Error) => {
              console.info('showActionMenu error: ' + err);
            })
        })
    }
    .width('100%')
  }
}
```


<a id="showactionmenu-1"></a>

## showActionMenu

```TypeScript
function showActionMenu(options: ActionMenuOptions): Promise<ActionMenuSuccessResponse>
```

Creates and displays an action menu in the given settings. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use showActionMenu instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **showActionMenu** can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
> 
> - Since API version 10, you can use the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object associated with the current UI context.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** showActionMenu

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | Yes | Promise that returns the action menu response. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md)&gt; | Promise that returns the action menu response. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

showActionMenu(options: ActionMenuOptions): Promise<ActionMenuSuccessResponse>

Creates and displays an action menu in the given settings. This API uses a promise to return the result.

> NOTE
> 
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use showActionMenu instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using showActionMenu can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
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

promptAction.showActionMenu({
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
  .catch((err: Error) => {
    console.info('showActionMenu error: ' + err);
  })
```
