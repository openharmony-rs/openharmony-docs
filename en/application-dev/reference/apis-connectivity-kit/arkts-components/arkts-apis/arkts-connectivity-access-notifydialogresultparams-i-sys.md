# NotifyDialogResultParams (System API)

```TypeScript
interface NotifyDialogResultParams
```

Describes the result of bluetooth dialog.

**Since:** 20

<!--Device-access-interface NotifyDialogResultParams--><!--Device-access-interface NotifyDialogResultParams-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## dialogResult

```TypeScript
dialogResult: boolean
```

The result of bluetooth dialog. The value true indicates that the user approves the request, and the value false indicates that the user rejects the request.

**Type:** boolean

**Since:** 20

<!--Device-NotifyDialogResultParams-dialogResult: boolean--><!--Device-NotifyDialogResultParams-dialogResult: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## dialogType

```TypeScript
dialogType: DialogType
```

The type of bluetooth dialog.

**Type:** [DialogType](arkts-connectivity-access-dialogtype-e-sys.md)

**Since:** 20

<!--Device-NotifyDialogResultParams-dialogType: DialogType--><!--Device-NotifyDialogResultParams-dialogType: DialogType-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.
