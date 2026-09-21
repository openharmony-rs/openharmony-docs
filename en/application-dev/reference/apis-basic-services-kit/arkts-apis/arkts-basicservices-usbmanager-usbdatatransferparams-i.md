# UsbDataTransferParams

```TypeScript
interface UsbDataTransferParams
```

Defines a USB data transfer parameter object, which contains all parameters required for USB data transfer. It is used by the **usbSubmitTransfer** and **usbCancelTransfer** APIs to initiate transfer requests.

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## buffer

```TypeScript
buffer: Uint8Array
```

Buffer, which is used to store data for read or write requests.

**Type:** Uint8Array

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## callback

```TypeScript
callback: AsyncCallback<SubmitTransferCallback>
```

Callback invoked when the transfer is complete. The signature is **(err: Error, data: SubmitTransferCallback) =&gt; void**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. **data** contains information such as the transfer status and actual length.

**Type:** [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[SubmitTransferCallback](arkts-basicservices-usbmanager-submittransfercallback-i.md)&gt;

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## devPipe

```TypeScript
devPipe: USBDevicePipe
```

USB device pipe, which is used to determine the bus address and device address. You need to call [connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) to obtain its value.

**Type:** [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md)

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## endpoint

```TypeScript
endpoint: number
```

Endpoint address. The value is a positive integer within the range of [1, 255]. You need to call [getDevices](arkts-basicservices-usbmanager-getdevices-f.md) to obtain the device information, use the **address** attribute of the endpoint to determine the endpoint information, and use the **direction** attribute to determine the endpoint direction.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## flags

```TypeScript
flags: UsbTransferFlags
```

USB transfer flag, which is used to control the transfer behavior. The options are as follows: **0**: Report short frames as errors; **1**: Automatically release the transfer buffer; **2**: Automatically release transfer resources after the callback is complete; **3**: Add an extra data packet to be transferred.

**Type:** [UsbTransferFlags](arkts-basicservices-usbmanager-usbtransferflags-e.md)

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## isoPacketCount

```TypeScript
isoPacketCount: number
```

Number of data packets during real-time transfer, used only for I/Os with real-time transfer endpoints. The value must be a non-negative number in the range of [0, **INT_MAX**].

**Type:** number

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## length

```TypeScript
length: number
```

Expected length of the data buffer, in bytes. The value must be a non-negative number in the range of [0, **INT_MAX**].

**Type:** number

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## timeout

```TypeScript
timeout: number
```

Timeout interval, in milliseconds. If the transfer is complete within the specified time, the size of the transferred or received data block is returned; otherwise, a timeout error is returned. The default value is **0**, indicating that the system waits infinitely until the control transfer is complete. If a negative number is passed, a parameter error is thrown.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## type

```TypeScript
type: UsbEndpointTransferType
```

Transfer type, which specifies the USB data transfer mode. The options are as follows: **0x1**: real-time transfer, suitable for real-time data streams such as audio and video; **0x2**: bulk transfer, suitable for non-real-time transfer of a large amount of data; **0x3**: interrupt transfer, suitable for real-time transfer of a small amount of data.

**Type:** [UsbEndpointTransferType](arkts-basicservices-usbmanager-usbendpointtransfertype-e.md)

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## userData

```TypeScript
userData: Uint8Array
```

User context data, which is used to pass custom context information in the callback. The size and format are defined by the user and specified in the transfer request. The data is returned in the callback without any modification.

**Type:** Uint8Array

**Since:** 18

**System capability:** SystemCapability.USB.USBManager
