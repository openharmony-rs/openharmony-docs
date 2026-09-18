# NotifyCharacteristic

Describes the value of the indication or notification sent by the Gatt server.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [NotifyCharacteristic](arkts-connectivity-ble-notifycharacteristic-i.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of a NotifyCharacteristic instance

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [characteristicUuid](arkts-connectivity-ble-notifycharacteristic-i.md#characteristicuuid)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## characteristicValue

```TypeScript
characteristicValue: ArrayBuffer
```

The value of a NotifyCharacteristic instance

**Type:** ArrayBuffer

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [characteristicValue](arkts-connectivity-ble-notifycharacteristic-i.md#characteristicvalue)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## confirm

```TypeScript
confirm: boolean
```

Specifies whether to request confirmation from the BLE peripheral device (indication) or send a notification. Value `true` indicates the former and `false` indicates the latter.

**Type:** boolean

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [confirm](arkts-connectivity-ble-notifycharacteristic-i.md#confirm)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the [GattService](arkts-connectivity-bluetoothmanager-gattservice-i.md) instance to which the characteristic belongs

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [serviceUuid](arkts-connectivity-ble-notifycharacteristic-i.md#serviceuuid)

**System capability:** SystemCapability.Communication.Bluetooth.Core
