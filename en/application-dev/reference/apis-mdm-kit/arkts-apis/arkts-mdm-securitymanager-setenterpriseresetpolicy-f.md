# setEnterpriseResetPolicy

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## setEnterpriseResetPolicy

```TypeScript
function setEnterpriseResetPolicy(policy: EnterpriseResetPolicy): void
```

Sets the enterprise reset policy.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

<!--Device-securityManager-function setEnterpriseResetPolicy(policy: EnterpriseResetPolicy): void--><!--Device-securityManager-function setEnterpriseResetPolicy(policy: EnterpriseResetPolicy): void-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policy | [EnterpriseResetPolicy](arkts-mdm-securitymanager-enterpriseresetpolicy-e.md) | Yes | Enterprise reset policy to set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
