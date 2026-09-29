# BLEConnectChangedState

```TypeScript
interface BLEConnectChangedState
```

Describes the Gatt profile connection state.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [BLEConnectChangedState](arkts-connectivity-bluetoothmanager-bleconnectchangedstate-i.md)

<!--Device-bluetooth-interface BLEConnectChangedState--><!--Device-bluetooth-interface BLEConnectChangedState-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

Indicates the peer device address

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [deviceId](arkts-connectivity-bluetoothmanager-bleconnectchangedstate-i.md#deviceid)

<!--Device-BLEConnectChangedState-deviceId: string--><!--Device-BLEConnectChangedState-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: ProfileConnectionState
```

Connection state of the Gatt profile

**Type:** [ProfileConnectionState](arkts-connectivity-bluetooth-profileconnectionstate-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [state](arkts-connectivity-bluetoothmanager-bleconnectchangedstate-i.md#state)

<!--Device-BLEConnectChangedState-state: ProfileConnectionState--><!--Device-BLEConnectChangedState-state: ProfileConnectionState-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
