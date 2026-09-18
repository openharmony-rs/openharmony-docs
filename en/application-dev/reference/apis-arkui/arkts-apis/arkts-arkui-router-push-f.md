# push

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## push

```TypeScript
function push(options: RouterOptions): void
```

Navigates to a specified page in the application.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [pushUrl](arkts-arkui-arkui-uicontext-router-c.md#pushurl)(options: router.RouterOptions)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | Yes | Page routing parameters. |

**Examples**

```TypeScript
push(options: RouterOptions): void

Navigates to a specified page in the application.

> NOTE
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use pushUrl(options: router.RouterOptions) instead.

System capability: SystemCapability.ArkUI.ArkUI.Full

Parameters
```
