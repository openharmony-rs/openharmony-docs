# BondStateParam

```TypeScript
interface BondStateParam
```

Describes the class of a bluetooth device.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [BondStateParam](arkts-connectivity-connection-bondstateparam-i.md)

<!--Device-bluetoothManager-interface BondStateParam--><!--Device-bluetoothManager-interface BondStateParam-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

Address of a Bluetooth device.

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [deviceId](arkts-connectivity-connection-bondstateparam-i.md#deviceid)

<!--Device-BondStateParam-deviceId: string--><!--Device-BondStateParam-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: BondState
```

Profile connection state of the device.

**Type:** [BondState](arkts-connectivity-bluetoothmanager-bondstate-e.md)

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [state](arkts-connectivity-connection-bondstateparam-i.md#state)

<!--Device-BondStateParam-state: BondState--><!--Device-BondStateParam-state: BondState-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
