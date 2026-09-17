# EnableAlertBeforeBackPageOptions

Defines the **EnableAlertBeforeBackPage** parameter.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SystemRouter, BackRouterOptions, DisableAlertBeforeBackPageOptions, EnableAlertBeforeBackPageOptions, RouterOptions, RouterState } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel?: (errMsg: string) => void
```

Called when the **Cancel** button in the confirm dialog box is clicked. **errMsg** indicates the returned information.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md)

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

**Substitutes:** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## success

```TypeScript
success?: (errMsg: string) => void
```

Called when the **OK** button in the confirm dialog box is clicked. **errMsg** indicates the returned information.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| errMsg | string | Yes |  |

## message

```TypeScript
message: string
```

Content displayed in the confirm dialog box.

**Type:** string

**Since:** 6

**Deprecated since:** 8

**Substitutes:** message

**System capability:** SystemCapability.ArkUI.ArkUI.Full
