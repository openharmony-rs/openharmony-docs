# AcbStateParam

```TypeScript
interface AcbStateParam
```

Represents the result of the logical link connection status change event.

**Since:** 26.0.0

<!--Device-remoteDevice-interface AcbStateParam--><!--Device-remoteDevice-interface AcbStateParam-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

Device address, indicating that the logical link connection status with the device changes. The address format is **11:22:33:AA:BB:FF**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AcbStateParam-address: string--><!--Device-AcbStateParam-address: string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: AcbState
```

Current logical link connection status.

**Type:** [AcbState](arkts-connectivity-remotedevice-acbstate-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AcbStateParam-state: AcbState--><!--Device-AcbStateParam-state: AcbState-End-->

**System capability:** SystemCapability.Communication.NearLink.Base
