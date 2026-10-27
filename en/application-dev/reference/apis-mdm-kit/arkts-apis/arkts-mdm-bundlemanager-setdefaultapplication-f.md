# setDefaultApplication

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## setDefaultApplication

```TypeScript
function setDefaultApplication(type: DefaultApplicationType, bundleName: string, abilityName: string, accountId: number): void
```

Sets the default application for the specified type.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**Model restriction:** This API can be used only in the stage model.

<!--Device-bundleManager-function setDefaultApplication(type: DefaultApplicationType, bundleName: string, abilityName: string, accountId: number): void--><!--Device-bundleManager-function setDefaultApplication(type: DefaultApplicationType, bundleName: string, abilityName: string, accountId: number): void-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [DefaultApplicationType](arkts-mdm-bundlemanager-defaultapplicationtype-e.md) | Yes | Type of the default application. |
| bundleName | string | Yes | Bundle name of the application. |
| abilityName | string | Yes | Name of the application ability. |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
