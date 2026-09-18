# addUserExtendCredential

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## addUserExtendCredential

```TypeScript
function addUserExtendCredential(info: AddCredentialInfo, accountId: number): Promise<Uint8Array>
```

Adds the extended user credential for an account.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AddCredentialInfo](arkts-mdm-securitymanager-addcredentialinfo-i.md) | Yes | info indicates the the infomation required to add the credential. |
| accountId | number | Yes | accountId indicates the ID of OS account.<br>Value range:[0, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Returns the credential ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| 9201052 | USB key session time out. |
