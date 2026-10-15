# getStateByIndex

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## getStateByIndex

```TypeScript
function getStateByIndex(index: number): RouterState | undefined
```

Obtains the status information about a page by its index.

> **NOTE:** 
> 
> - Since API version 12, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 12

**Deprecated since:** 18

**Substitutes:** [getStateByIndex](arkts-arkui-arkui-uicontext-router-c.md#getstatebyindex)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-router-function getStateByIndex(index: number): RouterState | undefined--><!--Device-router-function getStateByIndex(index: number): RouterState | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the page to obtain. The value range is [1, Page stack size], and the maximum page stack size is 32. The index starts from 1 from the bottom to the top of the stack. If the index does not exist, **undefined** is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [RouterState](arkts-arkui-router-routerstate-i.md) &#124; undefined | State of the page at the corresponding index, including the page index, name, path, and parameters. **undefined** is returned if the index does not exist. |

**Examples**

```TypeScript
import { router } from '@kit.ArkUI';

let options: router.RouterState | undefined = router.getStateByIndex(1);
if (options != undefined) {
  console.info('index = ' + options.index);
  console.info('name = ' + options.name);
  console.info('path = ' + options.path);
  console.info(`params = ${JSON.stringify(options.params)}`);
}
```
