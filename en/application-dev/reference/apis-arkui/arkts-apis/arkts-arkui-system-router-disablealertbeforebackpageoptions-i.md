# DisableAlertBeforeBackPageOptions

Defines the **DisableAlertBeforeBackPage** parameter.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** RouterOptions

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SystemRouter, BackRouterOptions, DisableAlertBeforeBackPageOptions, EnableAlertBeforeBackPageOptions, RouterOptions, RouterState } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel?: (errMsg: string) => void
```

Called when the dialog box fails to be closed. **errMsg** indicates the returned information.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** RouterOptions

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| errMsg | string | Yes |  |

## complete

```TypeScript
complete?: () => void
```

Called when the dialog box is closed.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** RouterOptions

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## success

```TypeScript
success?: (errMsg: string) => void
```

Called when the dialog box is closed. **errMsg** indicates the returned information.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** RouterOptions

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| errMsg | string | Yes |  |
