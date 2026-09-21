# showToast

## Modules to Import

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## showToast

```TypeScript
function showToast(options: ShowToastOptions): void
```

Creates and displays a toast.

> **NOTE:** 
> 
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use showToast instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **showToast** can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
> 
> - Since API version 10, you can use the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object associated with the current UI context.
> 
> - The toast has a fixed style and does not support content customization. For specific supported capabilities, see ShowToastOptions.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** showToast

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md) | Yes | Toast configuration options. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

showToast(options: ShowToastOptions): void

Creates and displays a toast.

> NOTE
> 
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use showToast instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using showToast can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
> 
> Since API version 10, you can use the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object associated with the current UI context.
> 
> The toast has a fixed style and does not support content customization. For specific supported capabilities, see ShowToastOptions.

Atomic service API: This API can be used in atomic services since API version 11.

System capability: SystemCapability.ArkUI.ArkUI.Full

Parameters

Error codes

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md) and [API Call Error Codes](../errorcode-internal.md).

> NOTE
> 
> If error code 100001 is returned, indicating an ambiguous UI context, use the corresponding APIs from UIContext instead. For details, see [Using the UI Context API for UI Operations (UIContext)](../../../ui/arkts-global-interface.md).

```TypeScript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct toastExample {
  build() {
    Column() {
      Button('Show toast').fontSize(20)
        .onClick(() => {
          try {
            promptAction.showToast({
              message: 'Hello World',
              duration: 2000
            });
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`showToast args error code is ${code}, message is ${message}`);
          };
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```
