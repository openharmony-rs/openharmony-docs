# requestExemptionResource

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## requestExemptionResource

```TypeScript
function requestExemptionResource(resourceType: StandbyResourceType, bundleName: string, duration: number): void
```

Applies for a standby resource exemption for a specified application. After a successful application, the specified application can use the exempted resources (such as network access) even when the device enters standby mode.

The exemption is time-limited. When the specified duration expires, the system automatically releases the exemption. If the enterprise administrator needs to release the exemption early, call [releaseExemptionResource](arkts-mdm-applicationmanager-releaseexemptionresource-f.md).

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

<!--Device-applicationManager-function requestExemptionResource(resourceType: StandbyResourceType, bundleName: string, duration: number): void--><!--Device-applicationManager-function requestExemptionResource(resourceType: StandbyResourceType, bundleName: string, duration: number): void-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceType | [StandbyResourceType](arkts-mdm-applicationmanager-standbyresourcetype-e.md) | Yes | Standby resource type. |
| bundleName | string | Yes | Bundle name of the application to apply for the resource exemption. |
| duration | number | Yes | Exemption duration.<br>Unit: Seconds. The value must be greater than 0. |

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
