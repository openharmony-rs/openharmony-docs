# Router

The **Router** module provides APIs to access pages through URIs.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [router](arkts-arkui-router.md)

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## Modules to Import

```TypeScript
import { SystemRouter, BackRouterOptions, DisableAlertBeforeBackPageOptions, EnableAlertBeforeBackPageOptions, RouterOptions, RouterState } from '@kit.ArkUI';
```

## back

```TypeScript
static back(options?: BackRouterOptions): void
```

Returns to the previous or a specified page.

> **NOTE:** 
> 
> In the example, the **uri** field indicates the page route, which is specified by the **pages** list in the
> configuration file.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** back

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [BackRouterOptions](arkts-arkui-system-router-backrouteroptions-i.md) | No | For details, see **BackRouterOptions**. |

## clear

```TypeScript
static clear(): void
```

Clears all historical pages in the stack and retains only the current page at the top of the stack.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** clear

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disableAlertBeforeBackPage

```TypeScript
static disableAlertBeforeBackPage(options?: DisableAlertBeforeBackPageOptions): void
```

Disables the display of a confirm dialog box before returning to the previous page.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** hideAlertBeforeBackPage

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DisableAlertBeforeBackPageOptions](arkts-arkui-system-router-disablealertbeforebackpageoptions-i.md) | No | For details, see **DisableAlertBeforeBackPageOptions**. |

## enableAlertBeforeBackPage

```TypeScript
static enableAlertBeforeBackPage(options: EnableAlertBeforeBackPageOptions): void
```

Enables the display of a confirm dialog box before returning to the previous page.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** showAlertBeforeBackPage

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EnableAlertBeforeBackPageOptions](arkts-arkui-system-router-enablealertbeforebackpageoptions-i.md) | Yes | For details, see **EnableAlertBeforeBackPageOptions**. |

## getLength

```TypeScript
static getLength(): string
```

Obtains the number of pages in the current stack.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** getLength

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Number of pages in the stack. The maximum value is **32**. |

## getParams

```TypeScript
static getParams(): ParamsInterface
```

Obtains parameter information about the current page.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** getParams

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ParamsInterface](arkts-arkui-paramsinterface-t.md) | For details, see **ParamsInterface**. |

## getState

```TypeScript
static getState(): RouterState
```

Obtains state information about the current page.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** getState

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [RouterState](arkts-arkui-system-router-routerstate-i.md) | For details, see **RouterState**. |

## push

```TypeScript
static push(options: RouterOptions): void
```

Navigates to a specified page in the application.

> **NOTE:** 
> 
> The page routing stack supports a maximum of 32 pages.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** push

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-system-router-routeroptions-i.md) | Yes | Page routing parameters. For details, see **RouterOptions**. |

## replace

```TypeScript
static replace(options: RouterOptions): void
```

Replaces the current page with another one in the application and destroys the current page.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** replace

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-system-router-routeroptions-i.md) | Yes | Page routing parameters. For details, see **RouterOptions**. |
