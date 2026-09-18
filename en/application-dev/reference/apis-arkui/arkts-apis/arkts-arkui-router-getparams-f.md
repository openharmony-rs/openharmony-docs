# getParams

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## getParams

```TypeScript
function getParams(): Object
```

Obtains the parameters passed from the page that initiates redirection to the current page.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.
> 
> **getParams** obtains only the parameters of the current page and does not clear the parameters associated with
> the page.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [getParams](arkts-arkui-arkui-uicontext-router-c.md#getparams)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Object | Parameters passed from the page that initiates redirection to the current page. |

**Examples**

```TypeScript
this.getUIContext().getRouter().getParams();
```
