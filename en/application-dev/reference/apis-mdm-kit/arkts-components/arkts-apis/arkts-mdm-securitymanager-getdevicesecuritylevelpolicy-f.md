# getDeviceSecurityLevelPolicy

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## getDeviceSecurityLevelPolicy

```TypeScript
function getDeviceSecurityLevelPolicy(): DeviceSecurityLevelPolicy
```

Gets the device security level policy.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Return value:**

| Type | Description |
| --- | --- |
| [DeviceSecurityLevelPolicy](arkts-mdm-securitymanager-devicesecuritylevelpolicy-e.md) | Returns the security level policy of device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
