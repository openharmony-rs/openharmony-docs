# ConnectionChangeState

Defines the connection status reporting parameters.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

Remote device address. The address format is **11:22:33:AA:BB:FF**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: ConnectionState
```

Connection status with a remote device.

**Type:** [ConnectionState](arkts-connectivity-ssap-connectionstate-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base
