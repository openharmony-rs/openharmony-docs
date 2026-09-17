# getBtConnectionState

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getBtConnectionState

```TypeScript
function getBtConnectionState(): ProfileConnectionState
```

Get the local device connection state to any profile of any remote device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getBtConnectionState](arkts-connectivity-bluetoothmanager-getbtconnectionstate-f.md)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ProfileConnectionState](arkts-connectivity-bluetooth-profileconnectionstate-e.md) | One of [STATE_DISCONNECTED](arkts-connectivity-bluetooth-profileconnectionstate-e.md#state_disconnected), [STATE_CONNECTING](arkts-connectivity-bluetooth-profileconnectionstate-e.md#state_connecting), [STATE_CONNECTED](arkts-connectivity-bluetooth-profileconnectionstate-e.md#state_connected), [STATE_DISCONNECTING](arkts-connectivity-bluetooth-profileconnectionstate-e.md#state_disconnecting). |

**Examples**

```TypeScript
let connectionState : bluetooth.ProfileConnectionState = bluetooth.getBtConnectionState();
```
