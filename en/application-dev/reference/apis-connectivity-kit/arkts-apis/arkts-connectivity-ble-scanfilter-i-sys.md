# ScanFilter

Describes the criteria for filtering scanning results can be set.

**Since:** 10

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## irk

```TypeScript
irk?: Uint8Array
```

Identity Resolving Key of BLE peripheral device. [irk](#irk) needs to be used with [address](arkts-connectivity-ble-scanfilter-i.md#address).

**Type:** Uint8Array

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.
