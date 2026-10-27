# getPasswordLastChangedTime

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## getPasswordLastChangedTime

```TypeScript
function getPasswordLastChangedTime(accountId: number): number
```

Obtains the last password change time based on the account ID. This API returns the time synchronously. Enterprises can use this API to query the last password change time for password policy audit and compliance check.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

<!--Device-securityManager-function getPasswordLastChangedTime(accountId: number): number--><!--Device-securityManager-function getPasswordLastChangedTime(accountId: number): number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Last password change timestamp, in milliseconds. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
