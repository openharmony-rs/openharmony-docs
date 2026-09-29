# ScanFilter

```TypeScript
interface ScanFilter
```

Describes the criteria for filtering scanning results can be set.

**Since:** 10

<!--Device-ble-interface ScanFilter--><!--Device-ble-interface ScanFilter-End-->

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

<!--Device-ScanFilter-address?: BluetoothAddress--><!--Device-ScanFilter-address?: BluetoothAddress-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId?: string
```

The address of a BLE peripheral device

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanFilter-deviceId?: string--><!--Device-ScanFilter-deviceId?: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## manufactureData

```TypeScript
manufactureData?: ArrayBuffer
```

Manufacture data.

**Type:** ArrayBuffer

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanFilter-manufactureData?: ArrayBuffer--><!--Device-ScanFilter-manufactureData?: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## manufactureDataMask

```TypeScript
manufactureDataMask?: ArrayBuffer
```

Manufacture data mask.

**Type:** ArrayBuffer

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanFilter-manufactureDataMask?: ArrayBuffer--><!--Device-ScanFilter-manufactureDataMask?: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## manufactureId

```TypeScript
manufactureId?: number
```

Manufacture id.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanFilter-manufactureId?: int--><!--Device-ScanFilter-manufactureId?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## name

```TypeScript
name?: string
```

The name of a BLE peripheral device

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanFilter-name?: string--><!--Device-ScanFilter-name?: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## rssiThreshold

```TypeScript
rssiThreshold?: number
```

RSSI threshold for filtering advertising that pass through.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-ScanFilter-rssiThreshold?: int--><!--Device-ScanFilter-rssiThreshold?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceData

```TypeScript
serviceData?: ArrayBuffer
```

Service data.

**Type:** ArrayBuffer

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanFilter-serviceData?: ArrayBuffer--><!--Device-ScanFilter-serviceData?: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceDataMask

```TypeScript
serviceDataMask?: ArrayBuffer
```

Service data mask.

**Type:** ArrayBuffer

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanFilter-serviceDataMask?: ArrayBuffer--><!--Device-ScanFilter-serviceDataMask?: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceSolicitationUuid

```TypeScript
serviceSolicitationUuid?: string
```

Service solicitation UUID.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanFilter-serviceSolicitationUuid?: string--><!--Device-ScanFilter-serviceSolicitationUuid?: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceSolicitationUuidMask

```TypeScript
serviceSolicitationUuidMask?: string
```

Service solicitation UUID mask.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanFilter-serviceSolicitationUuidMask?: string--><!--Device-ScanFilter-serviceSolicitationUuidMask?: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid?: string
```

The service UUID of a BLE peripheral device

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanFilter-serviceUuid?: string--><!--Device-ScanFilter-serviceUuid?: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuidMask

```TypeScript
serviceUuidMask?: string
```

Service UUID mask.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanFilter-serviceUuidMask?: string--><!--Device-ScanFilter-serviceUuidMask?: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
