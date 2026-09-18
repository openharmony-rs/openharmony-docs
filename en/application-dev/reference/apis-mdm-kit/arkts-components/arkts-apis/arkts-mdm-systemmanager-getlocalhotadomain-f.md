# getLocalHotaDomain

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## getLocalHotaDomain

```TypeScript
function getLocalHotaDomain(admin: Want): string
```

Get local HOTA domain for device.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | admin indicates the enterprise admin extension ability information. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the local HOTA domain.When the interface is not supported on the current device, return an empty string as the default value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200018](../errorcode-enterpriseDeviceManager.md#9200018-the-device-is-not-an-enterprise-device) | This device is not an enterprise device. |
