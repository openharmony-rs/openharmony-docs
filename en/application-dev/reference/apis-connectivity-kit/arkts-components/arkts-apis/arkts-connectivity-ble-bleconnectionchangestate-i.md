# BLEConnectionChangeState

```TypeScript
interface BLEConnectionChangeState
```

Describes the Gatt profile connection state.

**Since:** 10

<!--Device-ble-interface BLEConnectionChangeState--><!--Device-ble-interface BLEConnectionChangeState-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

Indicates the peer device address

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-BLEConnectionChangeState-deviceId: string--><!--Device-BLEConnectionChangeState-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## reason

```TypeScript
reason?: GattDisconnectReason
```

Reason of the disconnection of the gatt connection.

**Type:** [GattDisconnectReason](arkts-connectivity-ble-gattdisconnectreason-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-BLEConnectionChangeState-reason?: GattDisconnectReason--><!--Device-BLEConnectionChangeState-reason?: GattDisconnectReason-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## reasonMessage

```TypeScript
reasonMessage?: string
```

Reason message of the disconnection of the gatt connection.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-BLEConnectionChangeState-reasonMessage?: string--><!--Device-BLEConnectionChangeState-reasonMessage?: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: ProfileConnectionState
```

Connection state of the Gatt profile

**Type:** [ProfileConnectionState](arkts-connectivity-ble-profileconnectionstate-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-BLEConnectionChangeState-state: ProfileConnectionState--><!--Device-BLEConnectionChangeState-state: ProfileConnectionState-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
