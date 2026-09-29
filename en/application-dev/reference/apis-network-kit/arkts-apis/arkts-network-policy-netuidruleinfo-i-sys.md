# NetUidRuleInfo (System API)

```TypeScript
export interface NetUidRuleInfo
```

Defines a unique network ID.

**Since:** 11

<!--Device-policy-export interface NetUidRuleInfo--><!--Device-policy-export interface NetUidRuleInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## rule

```TypeScript
rule: NetUidRule
```

Rule that specifies whether the application specified by a given UID is allowed to access a metered or non- metered network.

**Type:** [NetUidRule](arkts-network-policy-netuidrule-e-sys.md)

**Since:** 11

<!--Device-NetUidRuleInfo-rule: NetUidRule--><!--Device-NetUidRuleInfo-rule: NetUidRule-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

Traffic alarm threshold. The default value is **DATA_USAGE_UNKNOWN**.

**Type:** number

**Since:** 11

<!--Device-NetUidRuleInfo-uid: int--><!--Device-NetUidRuleInfo-uid: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
