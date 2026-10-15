# disableAlertBeforeBackPage

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## disableAlertBeforeBackPage

```TypeScript
function disableAlertBeforeBackPage(): void
```

Disables the display of a confirm dialog box before returning to the previous page. After this API is called, the return confirm dialog box enabled by [enableAlertBeforeBackPage](arkts-arkui-router-enablealertbeforebackpage-f.md) will be closed, and the [back](arkts-arkui-router-back-f.md) operation will no longer display a confirm dialog box but will directly perform the page return.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [hideAlertBeforeBackPage](arkts-arkui-arkui-uicontext-router-c.md#hidealertbeforebackpage)

<!--Device-router-function disableAlertBeforeBackPage(): void--><!--Device-router-function disableAlertBeforeBackPage(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

disableAlertBeforeBackPage(): void

Disables the display of a confirm dialog box before returning to the previous page. After this API is called, the return confirm dialog box enabled by enableAlertBeforeBackPage will be closed, and the back operation will no longer display a confirm dialog box but will directly perform the page return.

> NOTE
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use hideAlertBeforeBackPage instead.

System capability: SystemCapability.ArkUI.ArkUI.Full

```TypeScript
import { router } from '@kit.ArkUI';

router.disableAlertBeforeBackPage();
```
