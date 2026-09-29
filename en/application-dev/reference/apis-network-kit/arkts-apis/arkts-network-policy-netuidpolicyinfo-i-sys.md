# NetUidPolicyInfo (System API)

```TypeScript
export interface NetUidPolicyInfo
```

Defines the network policy information for an application.

**Since:** 11

<!--Device-policy-export interface NetUidPolicyInfo--><!--Device-policy-export interface NetUidPolicyInfo-End-->

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

<!--Device-NetUidPolicyInfo-policy: NetUidPolicy--><!--Device-NetUidPolicyInfo-policy: NetUidPolicy-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

Traffic alarm threshold. The default value is **DATA_USAGE_UNKNOWN**.

**Type:** number

**Since:** 11

<!--Device-NetUidPolicyInfo-uid: int--><!--Device-NetUidPolicyInfo-uid: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
