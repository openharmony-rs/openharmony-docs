# getLength

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## getLength

```TypeScript
function getLength(): string
```

Obtains the number of pages in the current stack.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [getLength](arkts-arkui-arkui-uicontext-router-c.md#getlength)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Number of pages in the stack. The maximum value is **32**. |

**Examples**

```TypeScript
let size = this.getUIContext().getRouter().getLength();
console.info('pages stack size = ' + size);
```
