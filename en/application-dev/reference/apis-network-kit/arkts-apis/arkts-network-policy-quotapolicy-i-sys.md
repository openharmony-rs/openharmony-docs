# QuotaPolicy (System API)

Defines the network quota policy.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## lastLimitRemind

```TypeScript
lastLimitRemind?: number
```

Last time when the quota was exhausted. Default value: **-1**.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## lastWarningRemind

```TypeScript
lastWarningRemind?: number
```

Last time when an alarm was generated. Default value: **-1**.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## limitAction

```TypeScript
limitAction: LimitAction
```

Action to take when the data volume quota is reached.

**Type:** [LimitAction](arkts-network-policy-limitaction-e-sys.md)

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## limitBytes

```TypeScript
limitBytes: number
```

Data volume quota.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## metered

```TypeScript
metered: boolean
```

Whether the network is a metered network. The value **true** indicates that the network is a metered network, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## periodDuration

```TypeScript
periodDuration: string
```

Metering period for the quota limit. **D1**, **M1**, and **Y1** indicate one day, one month, and one year, respectively. If the specified metering period is exceeded, the quota is not limited.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## warningBytes

```TypeScript
warningBytes: number
```

Data volume threshold for generating an alarm.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
