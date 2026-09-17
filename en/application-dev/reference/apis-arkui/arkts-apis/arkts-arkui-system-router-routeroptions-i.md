# RouterOptions

Defines the page routing parameters.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** RouterOptions

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## Modules to Import

```TypeScript
import { SystemRouter, BackRouterOptions, DisableAlertBeforeBackPageOptions, EnableAlertBeforeBackPageOptions, RouterOptions, RouterState } from '@kit.ArkUI';
```

## params

```TypeScript
params?: Object
```

Data that needs to be passed to the target page during redirection. The target page can use **router.getParams()** to obtain the passed parameters, for example, **this.keyValue** (**keyValue** is the value of a key in **params**). In the web-like paradigm, these parameters can be directly used on the target page. If the field specified by **key** already exists on the target page, the passed value of the key will be displayed.

**Type:** Object

**Since:** 3

**Deprecated since:** 8

**Substitutes:** params

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## uri

```TypeScript
uri: string
```

URI of the target page, in either of the following formats:

1. Absolute path, which is provided by the page list in the **config.json** file. Examples:

- pages/index/index  
- pages/detail/detail

2. Specific path. If the URI is a slash (/), the home page is displayed.

**Type:** string

**Since:** 3

**Deprecated since:** 8

**Substitutes:** url

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
