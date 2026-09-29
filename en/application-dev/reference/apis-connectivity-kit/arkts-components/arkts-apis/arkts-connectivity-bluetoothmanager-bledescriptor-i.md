# BLEDescriptor

```TypeScript
interface BLEDescriptor
```

Describes the Gatt descriptor.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md)

<!--Device-bluetoothManager-interface BLEDescriptor--><!--Device-bluetoothManager-interface BLEDescriptor-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of the [BLECharacteristic](arkts-connectivity-bluetoothmanager-blecharacteristic-i.md) instance to which the descriptor belongs

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [characteristicUuid](arkts-connectivity-ble-bledescriptor-i.md#characteristicuuid)

<!--Device-BLEDescriptor-characteristicUuid: string--><!--Device-BLEDescriptor-characteristicUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## descriptorUuid

```TypeScript
descriptorUuid: string
```

The UUID of the BLEDescriptor instance

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [descriptorUuid](arkts-connectivity-ble-bledescriptor-i.md#descriptoruuid)

<!--Device-BLEDescriptor-descriptorUuid: string--><!--Device-BLEDescriptor-descriptorUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## descriptorValue

```TypeScript
descriptorValue: ArrayBuffer
```

The value of the BLEDescriptor instance

**Type:** ArrayBuffer

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [descriptorValue](arkts-connectivity-ble-bledescriptor-i.md#descriptorvalue)

<!--Device-BLEDescriptor-descriptorValue: ArrayBuffer--><!--Device-BLEDescriptor-descriptorValue: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the [GattService](arkts-connectivity-bluetoothmanager-gattservice-i.md) instance to which the descriptor belongs

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [serviceUuid](arkts-connectivity-ble-bledescriptor-i.md#serviceuuid)

<!--Device-BLEDescriptor-serviceUuid: string--><!--Device-BLEDescriptor-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
