# BLECharacteristic

Describes the Gatt characteristic.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of a BLECharacteristic instance

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [characteristicUuid](arkts-connectivity-ble-blecharacteristic-i.md#characteristicuuid)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## characteristicValue

```TypeScript
characteristicValue: ArrayBuffer
```

The value of a BLECharacteristic instance

**Type:** ArrayBuffer

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [characteristicValue](arkts-connectivity-ble-blecharacteristic-i.md#characteristicvalue)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## descriptors

```TypeScript
descriptors: Array<BLEDescriptor>
```

The list of [BLEDescriptor](arkts-connectivity-bluetoothmanager-bledescriptor-i.md) contained in the characteristic

**Type:** Array&lt;[BLEDescriptor](arkts-connectivity-bluetoothmanager-bledescriptor-i.md)&gt;

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [descriptors](arkts-connectivity-ble-blecharacteristic-i.md#descriptors)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the [GattService](arkts-connectivity-bluetoothmanager-gattservice-i.md) instance to which the characteristic belongs

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [serviceUuid](arkts-connectivity-ble-blecharacteristic-i.md#serviceuuid)

**System capability:** SystemCapability.Communication.Bluetooth.Core
