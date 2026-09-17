# GattService

Describes the Gatt service.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [GattService](arkts-connectivity-bluetoothmanager-gattservice-i.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## characteristics

```TypeScript
characteristics: Array<BLECharacteristic>
```

The [BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md) list belongs to this GattService instance

**Type:** Array&lt;[BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md)&gt;

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [characteristics](arkts-connectivity-bluetoothmanager-gattservice-i.md#characteristics)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## includeServices

```TypeScript
includeServices?: Array<GattService>
```

The list of GATT services contained in the service

**Type:** Array&lt;[GattService](arkts-connectivity-bluetooth-gattservice-i.md)&gt;

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [includeServices](arkts-connectivity-bluetoothmanager-gattservice-i.md#includeservices)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## isPrimary

```TypeScript
isPrimary: boolean
```

Indicates whether the GattService instance is primary or secondary.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isPrimary](arkts-connectivity-bluetoothmanager-gattservice-i.md#isprimary)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of a GattService instance

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [serviceUuid](arkts-connectivity-bluetoothmanager-gattservice-i.md#serviceuuid)

**System capability:** SystemCapability.Communication.Bluetooth.Core
