# NetworkIdQueryFilter (System API)

```TypeScript
interface NetworkIdQueryFilter
```

Defines the network ID filter options.

**Since:** 18

<!--Device-distributedDeviceManager-interface NetworkIdQueryFilter--><!--Device-distributedDeviceManager-interface NetworkIdQueryFilter-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## onlineStatus

```TypeScript
onlineStatus : number
```

Device online status.

- **0**: The device is offline.  
- **1**: The device is online.

**Type:** number

**Since:** 18

<!--Device-NetworkIdQueryFilter-onlineStatus : int--><!--Device-NetworkIdQueryFilter-onlineStatus : int-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## wiseDeviceId

```TypeScript
wiseDeviceId : string
```

Registered device ID.

**Type:** string

**Since:** 18

<!--Device-NetworkIdQueryFilter-wiseDeviceId : string--><!--Device-NetworkIdQueryFilter-wiseDeviceId : string-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
