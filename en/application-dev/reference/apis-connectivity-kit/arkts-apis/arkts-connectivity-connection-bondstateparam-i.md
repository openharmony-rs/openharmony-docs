# BondStateParam

```TypeScript
interface BondStateParam
```

Describes the class of a bluetooth device.

**Since:** 10

<!--Device-connection-interface BondStateParam--><!--Device-connection-interface BondStateParam-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## cause

```TypeScript
cause: UnbondCause
```

Cause of unbond.

**Type:** [UnbondCause](arkts-connectivity-connection-unbondcause-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-BondStateParam-cause: UnbondCause--><!--Device-BondStateParam-cause: UnbondCause-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## causeMessage

```TypeScript
causeMessage?: string
```

Cause message of unbond.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BondStateParam-causeMessage?: string--><!--Device-BondStateParam-causeMessage?: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

Address of a Bluetooth device.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-BondStateParam-deviceId: string--><!--Device-BondStateParam-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: BondState
```

Profile connection state of the device.

**Type:** [BondState](arkts-connectivity-connection-bondstate-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-BondStateParam-state: BondState--><!--Device-BondStateParam-state: BondState-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
