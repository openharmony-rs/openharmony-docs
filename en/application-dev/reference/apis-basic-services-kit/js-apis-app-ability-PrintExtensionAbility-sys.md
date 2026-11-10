# @ohos.app.ability.PrintExtensionAbility (Print Extension Ability) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @Zouhaifeng1-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=432796cf3e6a4be981f95a7796deb982eeaff362 translatedAt=2026-11-10T04:00:44.972Z pushedAt=2026-11-10T06:11:10.782Z nl=1 -->

This module provides APIs for calling the print extension ability. **PrintExtensionAbility** is the base class for print extensions. The system print service calls the extension methods implemented by developers in scenarios such as print preview. Developers need to inherit this class and implement related callbacks to provide custom print extension capabilities. For details about the printing framework, see [@ohos.print (Printing)](js-apis-print.md).

> **NOTE**
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only the system APIs of this module. For details about other public APIs, see [@ohos.app.ability.PrintExtensionAbility](js-apis-app-ability-PrintExtensionAbility.md).
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```

## PrintExtensionAbility

### onRequestPreview

onRequestPreview(jobInfo: print.PrintJob): string

Defines a method called when the system print service requests a preview. You need to inherit the **PrintExtensionAbility** class and implement this method to return the preview result to the system print service.

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

For details about the error codes, see [Print Service Error Codes](errorcode-print.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message | Description |
| -------- | -------- | -------- |
| 202 | not system application. | Only system apps can implement this API. If a non-system app attempts to implement this API, this error code will be returned. Ensure that your app has the system app permission before implementing this API. |

**Example**

```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onRequestPreview(jobInfo: print.PrintJob): string {
        console.info('onRequestPreview enter');
        // ...
        let previewResult: string = '';
        return previewResult;
    }
}
```
