# getUsbSerialNumber

## Modules to Import

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## getUsbSerialNumber

```TypeScript
function getUsbSerialNumber(busNum: number, devAddress: number): string
```

Queries the serial number of the usb device.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| busNum | number | Yes | busNum indicates the bus address of the usb device. |
| devAddress | number | Yes | devAddress indicates device address of the usb device. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the serial number of usb device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| 9201055 | Failed to obtain the USB serial number. |
