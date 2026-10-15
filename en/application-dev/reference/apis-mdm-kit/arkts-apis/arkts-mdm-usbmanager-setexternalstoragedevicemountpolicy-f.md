# setExternalStorageDeviceMountPolicy

## Modules to Import

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## setExternalStorageDeviceMountPolicy

```TypeScript
function setExternalStorageDeviceMountPolicy(volumeId: string, policy: MountPolicy): void
```

Set the mounting policy for external storage devices.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**Model restriction:** This API can be used only in the stage model.

<!--Device-usbManager-function setExternalStorageDeviceMountPolicy(volumeId: string, policy: MountPolicy): void--><!--Device-usbManager-function setExternalStorageDeviceMountPolicy(volumeId: string, policy: MountPolicy): void-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeId | string | Yes | Volume ID. |
| policy | [MountPolicy](arkts-mdm-usbmanager-mountpolicy-e.md) | Yes | Mounting strategy. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| 9201056 | Invalid external storage mount policy. |
