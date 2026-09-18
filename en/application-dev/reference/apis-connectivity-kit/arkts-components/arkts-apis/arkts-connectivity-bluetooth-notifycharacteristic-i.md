# NotifyCharacteristic

Describes the value of the indication or notification sent by the Gatt server.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [NotifyCharacteristic](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of a NotifyCharacteristic instance

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [characteristicUuid](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md#characteristicuuid)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## characteristicValue

```TypeScript
characteristicValue: ArrayBuffer
```

The value of a NotifyCharacteristic instance

**Type:** ArrayBuffer

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [characteristicValue](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md#characteristicvalue)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## confirm

```TypeScript
confirm: boolean
```

Specifies whether to request confirmation from the BLE peripheral device (indication) or send a notification. Value `true` indicates the former and `false` indicates the latter.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [confirm](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md#confirm)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the [GattService](arkts-connectivity-bluetooth-gattservice-i.md) instance to which the characteristic belongs

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [serviceUuid](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md#serviceuuid)

**System capability:** SystemCapability.Communication.Bluetooth.Core
