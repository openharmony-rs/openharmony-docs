# BluetoothDevice

```TypeScript
export interface BluetoothDevice
```

**Since:** 6

<!--Device-unnamed-export interface BluetoothDevice--><!--Device-unnamed-export interface BluetoothDevice-End-->

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

<!--Device-BluetoothDevice-addr: string--><!--Device-BluetoothDevice-addr: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## addrType

```TypeScript
addrType: 'public' | 'random'
```

The addrType of address, may be public or random

**Type:** 'public' &#124; 'random'

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-BluetoothDevice-addrType: 'public' | 'random'--><!--Device-BluetoothDevice-addrType: 'public' | 'random'-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## data

```TypeScript
data: string
```

The data of BluetoothDevice

**Type:** string

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-BluetoothDevice-data: string--><!--Device-BluetoothDevice-data: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## rssi

```TypeScript
rssi: number
```

RSSI of the remote device

**Type:** number

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-BluetoothDevice-rssi: number--><!--Device-BluetoothDevice-rssi: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Lite

## txpower

```TypeScript
txpower: string
```

Transmission power level for advertising

**Type:** string

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-BluetoothDevice-txpower: string--><!--Device-BluetoothDevice-txpower: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Lite
