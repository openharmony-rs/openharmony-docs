# CooperateMessage (System API)

```TypeScript
interface CooperateMessage
```

Defines a screen hopping status change event.

**Since:** 11

<!--Device-cooperate-interface CooperateMessage--><!--Device-cooperate-interface CooperateMessage-End-->

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

<!--Device-CooperateMessage-networkId: string--><!--Device-CooperateMessage-networkId: string-End-->

**System capability:** SystemCapability.Msdp.DeviceStatus.Cooperate

**System API:** This is a system API.

## state

```TypeScript
state: CooperateState
```

Screen hopping status.

**Type:** [CooperateState](arkts-distributedservice-cooperate-cooperatestate-e-sys.md)

**Since:** 11

<!--Device-CooperateMessage-state: CooperateState--><!--Device-CooperateMessage-state: CooperateState-End-->

**System capability:** SystemCapability.Msdp.DeviceStatus.Cooperate

**System API:** This is a system API.
