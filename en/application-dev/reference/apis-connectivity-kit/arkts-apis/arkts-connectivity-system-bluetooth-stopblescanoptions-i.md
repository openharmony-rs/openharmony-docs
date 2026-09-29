# StopBLEScanOptions

```TypeScript
export interface StopBLEScanOptions
```

**Since:** 6

<!--Device-unnamed-export interface StopBLEScanOptions--><!--Device-unnamed-export interface StopBLEScanOptions-End-->

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

<!--Device-StopBLEScanOptions-complete: () => void--><!--Device-StopBLEScanOptions-complete: () => void-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## fail

```TypeScript
fail: (data: string, code: number) => void
```

StopBLEScanOptions failed

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-StopBLEScanOptions-fail: (data: string, code: number) => void--><!--Device-StopBLEScanOptions-fail: (data: string, code: number) => void-End-->

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

<!--Device-StopBLEScanOptions-success: () => void--><!--Device-StopBLEScanOptions-success: () => void-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Lite
