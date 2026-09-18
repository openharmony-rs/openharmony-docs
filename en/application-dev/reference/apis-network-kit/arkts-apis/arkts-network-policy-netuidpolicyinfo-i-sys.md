# NetUidPolicyInfo (System API)

Defines the network policy information for an application.

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## policy

```TypeScript
policy: NetUidPolicy
```

Policy that specifies whether the application specified by a given UID is allowed to access the network when running in the background.

**Type:** [NetUidPolicy](arkts-network-policy-netuidpolicy-e-sys.md)

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

Traffic alarm threshold. The default value is **DATA_USAGE_UNKNOWN**.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
