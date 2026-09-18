# BackRouterOptions

Defines the parameters for routing back.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** RouterOptions

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SystemRouter, BackRouterOptions, DisableAlertBeforeBackPageOptions, EnableAlertBeforeBackPageOptions, RouterOptions, RouterState } from '@kit.ArkUI';
```

## params

```TypeScript
params?: Object
```

Data that needs to be passed to the target page during redirection.

**Type:** Object

**Since:** 7

**Deprecated since:** 8

**Substitutes:** params

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## uri

```TypeScript
uri?: string
```

URI of the page to return to. If the specified page does not exist in the page stack, the application does not respond. If this parameter is not set, the application returns to the previous page.

**Type:** string

**Since:** 7

**Deprecated since:** 8

**Substitutes:** url

**System capability:** SystemCapability.ArkUI.ArkUI.Full
