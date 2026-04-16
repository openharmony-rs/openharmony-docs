# @ohos.app.ability.PrintExtensionAbility (Print Extension Ability) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @gcw_4D6e0BBd-->
<!--Tester: @guoshengbang-->
<!--Adviser: @RayShih-->

The **PrintExtensionAbility** module provides operation APIs of the print extension ability.

> **NOTE** 
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.app.ability.PrintExtensionAbility (PrintExtensionAbility)](js-apis-app-ability-PrintExtensionAbility.md).
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```

## PrintExtensionAbility

### onRequestPreview

onRequestPreview(jobInfo: print.PrintJob): string

Called when a print preview request is sent. The result is returned to the print SA.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobInfo | [print.PrintJob](js-apis-print.md#printjob24) | Yes| Information about the print job.|

**Return value**

| Type| Description|
| -------- | -------- |
| string | Preview result.|

**Error codes**

For details about the error codes, see [Print Service Error Codes](errorcode-print.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 202 | not system application. |

**Example**

```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onRequestPreview(jobInfo: print.PrintJob): string {
        console.info('onRequestPreview enter');
        // ...
        let tmp : string = '';
        return tmp;
    }
}
```
