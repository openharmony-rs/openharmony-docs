# SyncStateChangeParam (System API)

```TypeScript
interface SyncStateChangeParam
```

Information about the phone book sync state change.

**Since:** 26.0.1

<!--Device-pbap-interface SyncStateChangeParam--><!--Device-pbap-interface SyncStateChangeParam-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { pbap } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

The address of the remote device.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SyncStateChangeParam-deviceId: string--><!--Device-SyncStateChangeParam-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## state

```TypeScript
state: SyncStateType
```

Phone book sync state.

**Type:** [SyncStateType](arkts-connectivity-pbap-syncstatetype-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SyncStateChangeParam-state: SyncStateType--><!--Device-SyncStateChangeParam-state: SyncStateType-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.
