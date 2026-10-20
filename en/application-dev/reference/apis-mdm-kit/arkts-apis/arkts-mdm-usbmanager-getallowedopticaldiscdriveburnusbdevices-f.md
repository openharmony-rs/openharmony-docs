# getAllowedOpticalDiscDriveBurnUsbDevices

## Modules to Import

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## getAllowedOpticalDiscDriveBurnUsbDevices

```TypeScript
function getAllowedOpticalDiscDriveBurnUsbDevices(queryPolicy?: common.QueryPolicy): Promise<Array<UsbDevice>>
```

Obtain the list of USB devices that support CD/DVD burning.This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**Model restriction:** This API can be used only in the stage model.

<!--Device-usbManager-function getAllowedOpticalDiscDriveBurnUsbDevices(queryPolicy?: common.QueryPolicy): Promise<Array<UsbDevice>>--><!--Device-usbManager-function getAllowedOpticalDiscDriveBurnUsbDevices(queryPolicy?: common.QueryPolicy): Promise<Array<UsbDevice>>-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| queryPolicy | [common.QueryPolicy](arkts-mdm-common-querypolicy-e.md) | No | queryPolicy indicates the policy of query. <br>Default value: common.QueryPolicy.SELF. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[UsbDevice](arkts-mdm-usbmanager-usbdevice-i.md)&gt;&gt; | Promise used to return Array<UsbDevice>.The array of allowed USB devices. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
