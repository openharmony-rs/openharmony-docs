# getAdminInfos

## Modules to Import

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## getAdminInfos

```TypeScript
function getAdminInfos(): Array<AdminInfo>
```

Queries all device administrators information.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_DEVICE_ADMIN

**Model restriction:** This API can be used only in the stage model.

<!--Device-adminManager-function getAdminInfos(): Array<AdminInfo>--><!--Device-adminManager-function getAdminInfos(): Array<AdminInfo>-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[AdminInfo](arkts-mdm-adminmanager-admininfo-i.md)&gt; | Returns the administrators information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
