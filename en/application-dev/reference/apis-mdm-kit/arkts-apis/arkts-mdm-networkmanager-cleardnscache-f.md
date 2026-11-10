# clearDnsCache

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## clearDnsCache

```TypeScript
function clearDnsCache(netId: number): void
```

Clears the DNS cache for a specified network. This API uses an asynchronous callback to return the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**Model restriction:** This API can be used only in the stage model.

<!--Device-networkManager-function clearDnsCache(netId: number): void--><!--Device-networkManager-function clearDnsCache(netId: number): void-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netId | number | Yes | Network ID. The value must be greater than or equal to 100. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
