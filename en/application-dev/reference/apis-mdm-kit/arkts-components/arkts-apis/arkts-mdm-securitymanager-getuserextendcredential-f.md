# getUserExtendCredential

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## getUserExtendCredential

```TypeScript
function getUserExtendCredential(accountId: number): Promise<UserExtCredentialInfo[]>
```

Gets the extended user credential information of the specified account.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | number | Yes | accountId indicates the ID of OS account.<br>Value range:[0, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[UserExtCredentialInfo](arkts-mdm-securitymanager-userextcredentialinfo-i.md)[]&gt; | Returns the list of extended user credential information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
