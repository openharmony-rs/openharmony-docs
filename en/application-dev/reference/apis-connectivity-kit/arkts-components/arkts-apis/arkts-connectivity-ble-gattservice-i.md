# GattService

```TypeScript
interface GattService
```

Describes the Gatt service.

**Since:** 10

<!--Device-ble-interface GattService--><!--Device-ble-interface GattService-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## characteristics

```TypeScript
characteristics: Array<BLECharacteristic>
```

The [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) list belongs to this GattService instance

**Type:** Array&lt;[BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GattService-characteristics: Array<BLECharacteristic>--><!--Device-GattService-characteristics: Array<BLECharacteristic>-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## includeServices

```TypeScript
includeServices?: Array<GattService>
```

The list of GATT services contained in the service

**Type:** Array&lt;[GattService](arkts-connectivity-ble-gattservice-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GattService-includeServices?: Array<GattService>--><!--Device-GattService-includeServices?: Array<GattService>-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## isPrimary

```TypeScript
isPrimary: boolean
```

Indicates whether the GattService instance is primary or secondary.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GattService-isPrimary: boolean--><!--Device-GattService-isPrimary: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of a GattService instance

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GattService-serviceUuid: string--><!--Device-GattService-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
