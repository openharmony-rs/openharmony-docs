# clear

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## clear

```TypeScript
function clear(): void
```

Clears all historical pages in the stack and retains only the current page at the top of the stack.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [clear](arkts-arkui-arkui-uicontext-router-c.md#clear)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
this.getUIContext().getRouter().clear();
```
