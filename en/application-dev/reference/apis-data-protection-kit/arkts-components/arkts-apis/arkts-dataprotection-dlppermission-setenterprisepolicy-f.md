# setEnterprisePolicy

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## setEnterprisePolicy

```TypeScript
function setEnterprisePolicy(policy: EnterprisePolicy): void
```

Sets the protection policy for enterprise applications. After the API is successfully called, the DLP protection for enterprise applications is implemented based on the configured policy.

This API is used by the enterprise administrator to configure DLP security policies for unified management of data security protection rules.

> **NOTE:** 
> 
> This API can be called only by enterprise accounts.

**Since:** 21

**Required permissions:** ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policy | [EnterprisePolicy](arkts-dataprotection-dlppermission-enterprisepolicy-i.md) | Yes | Enterprise application protection policy to be set. Access control and behavior restrictions of enterprise DLP files are implemented based on the policy. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.0.1 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |
| [19100021](../errorcode-dlp.md#19100021-failed-to-set-enterprise-application-policy) | Failed to set the enterprise policy. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

interface Attribute {
  attributeId: string;
  attributeValues: Array<string>;
  valueType: number;
  opt: number;
}

interface Rule {
  ruleId: string;
  attributes: Array<Attribute>;
}

interface Policy {
  rules: Array<Rule>;
  policyId: string;
  ruleConflictAlg: number;
}

try {
    let attributeValues: Array<string> = [ '1' ];
    let attribute: Attribute = {
        attributeId: 'DeviceHealthyStatus',
        attributeValues: attributeValues,
        valueType: 0,
        opt: 2
    }; // Attribute information
    let rule: Rule = {
        ruleId: 'ruleId',
        attributes: [ attribute ]
    }; // Rules
    let policy: Policy = {
        rules: [ rule ],
        policyId: 'policyId',
        ruleConflictAlg: 0
    }; // Policy
    let enterprisePolicy: dlpPermission.EnterprisePolicy = {
        policyString: JSON.stringify(policy)
    };
    dlpPermission.setEnterprisePolicy(enterprisePolicy);
    console.info('set enterprise policy success'); 
} catch (err) { 
    console.error(`Failed to set enterprise policy. Code: ${err.code}, message: ${err.message}`);
}
```
