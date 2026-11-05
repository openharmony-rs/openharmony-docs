# Setting DLP File Protection Policies
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=bbcc2e37e8129d97ee49fdfc327c495aa2406a09 translatedAt=2026-10-31T07:05:33.195Z pushedAt=2026-10-31T09:17:28.399Z nl=1 -->

## When to Use

Data Protection Kit provides applications with the capability to set dynamic protection policies. When a user opens a DLP file, the system verifies the configured protection policies and blocks the operation when necessary.

The currently supported policy types include device health status, network status, debug mode status, advanced security mode status, and file type.

No communication plug-in needs to be registered in advance to use this capability.

## Development Procedure

1.  Import the modules required by the APIs.
    <!-- @[dlp_include_dlpPermission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { dlpPermission } from '@kit.DataProtectionKit';
    ```

2. Set the protection policy.

    2.1 Request the permission: `ohos.permission.ENTERPRISE_ACCESS_DLP_FILE`.

    2.2 Set the enterprise application protection policy [EnterprisePolicy](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#enterprisepolicy21) (including attribute information, rules, and policies).

    2.3 Call [dlpPermission.setEnterprisePolicy](../../reference/apis-data-protection-kit/js-apis-dlppermission.md#dlppermissionsetenterprisepolicy21) to complete the protection policy configuration.

    <!-- @[dlp_setEnterprisePolicy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    setEnterprisePolicy() {
      try {
        if (canIUse('SystemCapability.Security.DataLossPrevention')) {
          let attributeValues: string[] = ['1'];
          let attribute: Attribute = {
            attributeId: 'DeviceHealthyStatus',
            attributeValues: attributeValues,
            valueType: 0,
            opt: 2
          }; // Attribute information.
          let rule: Rule = {
            ruleId: 'ruleId',
            attributes: [attribute]
          }; // Rules.
          let policy: Policy = {
            rules: [rule],
            policyId: 'policyId',
            ruleConflictAlg: 0
          }; // Policy.
          let enterprisePolicy: dlpPermission.EnterprisePolicy = {
            policyString: JSON.stringify(policy)
          };
          dlpPermission.setEnterprisePolicy(enterprisePolicy);
          console.info('set enterprise policy success');
          this.result = 'set enterprise policy success';
          hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'set enterprise policy success');
        }
      } catch (err) {
        console.error('error message', err.message);
        this.result = 'error message' + err.message;
        hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
      }
    }
    ```

## FAQs

### Enterprise Policy Format Error

**Symptom**: A policy format error is reported when `setEnterprisePolicy` is called.

**Solution**:
- `policyId` and `ruleId` can contain only letters, digits, and underscores, and must not exceed 64 bytes in length.
- A policy can contain at most 32 rules, 32 attributes, and 32 attribute values.
- Ensure that `valueType` matches the attribute value type.