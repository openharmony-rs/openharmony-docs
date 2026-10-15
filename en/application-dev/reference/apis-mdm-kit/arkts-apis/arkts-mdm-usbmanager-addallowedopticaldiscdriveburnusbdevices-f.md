# addAllowedOpticalDiscDriveBurnUsbDevices

## Modules to Import

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## addAllowedOpticalDiscDriveBurnUsbDevices

```TypeScript
function addAllowedOpticalDiscDriveBurnUsbDevices(usbDevices: Array<UsbDevice>): void
```

Add the list of USB devices that support CD/DVD burning.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**Model restriction:** This API can be used only in the stage model.

<!--Device-usbManager-function addAllowedOpticalDiscDriveBurnUsbDevices(usbDevices: Array<UsbDevice>): void--><!--Device-usbManager-function addAllowedOpticalDiscDriveBurnUsbDevices(usbDevices: Array<UsbDevice>): void-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| usbDevices | Array&lt;[UsbDevice](arkts-mdm-usbmanager-usbdevice-i.md)&gt; | Yes | Array of USB device types to be added.<br>The maximum length is 10000 and cannot be empty. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| 9200019 | The policy list has exceeded the limit. The maximum length of usbDevices is         10000. Remove some devices from the list and try again. |
