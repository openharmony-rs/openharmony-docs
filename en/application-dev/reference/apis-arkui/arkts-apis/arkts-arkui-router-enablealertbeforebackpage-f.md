# enableAlertBeforeBackPage

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## enableAlertBeforeBackPage

```TypeScript
function enableAlertBeforeBackPage(options: EnableAlertOptions): void
```

Enables the display of a confirm dialog box before returning to the previous page.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [showAlertBeforeBackPage](arkts-arkui-arkui-uicontext-router-c.md#showalertbeforebackpage)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md) | Yes | Description of the dialog box. |

**Examples**

```TypeScript
enableAlertBeforeBackPage(options: EnableAlertOptions): void

Enables the display of a confirm dialog box before returning to the previous page. After this API is called, a confirm dialog box will be displayed when back is executed to return to a page. The page return operation is performed only after the user confirms; if the user cancels, the return is not performed. This is applicable to scenarios where you need to prevent data loss caused by accidental return operations, for example, when the user is filling in a form, editing a document, or making a payment, a confirm dialog box is displayed to avoid accidental exit.

> NOTE
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use showAlertBeforeBackPage instead.

System capability: SystemCapability.ArkUI.ArkUI.Full

Parameters
```
