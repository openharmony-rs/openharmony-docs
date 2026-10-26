# setVolumeDegree

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## setVolumeDegree

```TypeScript
function setVolumeDegree(volumeType: AudioVolumeType, degree: number): void
```

Set the volume degree for a special volume type.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**Model restriction:** This API can be used only in the stage model.

<!--Device-systemManager-function setVolumeDegree(volumeType: AudioVolumeType, degree: number): void--><!--Device-systemManager-function setVolumeDegree(volumeType: AudioVolumeType, degree: number): void-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volumeType | [AudioVolumeType](arkts-mdm-systemmanager-audiovolumetype-e.md) | Yes | Volume type. |
| degree | number | Yes | Volume degree. The value must be greater than or equal to 0 and less than or equal to 100. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
