# StateChangeParam

Profile state change parameters.

**Since:** 10

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { baseProfile } from '@kit.ConnectivityKit';
```

## cause

```TypeScript
cause: DisconnectCause
```

Cause of disconnect

**Type:** [DisconnectCause](arkts-connectivity-baseprofile-disconnectcause-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

The address of device

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## role

```TypeScript
role?: PanRole
```

PAN role of the device

**Type:** [PanRole](arkts-connectivity-baseprofile-panrole-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: ProfileConnectionState
```

Profile state value

**Type:** [ProfileConnectionState](arkts-connectivity-baseprofile-profileconnectionstate-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core
