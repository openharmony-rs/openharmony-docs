# BLEDescriptor

```TypeScript
interface BLEDescriptor
```

Describes the Gatt descriptor.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [BLEDescriptor](arkts-connectivity-bluetoothmanager-bledescriptor-i.md)

<!--Device-bluetooth-interface BLEDescriptor--><!--Device-bluetooth-interface BLEDescriptor-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of the [BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md) instance to which the descriptor belongs

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [characteristicUuid](arkts-connectivity-bluetoothmanager-bledescriptor-i.md#characteristicuuid)

<!--Device-BLEDescriptor-characteristicUuid: string--><!--Device-BLEDescriptor-characteristicUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## descriptorUuid

```TypeScript
descriptorUuid: string
```

The UUID of the BLEDescriptor instance

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [descriptorUuid](arkts-connectivity-bluetoothmanager-bledescriptor-i.md#descriptoruuid)

<!--Device-BLEDescriptor-descriptorUuid: string--><!--Device-BLEDescriptor-descriptorUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## descriptorValue

```TypeScript
descriptorValue: ArrayBuffer
```

The value of the BLEDescriptor instance

**Type:** ArrayBuffer

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [descriptorValue](arkts-connectivity-bluetoothmanager-bledescriptor-i.md#descriptorvalue)

<!--Device-BLEDescriptor-descriptorValue: ArrayBuffer--><!--Device-BLEDescriptor-descriptorValue: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the [GattService](arkts-connectivity-bluetooth-gattservice-i.md) instance to which the descriptor belongs

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [serviceUuid](arkts-connectivity-bluetoothmanager-bledescriptor-i.md#serviceuuid)

<!--Device-BLEDescriptor-serviceUuid: string--><!--Device-BLEDescriptor-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
