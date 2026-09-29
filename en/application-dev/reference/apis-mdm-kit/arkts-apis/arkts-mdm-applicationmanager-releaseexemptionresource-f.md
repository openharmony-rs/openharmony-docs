# releaseExemptionResource

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## releaseExemptionResource

```TypeScript
function releaseExemptionResource(resourceType: StandbyResourceType, bundleName: string): void
```

Releases a standby resource exemption for a specified application.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

<!--Device-applicationManager-function releaseExemptionResource(resourceType: StandbyResourceType, bundleName: string): void--><!--Device-applicationManager-function releaseExemptionResource(resourceType: StandbyResourceType, bundleName: string): void-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceType | [StandbyResourceType](arkts-mdm-applicationmanager-standbyresourcetype-e.md) | Yes | Standby resource type. |
| bundleName | string | Yes | Bundle name of the application to release the resource exemption for. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| [9201002](../errorcode-enterpriseDeviceManager.md#9201002-failed-to-install-the-enterprise-application) | The application is not installed. |
