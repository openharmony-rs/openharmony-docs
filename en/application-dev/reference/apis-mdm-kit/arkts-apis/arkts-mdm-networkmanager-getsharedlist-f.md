# getSharedList

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## getSharedList

```TypeScript
function getSharedList(): Array<PathSharedData>
```

Obtain a list of all folder paths that are shared through the network domain on the device.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**Model restriction:** This API can be used only in the stage model.

<!--Device-networkManager-function getSharedList(): Array<PathSharedData>--><!--Device-networkManager-function getSharedList(): Array<PathSharedData>-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[PathSharedData](arkts-mdm-networkmanager-pathshareddata-i.md)&gt; | Return the array of shared path information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
