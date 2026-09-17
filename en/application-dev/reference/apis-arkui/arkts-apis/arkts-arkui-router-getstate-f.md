# getState

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## getState

```TypeScript
function getState(): RouterState
```

Obtains state information about the page at the top of the navigation stack.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [getState](arkts-arkui-arkui-uicontext-router-c.md#getstate)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [RouterState](arkts-arkui-router-routerstate-i.md) | Page routing state. |

**Examples**

```TypeScript
let page = this.getUIContext().getRouter().getState();
console.info('current index = ' + page.index);
console.info('current name = ' + page.name);
console.info('current path = ' + page.path);
```
