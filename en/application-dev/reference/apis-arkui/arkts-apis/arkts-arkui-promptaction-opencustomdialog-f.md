# openCustomDialog

## Modules to Import

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## openCustomDialog

```TypeScript
function openCustomDialog(options: CustomDialogOptions): Promise<number>
```

Opens a custom dialog box. This API uses a promise to return the result.

<!--Del-->This API cannot be used in **ServiceExtension**.<!--DelEnd-->

By default, the width of the dialog box in portrait mode is the width of the window where it is located minus the left and right margins (40 vp for 2-in-1 devices and 16 vp for other devices), and the maximum width is 400 vp.

> **NOTE:** 
> 
> - This API is supported since API version 11 and deprecated since API version 18. You are advised to use openCustomDialog instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using **openCustomDialog** can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
> 
> - Since API version 12, you can use the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object associated with the current UI context.

**Since:** 11

**Deprecated since:** 18

**Substitutes:** openCustomDialog

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CustomDialogOptions](arkts-arkui-promptaction-customdialogoptions-i.md) | Yes | Content of the custom dialog box. <br>Note: If both [isModal](arkts-arkui-promptaction-basedialogoptions-i.md) and [showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md) in **BaseDialogOptions** are set to **true**, only **showInSubWindow** takes effect. In this case, the non-modal dialog box is displayed without mask in the subwindow. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | ID of the custom dialog box, which can be used in **closeCustomDialog**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

```TypeScript
openCustomDialog(options: CustomDialogOptions): Promise<number>

Opens a custom dialog box. This API uses a promise to return the result.

By default, the width of the dialog box in portrait mode is the width of the window where it is located minus the left and right margins (40 vp for 2-in-1 devices and 16 vp for other devices), and the maximum width is 400 vp.

> NOTE
> 
> This API is supported since API version 11 and deprecated since API version 18. You are advised to use openCustomDialog instead. Before calling this API, you need to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) method in [UIContext](arkts-apis-uicontext-uicontext.md). Directly using openCustomDialog can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).
> 
> Since API version 12, you can use the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object associated with the current UI context.

Model constraint: This API can be used only in the stage model.

Atomic service API: This API can be used in atomic services since API version 12.

System capability: SystemCapability.ArkUI.ArkUI.Full

Parameters

Return value

Error codes

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md) and [API Call Error Codes](../errorcode-internal.md).
```

```TypeScript
This example demonstrates how to set styles of a dialog box, including the width, height, background color, and shadow.

> NOTE
> 
> Directly using openCustomDialog can lead to the issue of ambiguous UI context. To avoid this, obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) and then call the openCustomDialog API through this object.
```

```TypeScript


This example shows how to implement a dialog box on a page.

> NOTE
> 
> Directly using openCustomDialog can lead to the issue of ambiguous UI context. To avoid this, obtain the [PromptAction](arkts-apis-uicontext-promptaction.md) object using the [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) API in [UIContext](arkts-apis-uicontext-uicontext.md) and then call the openCustomDialog API through this object.
```

```TypeScript
// Next.ets
@Entry
@Component
struct Next {
  @State message: string = 'Back';

  build() {
    Row() {
      Column() {
        Button(this.message)
          .onClick(() => {
            this.getUIContext().getRouter().back();
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
