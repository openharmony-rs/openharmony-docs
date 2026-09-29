# HardwareDescriptor (System API)

```TypeScript
interface HardwareDescriptor
```

Represents the distributed hardware information.

@typedef HardwareDescriptor

**Since:** 11

<!--Device-hardwareManager-interface HardwareDescriptor--><!--Device-hardwareManager-interface HardwareDescriptor-End-->

**System capability:** SystemCapability.DistributedHardware.DistributedHardwareFWK

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { hardwareManager } from '@kit.DistributedServiceKit';
```

## srcNetworkId

```TypeScript
srcNetworkId?: string
```

Source device. If this parameter is not specified, it indicates all source devices.

**Type:** string

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_DISTRIBUTED_HARDWARE

<!--Device-HardwareDescriptor-srcNetworkId?: string--><!--Device-HardwareDescriptor-srcNetworkId?: string-End-->

**System capability:** SystemCapability.DistributedHardware.DistributedHardwareFWK

**System API:** This is a system API.

## type

```TypeScript
type: DistributedHardwareType
```

Type of the distributed hardware.

**Type:** [DistributedHardwareType](arkts-distributedservice-hardwaremanager-distributedhardwaretype-e-sys.md)

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_DISTRIBUTED_HARDWARE

<!--Device-HardwareDescriptor-type: DistributedHardwareType--><!--Device-HardwareDescriptor-type: DistributedHardwareType-End-->

**System capability:** SystemCapability.DistributedHardware.DistributedHardwareFWK

**System API:** This is a system API.
