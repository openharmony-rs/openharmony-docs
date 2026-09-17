# bulkTransfer

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## bulkTransfer

```TypeScript
function bulkTransfer(
    pipe: USBDevicePipe,
    endpoint: USBEndpoint,
    buffer: Uint8Array,
    timeout?: number
  ): Promise<number>
```

After the bulk transfer is complete, the size of the transferred or received data block is returned. This API uses a promise to return the result. Compared with **usbSubmitTransfer**, **bulkTransfer** is suitable for simple bulk transfer. It directly transfers data and endpoints through independent parameters and uses a promise to return the result. **usbSubmitTransfer** is suitable for scenarios that require more flexible control. It encapsulates parameters in the **UsbDataTransferParams** object, supports asynchronous callback, and allows you to cancel a transfer request using **usbCancelTransfer**.

> **NOTE:** 
> 
> The total size of data (including **pipe**, **endpoint**, **buffer**, and **timeout**) to be
> transferred in a single bulk transfer must be less than 200 KB. Otherwise, the transfer fails
> and **-1** is returned.
> 
> Before calling this API, call the [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md)
> API to claim a communication interface.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | Yes | USB device pipe, which is used to determine the bus address and device address. You need to call [connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) to obtain its value. |
| endpoint | [USBEndpoint](arkts-basicservices-usbmanager-usbendpoint-i.md) | Yes | USB endpoint, which is used to determine the USB port for data transfer. You need to call [getDevices](arkts-basicservices-usbmanager-getdevices-f.md) to obtain the device information list. In the **USBEndpoint** API, the **address** parameter indicates the endpoint address. The **direction** parameter indicates the transmission direction of the endpoint, the value **0** indicates output, and **128** indicates input. The **interfaceId** parameter identifies the interface to which the endpoint belongs. Currently, other attributes are not processed. |
| buffer | Uint8Array | Yes | Buffer for writing or reading data. The array length indicates the buffer size. This parameter is used to write or read data during bulk transfer. |
| timeout | number | No | Timeout interval, in milliseconds. This parameter is optional. If the bulk transfer is complete within the specified time, the size of the transferred or received data block is returned; otherwise, a timeout error is returned. The default value is **0**, indicating that the system waits infinitely until the control transfer is complete. If a negative number is passed, a parameter error is thrown. Set this parameter as required. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result, which is the size of the transferred or received data block if the transfer is successful. If the API call fails, the following error codes are returned:<br>- -1: The driver is abnormal. Possible causes: 1. The device connection is unstable or the device is disconnected. 2. The USB driver fails to be loaded. 3. The kernel USB module is abnormal. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
> NOTE
> 
> The following sample code is only a basic process for calling the bulkTransfer API. When calling this API, you must comply with the protocol specifications of the target USB device to ensure proper data transfer and device compatibility. For details about the protocol requirements, see the technical documentation of the device.
```
