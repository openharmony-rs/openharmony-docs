# EnterprisePolicy

```TypeScript
export interface EnterprisePolicy
```

Represents an enterprise custom policy.

**Since:** 21

<!--Device-dlpPermission-export interface EnterprisePolicy--><!--Device-dlpPermission-export interface EnterprisePolicy-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## policyString

```TypeScript
policyString: string
```

JSON string of an enterprise custom policy. The value contains a maximum of 4,194,304 bytes. If the value is out of range, an error log is generated.

**Type:** string

**Since:** 21

<!--Device-EnterprisePolicy-policyString: string--><!--Device-EnterprisePolicy-policyString: string-End-->

**System capability:** SystemCapability.Security.DataLossPrevention
