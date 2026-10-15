# EnableAlertBeforeBackPageOptions

```TypeScript
export interface EnableAlertBeforeBackPageOptions
```

Defines the **EnableAlertBeforeBackPage** parameter.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md)

<!--Device-unnamed-export interface EnableAlertBeforeBackPageOptions--><!--Device-unnamed-export interface EnableAlertBeforeBackPageOptions-End-->

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

<!--Device-EnableAlertBeforeBackPageOptions-cancel?: (errMsg: string) => void--><!--Device-EnableAlertBeforeBackPageOptions-cancel?: (errMsg: string) => void-End-->

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

<!--Device-EnableAlertBeforeBackPageOptions-complete?: () => void--><!--Device-EnableAlertBeforeBackPageOptions-complete?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## success

```TypeScript
success?: (errMsg: string) => void
```

Called when the **OK** button in the confirm dialog box is clicked. **errMsg** indicates the returned information.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md)

<!--Device-EnableAlertBeforeBackPageOptions-success?: (errMsg: string) => void--><!--Device-EnableAlertBeforeBackPageOptions-success?: (errMsg: string) => void-End-->

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

**Substitutes:** [message](arkts-arkui-router-enablealertoptions-i.md#message)

<!--Device-EnableAlertBeforeBackPageOptions-message: string--><!--Device-EnableAlertBeforeBackPageOptions-message: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
