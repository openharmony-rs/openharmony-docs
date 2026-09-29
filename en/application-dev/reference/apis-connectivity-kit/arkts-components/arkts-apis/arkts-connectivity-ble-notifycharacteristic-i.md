# NotifyCharacteristic

```TypeScript
interface NotifyCharacteristic
```

Describes the value of the indication or notification sent by the Gatt server.

**Since:** 10

<!--Device-ble-interface NotifyCharacteristic--><!--Device-ble-interface NotifyCharacteristic-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of a NotifyCharacteristic instance

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-NotifyCharacteristic-characteristicUuid: string--><!--Device-NotifyCharacteristic-characteristicUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## characteristicValue

```TypeScript
characteristicValue: ArrayBuffer
```

The value of a NotifyCharacteristic instance

**Type:** ArrayBuffer

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-NotifyCharacteristic-characteristicValue: ArrayBuffer--><!--Device-NotifyCharacteristic-characteristicValue: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## confirm

```TypeScript
confirm: boolean
```

Specifies whether to request confirmation from the BLE peripheral device (indication) or send a notification. Value `true` indicates the former and `false` indicates the latter.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-NotifyCharacteristic-confirm: boolean--><!--Device-NotifyCharacteristic-confirm: boolean-End-->

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

<!--Device-NotifyCharacteristic-serviceUuid: string--><!--Device-NotifyCharacteristic-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
