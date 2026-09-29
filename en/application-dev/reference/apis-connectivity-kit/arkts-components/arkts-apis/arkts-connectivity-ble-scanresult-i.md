# ScanResult

```TypeScript
interface ScanResult
```

Describes the contents of the scan results.

**Since:** 10

<!--Device-ble-interface ScanResult--><!--Device-ble-interface ScanResult-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address?: BluetoothAddress
```

The address object of a BLE peripheral device, including the address type.

**Type:** [BluetoothAddress](arkts-connectivity-ble-bluetoothaddress-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-ScanResult-address?: BluetoothAddress--><!--Device-ScanResult-address?: BluetoothAddress-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## advertiseFlags

```TypeScript
advertiseFlags?: number
```

This field is used to identify the discovery mode and supported capabilities of the peer device.

**Type:** number

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ScanResult-advertiseFlags?: int--><!--Device-ScanResult-advertiseFlags?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## advertisingDataMap

```TypeScript
advertisingDataMap?: Map<number, Uint8Array>
```

Map of advertising data fields.

**Type:** Map&lt;number, Uint8Array&gt;

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ScanResult-advertisingDataMap?: Map<int, Uint8Array>--><!--Device-ScanResult-advertisingDataMap?: Map<int, Uint8Array>-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## connectable

```TypeScript
connectable: boolean
```

Connectable of the remote device

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanResult-connectable: boolean--><!--Device-ScanResult-connectable: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## data

```TypeScript
data: ArrayBuffer
```

The raw data of broadcast packet

**Type:** ArrayBuffer

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanResult-data: ArrayBuffer--><!--Device-ScanResult-data: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

Address of the scanned device

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanResult-deviceId: string--><!--Device-ScanResult-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceName

```TypeScript
deviceName: string
```

The local name of the BLE device

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanResult-deviceName: string--><!--Device-ScanResult-deviceName: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## manufacturerDataMap

```TypeScript
manufacturerDataMap?: Map<number, Uint8Array>
```

Map of manufacturer data.

**Type:** Map&lt;number, Uint8Array&gt;

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ScanResult-manufacturerDataMap?: Map<int, Uint8Array>--><!--Device-ScanResult-manufacturerDataMap?: Map<int, Uint8Array>-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## rssi

```TypeScript
rssi: number
```

RSSI of the remote device

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanResult-rssi: int--><!--Device-ScanResult-rssi: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceDataMap

```TypeScript
serviceDataMap?: Map<string, Uint8Array>
```

Map of service data.

**Type:** Map&lt;string, Uint8Array&gt;

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ScanResult-serviceDataMap?: Map<string, Uint8Array>--><!--Device-ScanResult-serviceDataMap?: Map<string, Uint8Array>-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuids

```TypeScript
serviceUuids?: string[]
```

The list of service uuid.

**Type:** string[]

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ScanResult-serviceUuids?: string[]--><!--Device-ScanResult-serviceUuids?: string[]-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## txPowerLevel

```TypeScript
txPowerLevel?: number
```

The tx power level of the packet in dBm.

**Type:** number

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ScanResult-txPowerLevel?: int--><!--Device-ScanResult-txPowerLevel?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
