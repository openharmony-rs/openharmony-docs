# BluetoothDevice

**Since:** 6

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## Modules to Import

```TypeScript
import { Bluetooth, BLEFoundResponse, BluetoothDevice, StartBLEScanOptions, StopBLEScanOptions, SubscribeBLEFoundOptions } from '@kit.ConnectivityKit';
```

## addr

```TypeScript
addr: string
```

Address of BluetoothDevice

**Type:** string

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## addrType

```TypeScript
addrType: 'public' | 'random'
```

The addrType of address, may be public or random

**Type:** 'public' &#124; 'random'

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## data

```TypeScript
data: string
```

The data of BluetoothDevice

**Type:** string

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## rssi

```TypeScript
rssi: number
```

RSSI of the remote device

**Type:** number

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## txpower

```TypeScript
txpower: string
```

Transmission power level for advertising

**Type:** string

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Communication.Bluetooth.Lite
