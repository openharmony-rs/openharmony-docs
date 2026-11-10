# usb_serial_api.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=6bf705413e67f9d206cf9b81603cd89e87db21cc translatedAt=2026-11-10T01:11:35.082Z pushedAt=2026-11-10T01:47:21.111Z nl=1 -->

## Overview

Declares the USB Serial DDK APIs used by the host to access the serial port device. It provides the capabilities of reading data from and writing data to serial ports and configuring parameters. This API is applicable to scenarios where serial port devices need to be accessed through the USB port, such as industrial control and embedded device communication.

**File to include**: <usb_serial/usb_serial_api.h>

**Library:** libusb_serial_ndk.z.so

**System capability**: SystemCapability.Driver.UsbSerial.Extension

**Since**: 18

**Related module**: [USBSerialDDK](capi-serialddk.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [int32_t OH_UsbSerial_Init(void)](#oh_usbserial_init) | Initializes the USB Serial DDK. This API must be called before calling any other USB Serial DDK APIs. It establishes a communication connection with the DDK service and loads the necessary driver resources. Call [OH_UsbSerial_Release()](#oh_usbserial_release) after use to release the DDK and avoid resource leaks.|
| [int32_t OH_UsbSerial_Release(void)](#oh_usbserial_release) | Releases the USB Serial DDK. This API must be used in pairs with [OH_UsbSerial_Init()](#oh_usbserial_init). After release, no other USB Serial DDK APIs can be called. |
| [int32_t OH_UsbSerial_Open(uint64_t deviceId, uint8_t interfaceIndex, UsbSerial_Device **dev)](#oh_usbserial_open) | Opens a USB serial port device by deviceId and interfaceIndex. This API establishes a connection with the specified USB serial port device and returns a device handle for subsequent operations. Call [OH_UsbSerial_Close()](#oh_usbserial_close) after use to close the device; otherwise, the device resources may not be released correctly. |
| [int32_t OH_UsbSerial_Close(UsbSerial_Device **dev)](#oh_usbserial_close) | Closes a USB serial port device. This API releases the resources occupied by the device and must be used in pairs with [OH_UsbSerial_Open()](#oh_usbserial_open). |
| [int32_t OH_UsbSerial_Read(UsbSerial_Device *dev, uint8_t *buff, uint32_t bufferSize, uint32_t *bytesRead)](#oh_usbserial_read) | Reads data from the USB serial port device to the buffer.|
| [int32_t OH_UsbSerial_Write(UsbSerial_Device *dev, uint8_t *buff, uint32_t bufferSize, uint32_t *bytesWritten)](#oh_usbserial_write) | Writes the data in the buffer to the USB serial port device.|
| [int32_t OH_UsbSerial_SetBaudRate(UsbSerial_Device *dev, uint32_t baudRate)](#oh_usbserial_setbaudrate) | Sets the baud rate of a USB serial port device. If the parameters of the USB serial port device are the default values (8 data bits, 1 stop bit, and no parity check for data transmission), only this API needs to be called to set the baud rate. |
| [int32_t OH_UsbSerial_SetParams(UsbSerial_Device *dev, UsbSerial_Params *params)](#oh_usbserial_setparams) | Sets the parameters of the USB serial port device. If the parameters of the USB serial port device are not set to the default values (the data bit is **8**, the stop bit is **1**, and parity is disabled for data transfer), you only need to call this API to set the related parameters.|
| [int32_t OH_UsbSerial_SetTimeout(UsbSerial_Device *dev, int timeout)](#oh_usbserial_settimeout) | Sets the timeout interval (ms) for reading data reported by a USB serial port device. If this function is not called, the timeout value is **0** by default, indicating that data is returned immediately regardless of whether data is read. If you need to wait for a certain period of time or data must be read, call this API to set the timeout interval.|
| [int32_t OH_UsbSerial_SetFlowControl(UsbSerial_Device *dev, UsbSerial_FlowControl flowControl)](#oh_usbserial_setflowcontrol) | Sets the flow control parameters. Flow control in USB serial port device communication is used to manage the rate of data transmission, ensuring that the sender does not send more data than the receiver can process. If the USB serial port device implements flow control, this API must be called. If this API is not called, no flow control is used by default. |
| [int32_t OH_UsbSerial_Flush(UsbSerial_Device *dev)](#oh_usbserial_flush) | Clears the input and output buffers (and waits for the data in the output buffer to be sent). When sending data to a USB serial port device, a large amount of data may be buffered in the kernel waiting to be sent. If the application closes the device or exits without waiting for this data to be actually sent, some data may be lost. Calling this API ensures that all data is sent before subsequent operations continue. |
| [int32_t OH_UsbSerial_FlushInput(UsbSerial_Device *dev)](#oh_usbserial_flushinput) | Clears the input buffer, and the data in the buffer is cleared immediately. During the communication process with a USB serial port device, especially in the debugging phase, out-of-order data packets or other abnormal conditions may occur. This API can be used to clear the abnormal state on the receiving end and restore normal communication. This API does not affect the data pending transmission in the output buffer. |
| [int32_t OH_UsbSerial_FlushOutput(UsbSerial_Device *dev)](#oh_usbserial_flushoutput) | Clears the output buffer, and the data in the buffer is cleared immediately. During the communication process with a USB serial port device, especially in the debugging phase, out-of-order data packets or other abnormal conditions may occur. This API can be used to clear the abnormal state on the sending end and restore normal communication. This API does not affect the received data in the input buffer. |

## Function Description

### OH_UsbSerial_Init()

```c
int32_t OH_UsbSerial_Init(void)
```

**Description**

Initializes the USB Serial DDK. This API must be called before calling any other USB Serial DDK APIs. It establishes a communication connection with the DDK service and loads the necessary driver resources. Call [OH_UsbSerial_Release()](#oh_usbserial_release) after use to release the DDK and avoid resource leaks.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18

**Returns**

| Type| Description                                                                                                                                                                                                                               |
| -- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) Returns this code if the API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Returns this code if permission verification fails. Check whether the application has obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) Returns this code if the DDK fails to be initialized. |

### OH_UsbSerial_Release()

```c
int32_t OH_UsbSerial_Release(void)
```

**Description**

Releases the USB Serial DDK. This API must be used in pairs with [OH_UsbSerial_Init()](#oh_usbserial_init). After release, no other USB Serial DDK APIs can be called.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized or has been released. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service failed to execute. Check the device status. |

### OH_UsbSerial_Open()

```c
int32_t OH_UsbSerial_Open(uint64_t deviceId, uint8_t interfaceIndex, UsbSerial_Device **dev)
```

**Description**

Opens a USB serial port device by deviceId and interfaceIndex. This API establishes a connection with the specified USB serial port device and returns a device handle for subsequent operations. Call [OH_UsbSerial_Close()](#oh_usbserial_close) after use to close the device; otherwise, the device resources may not be released correctly.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name                             | Description                                        |
|----------------------------------|--------------------------------------------|
| uint64_t deviceId                | Device ID, which represents the device to operate. It can be obtained by calling [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices).                             |
| uint8_t interfaceIndex           | Interface index, which corresponds to bInterfaceNumber in the USB protocol. |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) **dev | Device handle, which is an output parameter used to return the opened USB serial port device handle. Call [OH_UsbSerial_Close()](#oh_usbserial_close) to release it after use. |

**Returns**

| Type | Description |
| -- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has correctly obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) Parameter check failed. Possible causes: dev is a null pointer or *dev is a null pointer. Check the validity of the parameters.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service failed to execute. Check the parameters and device status.<br>         [USB_SERIAL_DDK_MEMORY_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) Insufficient memory.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) An I/O error occurred in the DDK. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_DEVICE_NOT_FOUND](capi-usb-serial-types-h.md#usbserial_ddkretcode) The device or interface is not found. |

### OH_UsbSerial_Close()

```c
int32_t OH_UsbSerial_Close(UsbSerial_Device **dev)
```

**Description**

Closes a USB serial port device. This API releases the resources occupied by the device and must be used in pairs with [OH_UsbSerial_Open()](#oh_usbserial_open).

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) **dev | Device handle, which is an input/output parameter. The pointer is set to null after the device is closed. |

**Returns**

| Type | Description |
| -- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has correctly obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) Parameter check failed. Possible causes: dev is a null pointer or *dev is a null pointer. Check the validity of the parameters.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service failed to execute. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) An I/O error occurred in the DDK. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) Invalid operation. Ensure that the device is opened correctly. |

### OH_UsbSerial_Read()

```c
int32_t OH_UsbSerial_Read(UsbSerial_Device *dev, uint8_t *buff, uint32_t bufferSize, uint32_t *bytesRead)
```

**Description**

Reads data from the USB serial port device to the buffer.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, obtained by calling [OH_UsbSerial_Open()](#oh_usbserial_open) to open the device. |
| uint8_t *buff | Buffer for reading data from the USB serial port device. It is allocated by the caller, with a size not less than bufferSize. |
| uint32_t bufferSize | Buffer size.|
| uint32_t *bytesRead | Number of bytes actually read. In blocking mode, the function returns only after the number of bytes actually read equals bufferSize. If a timeout is set, the return value may be less than bufferSize.<br>                  For details, see [OH_UsbSerial_SetTimeout()](#oh_usbserial_settimeout). |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) Parameter check failed. Possible causes: 1. dev is a null pointer; 2. buff is a null pointer; 3. bufferSize is 0; 4. bytesRead is a null pointer. Check the validity of the parameters.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service failed to execute. Check the parameters and device status.<br>         [USB_SERIAL_DDK_MEMORY_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The buff address is invalid.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) An I/O error occurred in the DDK. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) Invalid operation. Ensure that the device is opened properly. |

### OH_UsbSerial_Write()

```c
int32_t OH_UsbSerial_Write(UsbSerial_Device *dev, uint8_t *buff, uint32_t bufferSize, uint32_t *bytesWritten)
```

**Description**

Writes the data in the buffer to the USB serial port device.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, obtained by calling [OH_UsbSerial_Open()](#oh_usbserial_open) to open the device. |
| uint8_t *buff | Buffer for the data to be written to the USB serial port device. It must be allocated by the caller and its capacity must not be less than bufferSize. |
| uint32_t bufferSize | Buffer size.|
| uint32_t *bytesWritten | Number of bytes actually written. It is valid only when the API returns success, and it may be less than bufferSize. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has correctly obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) Parameter check failed. Possible causes: 1. dev is a null pointer; 2. buff is a null pointer; 3. bufferSize is 0; 4. bytesWritten is a null pointer. Check the validity of the parameters.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service fails to execute. Check the parameters and device status.<br>[USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) An I/O error occurs in the DDK. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) Invalid operation. Ensure that the device is opened properly. |

### OH_UsbSerial_SetBaudRate()

```c
int32_t OH_UsbSerial_SetBaudRate(UsbSerial_Device *dev, uint32_t baudRate)
```

**Description**

Sets the baud rate for a USB serial port device. If the parameters of the USB serial port device are set to the default values (the data bit is **8**, the stop bit is **1**, and parity is disabled for data transfer), you only need to call this API to set the baud rate.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, obtained by calling [OH_UsbSerial_Open()](#oh_usbserial_open) to open the device. |
| uint32_t baudRate | Baud rate of the USB serial port device, in baud. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) Parameter check failed. Possible causes: dev is a null pointer. Check the validity of the parameter.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service failed to execute. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) An I/O error occurred in the DDK. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) Invalid operation. Ensure that the device is opened properly. |

### OH_UsbSerial_SetParams()

```c
int32_t OH_UsbSerial_SetParams(UsbSerial_Device *dev, UsbSerial_Params *params)
```

**Description**

Sets the parameters of the USB serial port device. If the parameters of the USB serial port device are not set to the default values (the data bit is **8**, the stop bit is **1**, and parity is disabled for data transfer), you only need to call this API to set related parameters.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name                                                                    | Description|
|-------------------------------------------------------------------------| -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, obtained by calling [OH_UsbSerial_Open()](#oh_usbserial_open) to open the device. |
| [UsbSerial_Params](capi-serialddk-usbserial-params.md) *params                                            | USB serial port device parameters. For details, see [UsbSerial_Params](capi-serialddk-usbserial-params.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) Parameter check failed. Possible causes: 1. dev is a null pointer;<br>         2. params is a null pointer. Check the validity of the parameters.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service failed to execute. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) An I/O error occurred in the DDK. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) Invalid operation. Ensure that the device is opened properly. |

### OH_UsbSerial_SetTimeout()

```c
int32_t OH_UsbSerial_SetTimeout(UsbSerial_Device *dev, int timeout)
```

**Description**

Sets the timeout interval (ms) for reading data reported by a USB serial port device. If this function is not called, the timeout value is **0** by default, indicating that data is returned immediately regardless of whether data is read. If you need to wait for a certain period of time or data must be read, call this API to set the timeout interval.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, obtained by calling [OH_UsbSerial_Open()](#oh_usbserial_open) to open the device. |
| int timeout | Timeout for reading data from the USB serial port device. When the value is in the range (0, 25500], it indicates a time value in milliseconds, which is rounded to the nearest 100 milliseconds as the actual timeout. For example, when 12321 is input, the actual timeout is 12300. When the value is 0, data is returned immediately without waiting. When the value is -1, data is read in blocking mode, that is, the read operation returns only after data of the specified length is read. For details, see [OH_UsbSerial_Read()](#oh_usbserial_read). It is recommended to use 0 in polling scenarios, (0, 25500] in scenarios requiring timeout control, and -1 in scenarios where complete data must be read. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has correctly obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) Parameter check failed. Possible causes: 1. dev is a null pointer;<br>         2. timeout < -1 or timeout > 25500. Check the parameter validity and the timeout.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service failed to execute. Check the parameters and the device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) An I/O error occurred in the DDK. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) Invalid operation. Ensure that the device has been opened properly. |

### OH_UsbSerial_SetFlowControl()

```c
int32_t OH_UsbSerial_SetFlowControl(UsbSerial_Device *dev, UsbSerial_FlowControl flowControl)
```

**Description**

Sets the flow control parameters. Flow control in USB serial port device communication is used to manage the rate of data transmission, ensuring that the sender does not send more data than the receiver can process. If the USB serial port device implements flow control, this API must be called. If this API is not called, no flow control is used by default.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name                                                                                  | Description|
|---------------------------------------------------------------------------------------| -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev               | Device handle, obtained by calling [OH_UsbSerial_Open()](#oh_usbserial_open) to open the device. |
| [UsbSerial_FlowControl](capi-usb-serial-types-h.md#usbserial_flowcontrol) flowControl | Flow control mode. For details, see [UsbSerial_FlowControl](capi-usb-serial-types-h.md#usbserial_flowcontrol).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) Parameter check failed. Possible causes: dev is a null pointer. Check the validity of the parameter.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service failed to execute. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) An I/O error occurred in the DDK. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) Invalid operation. Ensure that the device is opened properly. |

### OH_UsbSerial_Flush()

```c
int32_t OH_UsbSerial_Flush(UsbSerial_Device *dev)
```

**Description**

Clears the input and output buffers (and waits for the data in the output buffer to be sent). When sending data to a USB serial port device, a large amount of data may be buffered in the kernel waiting to be sent. If the application closes the device or exits without waiting for this data to be actually sent, some data may be lost. Calling this API ensures that all data is sent before subsequent operations continue.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, obtained by calling [OH_UsbSerial_Open()](#oh_usbserial_open) to open the device. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) Parameter check failed. Possible causes: dev is a null pointer. Check the validity of the parameter.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service failed to execute. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) An I/O error occurred in the DDK. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) Invalid operation. Ensure that the device is opened properly. |

### OH_UsbSerial_FlushInput()

```c
int32_t OH_UsbSerial_FlushInput(UsbSerial_Device *dev)
```

**Description**

Clears the input buffer, and the data in the buffer is cleared immediately. During the communication process with a USB serial port device, especially in the debugging phase, out-of-order data packets or other abnormal conditions may occur. This API can be used to clear the abnormal state on the receiving end and restore normal communication. This API does not affect the data pending transmission in the output buffer.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, obtained by calling [OH_UsbSerial_Open()](#oh_usbserial_open) to open the device. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) Parameter check failed. Possible causes: dev is a null pointer. Check the validity of the parameter.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service failed to execute. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) An I/O error occurred in the DDK. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) Invalid operation. Ensure that the device is opened properly. |

### OH_UsbSerial_FlushOutput()

```c
int32_t OH_UsbSerial_FlushOutput(UsbSerial_Device *dev)
```

**Description**

Clears the output buffer, and the data in the buffer is cleared immediately. During the communication process with a USB serial port device, especially in the debugging phase, out-of-order data packets or other abnormal conditions may occur. This API can be used to clear the abnormal state on the sending end and restore normal communication. This API does not affect the received data in the input buffer.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, obtained by calling [OH_UsbSerial_Open()](#oh_usbserial_open) to open the device. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode) The API is called successfully.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode) Permission verification failed. Check whether the application has obtained the ohos.permission.ACCESS_DDK_USB_SERIAL permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode) Parameter check failed. Possible causes: dev is a null pointer. Check the validity of the parameter.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK is not initialized. Call [OH_UsbSerial_Init()](#oh_usbserial_init) to initialize the DDK first.<br>         [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) The DDK service failed to execute. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) An I/O error occurred in the DDK. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode) Invalid operation. Ensure that the device is opened properly. |


