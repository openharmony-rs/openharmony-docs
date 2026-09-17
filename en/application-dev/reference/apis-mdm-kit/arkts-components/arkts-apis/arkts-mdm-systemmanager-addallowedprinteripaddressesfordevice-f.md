# addAllowedPrinterIPAddressesForDevice

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## addAllowedPrinterIPAddressesForDevice

```TypeScript
function addAllowedPrinterIPAddressesForDevice(ipAddresses: Array<string>): void
```

Adds allowed printer IP addresses for device. The policy takes effect for all accounts.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ipAddresses | Array&lt;string&gt; | Yes | ipAddresses indicate the IP address list of printer. Each IP address must be in IPv4 format or IPV6 format. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| 9200019 | The policy list has exceeded the limit. |
