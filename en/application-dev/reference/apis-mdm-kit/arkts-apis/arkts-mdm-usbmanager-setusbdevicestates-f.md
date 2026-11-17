# setUsbDeviceStates

## Modules to Import

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## setUsbDeviceStates

```TypeScript
function setUsbDeviceStates(usbDeviceConfigInfo: common.USBDeviceConfigInfo, isEnable: boolean): void
```

Sets the state of USB devices.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**Model restriction:** This API can be used only in the stage model.

<!--Device-usbManager-function setUsbDeviceStates(usbDeviceConfigInfo: common.USBDeviceConfigInfo, isEnable: boolean): void--><!--Device-usbManager-function setUsbDeviceStates(usbDeviceConfigInfo: common.USBDeviceConfigInfo, isEnable: boolean): void-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| usbDeviceConfigInfo | [common.USBDeviceConfigInfo](arkts-mdm-common-usbdeviceconfiginfo-i.md) | Yes | USB device configuration information. |
| isEnable | boolean | Yes | Whether to enable the USB device. true: Enable the USB device. false: Disable the USB device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| 9201059 | Failed to set the state because dynamic USB control is not enabled. |
