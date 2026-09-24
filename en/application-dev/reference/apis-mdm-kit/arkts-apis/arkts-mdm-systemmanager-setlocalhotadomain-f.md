# setLocalHotaDomain

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## setLocalHotaDomain

```TypeScript
function setLocalHotaDomain(admin: Want, domain: string): void
```

Set the local HOTA domain of the device.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | admin indicates the enterprise admin extension ability information. |
| domain | string | Yes | Indicates the local HOTA domain to set. The value must comply with domain name rules. The validation rules are as follows: 1. The length must not exceed 64 characters. 2. IP addresses and localhost are not supported. 3. The domain requires the full request root address, must start with the https://. 4. The domain must match the folllowing regular expression: ^(?:[a-zA-Z0-9](?:[a-zA-Z0-9.-]*[a-zA-Z0-9])?\\.)+[a-zA-Z]{2,}$ 5. Passing an empty string means reverting the domain to its default value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200018](../errorcode-enterpriseDeviceManager.md#9200018-the-device-is-not-an-enterprise-device) | This device is not an enterprise device. |
