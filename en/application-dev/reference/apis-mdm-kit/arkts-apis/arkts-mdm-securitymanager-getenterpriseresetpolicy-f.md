# getEnterpriseResetPolicy

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## getEnterpriseResetPolicy

```TypeScript
function getEnterpriseResetPolicy(): EnterpriseResetPolicy
```

Obtains the enterprise reset policy. This API returns the policy synchronously.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

<!--Device-securityManager-function getEnterpriseResetPolicy(): EnterpriseResetPolicy--><!--Device-securityManager-function getEnterpriseResetPolicy(): EnterpriseResetPolicy-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Return value:**

| Type | Description |
| --- | --- |
| [EnterpriseResetPolicy](arkts-mdm-securitymanager-enterpriseresetpolicy-e.md) | Enterprise reset policy. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
