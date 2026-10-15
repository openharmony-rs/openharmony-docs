# BackRouterOptions

```TypeScript
export interface BackRouterOptions
```

Defines the parameters for routing back.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [RouterOptions](arkts-arkui-router-routeroptions-i.md)

<!--Device-unnamed-export interface BackRouterOptions--><!--Device-unnamed-export interface BackRouterOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SystemRouter, BackRouterOptions, DisableAlertBeforeBackPageOptions, EnableAlertBeforeBackPageOptions, RouterOptions, RouterState } from '@kit.ArkUI';
```

## params

```TypeScript
params?: Object
```

Data to be passed to the target page when the page is returned.

**Type:** Object

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [params](arkts-arkui-router-routeroptions-i.md#params)

<!--Device-BackRouterOptions-params?: Object--><!--Device-BackRouterOptions-params?: Object-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## uri

```TypeScript
uri?: string
```

URI of the page to return to. If the specified page does not exist in the page stack, the application does not respond. If this parameter is not set, the application returns to the previous page.

**Type:** string

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [url](arkts-arkui-router-routeroptions-i.md#url)

<!--Device-BackRouterOptions-uri?: string--><!--Device-BackRouterOptions-uri?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
