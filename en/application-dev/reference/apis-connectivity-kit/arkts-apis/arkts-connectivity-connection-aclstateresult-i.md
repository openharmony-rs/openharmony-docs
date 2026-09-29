# AclStateResult

```TypeScript
interface AclStateResult
```

Acl state change result.

**Since:** 26.0.0

<!--Device-connection-interface AclStateResult--><!--Device-connection-interface AclStateResult-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

The virtual address of a Bluetooth device. For example, "11:22:33:AA:BB:FF".

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AclStateResult-deviceId: string--><!--Device-AclStateResult-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: AclState
```

Acl state of the device.

**Type:** [AclState](arkts-connectivity-connection-aclstate-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AclStateResult-state: AclState--><!--Device-AclStateResult-state: AclState-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
