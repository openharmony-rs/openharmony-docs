# SubscribeBLEFoundOptions

**Since:** 6

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## Modules to Import

```TypeScript
import { Bluetooth, BLEFoundResponse, BluetoothDevice, StartBLEScanOptions, StopBLEScanOptions, SubscribeBLEFoundOptions } from '@kit.ConnectivityKit';
```

## fail

```TypeScript
fail: (data: string, code: number) => void
```

SubscribeBLEFoundOptions failed

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
success: (data: BLEFoundResponse) => void
```

SubscribeBLEFoundOptions success

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Communication.Bluetooth.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [BLEFoundResponse](arkts-connectivity-system-bluetooth-blefoundresponse-i.md) | Yes |  |
