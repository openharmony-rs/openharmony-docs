# StopBLEScanOptions

**Since:** 6

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## Modules to Import

```TypeScript
import { Bluetooth, BLEFoundResponse, BluetoothDevice, StartBLEScanOptions, StopBLEScanOptions, SubscribeBLEFoundOptions } from '@kit.ConnectivityKit';
```

## complete

```TypeScript
complete: () => void
```

StopBLEScanOptions completed

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## fail

```TypeScript
fail: (data: string, code: number) => void
```

StopBLEScanOptions failed

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Communication.Bluetooth.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success: () => void
```

StopBLEScanOptions success

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Communication.Bluetooth.Lite
