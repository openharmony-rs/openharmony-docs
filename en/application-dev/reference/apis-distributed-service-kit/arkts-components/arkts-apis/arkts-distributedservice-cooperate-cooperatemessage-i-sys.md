# CooperateMessage (System API)

Defines a screen hopping status change event.

**Since:** 11

**System capability:** SystemCapability.Msdp.DeviceStatus.Cooperate

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

## networkId

```TypeScript
networkId: string
```

Descriptor of the target device for screen hopping.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Msdp.DeviceStatus.Cooperate

**System API:** This is a system API.

## state

```TypeScript
state: CooperateState
```

Screen hopping status.

**Type:** [CooperateState](arkts-distributedservice-cooperate-cooperatestate-e-sys.md)

**Since:** 11

**System capability:** SystemCapability.Msdp.DeviceStatus.Cooperate

**System API:** This is a system API.
