# replace

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## replace

```TypeScript
function replace(options: RouterOptions): void
```

Replaces the current page with another one in the application and destroys the current page.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [replaceUrl](arkts-arkui-arkui-uicontext-router-c.md#replaceurl-1)(options: router.RouterOptions)

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | Yes | Description of the new page. |

**Examples**

replace(options: RouterOptions): void

Replaces the current page with a page within the application and destroys the current page. Page transition animation is not supported. If you need to set the animation, you are advised to use the [Navigation](../../../ui/arkts-navigation-architecture.md) component.

> NOTE
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use replaceUrl(options: router.RouterOptions) instead.

System capability: SystemCapability.ArkUI.ArkUI.Lite

Parameters

```TypeScript
import { router } from '@kit.ArkUI';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replace({
  url: 'pages/detail',
  params: new RouterParams('message')
});
```
