# getStateByUrl

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## getStateByUrl

```TypeScript
function getStateByUrl(url: string): Array<RouterState>
```

Obtains the status information about a page by its URL.

> **NOTE:** 
> 
> - Since API version 12, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 12

**Deprecated since:** 18

**Substitutes:** [getStateByUrl](arkts-arkui-arkui-uicontext-router-c.md#getstatebyurl)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the target page. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[RouterState](arkts-arkui-router-routerstate-i.md)&gt; | Page routing state. |

**Examples**

```TypeScript
import { router } from '@kit.ArkUI';

let options: Array<router.RouterState> = router.getStateByUrl('pages/index');
for (let i: number = 0; i < options.length; i++) {
  console.info('index = ' + options[i].index);
  console.info('name = ' + options[i].name);
  console.info('path = ' + options[i].path);
  console.info('params = ' + options[i].params);
}
```
