# GattService

Describes the Gatt service.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [GattService](arkts-connectivity-ble-gattservice-i.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## characteristics

```TypeScript
characteristics: Array<BLECharacteristic>
```

The [BLECharacteristic](arkts-connectivity-bluetoothmanager-blecharacteristic-i.md) list belongs to this GattService instance

**Type:** Array&lt;[BLECharacteristic](arkts-connectivity-bluetoothmanager-blecharacteristic-i.md)&gt;

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [characteristics](arkts-connectivity-ble-gattservice-i.md#characteristics)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## includeServices

```TypeScript
includeServices?: Array<GattService>
```

The list of GATT services contained in the service

**Type:** Array&lt;[GattService](arkts-connectivity-bluetoothmanager-gattservice-i.md)&gt;

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [includeServices](arkts-connectivity-ble-gattservice-i.md#includeservices)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## isPrimary

```TypeScript
isPrimary: boolean
```

Indicates whether the GattService instance is primary or secondary.

**Type:** boolean

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [isPrimary](arkts-connectivity-ble-gattservice-i.md#isprimary)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of a GattService instance

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [serviceUuid](arkts-connectivity-ble-gattservice-i.md#serviceuuid)

**System capability:** SystemCapability.Communication.Bluetooth.Core
