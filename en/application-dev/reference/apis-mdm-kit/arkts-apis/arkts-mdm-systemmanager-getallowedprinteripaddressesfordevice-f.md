# getAllowedPrinterIPAddressesForDevice

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## getAllowedPrinterIPAddressesForDevice

```TypeScript
function getAllowedPrinterIPAddressesForDevice(queryPolicy?: common.QueryPolicy): Array<string>
```

Gets allowed printer IP addresses for device.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| queryPolicy | [common.QueryPolicy](arkts-mdm-common-querypolicy-e.md) | No | queryPolicy indicates the policy of query.<br>Default value: common.QueryPolicy.SELF. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Returns the IP address list of printer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
