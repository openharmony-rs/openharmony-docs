# BLECharacteristic

```TypeScript
interface BLECharacteristic
```

Describes the Gatt characteristic.

**Since:** 10

<!--Device-ble-interface BLECharacteristic--><!--Device-ble-interface BLECharacteristic-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of a BLECharacteristic instance

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-BLECharacteristic-characteristicUuid: string--><!--Device-BLECharacteristic-characteristicUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## characteristicValue

```TypeScript
characteristicValue: ArrayBuffer
```

The value of a BLECharacteristic instance

**Type:** ArrayBuffer

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-BLECharacteristic-characteristicValue: ArrayBuffer--><!--Device-BLECharacteristic-characteristicValue: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## characteristicValueHandle

```TypeScript
characteristicValueHandle?: number
```

The characteristic value handle of a BLECharacteristic instance

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-BLECharacteristic-characteristicValueHandle?: int--><!--Device-BLECharacteristic-characteristicValueHandle?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## descriptors

```TypeScript
descriptors: Array<BLEDescriptor>
```

The list of [BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md) contained in the characteristic

**Type:** Array&lt;[BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-BLECharacteristic-descriptors: Array<BLEDescriptor>--><!--Device-BLECharacteristic-descriptors: Array<BLEDescriptor>-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## permissions

```TypeScript
permissions?: GattPermissions
```

The permissions of a BLECharacteristic instance. The default value is Readable and Writable.

**Type:** [GattPermissions](arkts-connectivity-ble-gattpermissions-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-BLECharacteristic-permissions?: GattPermissions--><!--Device-BLECharacteristic-permissions?: GattPermissions-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## properties

```TypeScript
properties?: GattProperties
```

The properties of a BLECharacteristic instance

**Type:** [GattProperties](arkts-connectivity-ble-gattproperties-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-BLECharacteristic-properties?: GattProperties--><!--Device-BLECharacteristic-properties?: GattProperties-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the [GattService](arkts-connectivity-ble-gattservice-i.md) instance to which the characteristic belongs

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-BLECharacteristic-serviceUuid: string--><!--Device-BLECharacteristic-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
