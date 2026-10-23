# usb_serial_api.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

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
| [int32_t OH_UsbSerial_Init(void)](#oh_usbserial_init) | Initializes the USB Serial DDK. This API must be called before any other USB Serial DDK APIs. It establishes communication with the DDK service and loads necessary driver resources. After using the DDK, call [OH_UsbSerial_Release](#oh_usbserial_release) to release it to avoid resource leaks.|
| [int32_t OH_UsbSerial_Release(void)](#oh_usbserial_release) | Releases the USB Serial DDK. This function must be used together with [OH_UsbSerial_Init](#oh_usbserial_init). After the DDK is released, other USB Serial DDK methods cannot be called.|
| [int32_t OH_UsbSerial_Open(uint64_t deviceId, uint8_t interfaceIndex, UsbSerial_Device **dev)](#oh_usbserial_open) | Opens the USB serial port device based on the specified **deviceId** and **interfaceIndex**. This API establishes a connection with the specified USB serial port device and returns the device handle for follow-up procedures. After using the device, call [OH_UsbSerial_Close](#oh_usbserial_close) to close the device. Otherwise, device resources may not be correctly released.|
| [int32_t OH_UsbSerial_Close(UsbSerial_Device **dev)](#oh_usbserial_close) | Closes the USB serial port device. This API releases the resources occupied by the device and must be used together with [OH_UsbSerial_Open](#oh_usbserial_open).|
| [int32_t OH_UsbSerial_Read(UsbSerial_Device *dev, uint8_t *buff, uint32_t bufferSize, uint32_t *bytesRead)](#oh_usbserial_read) | Reads data from the USB serial port device to the buffer.|
| [int32_t OH_UsbSerial_Write(UsbSerial_Device *dev, uint8_t *buff, uint32_t bufferSize, uint32_t *bytesWritten)](#oh_usbserial_write) | Writes the data in the buffer to the USB serial port device.|
| [int32_t OH_UsbSerial_SetBaudRate(UsbSerial_Device *dev, uint32_t baudRate)](#oh_usbserial_setbaudrate) | Sets the baud rate for a USB serial port device. If the parameters of the USB serial port device are set to the default values (the data bit is **8**, the stop bit is **1**, and parity is disabled for data transfer), you only need to call this API to set the baud rate.|
| [int32_t OH_UsbSerial_SetParams(UsbSerial_Device *dev, UsbSerial_Params *params)](#oh_usbserial_setparams) | Sets the parameters of the USB serial port device. If the parameters of the USB serial port device are not set to the default values (the data bit is **8**, the stop bit is **1**, and parity is disabled for data transfer), you only need to call this API to set the related parameters.|
| [int32_t OH_UsbSerial_SetTimeout(UsbSerial_Device *dev, int timeout)](#oh_usbserial_settimeout) | Sets the timeout interval (ms) for reading data reported by a USB serial port device. If this function is not called, the timeout value is **0** by default, indicating that data is returned immediately regardless of whether data is read. If you need to wait for a certain period of time or data must be read, call this API to set the timeout interval.|
| [int32_t OH_UsbSerial_SetFlowControl(UsbSerial_Device *dev, UsbSerial_FlowControl flowControl)](#oh_usbserial_setflowcontrol) | Sets flow control parameters. Flow control is used to manage the data transfer rate during communication with the USB serial port device to ensure that the sender does not send data that exceeds the processing capability of the receiver. If flow control is required, call this API to set flow control parameters. If this API is not called, flow control is disabled by default.|
| [int32_t OH_UsbSerial_Flush(UsbSerial_Device *dev)](#oh_usbserial_flush) | Flushes the input and output buffers. The system waits until all data in the output buffer is sent. If a large amount of data is to be transmitted to the USB serial port device, the data may be buffered in the kernel for transmission. If the app closes the device or exits before all data is sent out, some data may be lost. You can call this API to ensure that all data is sent before subsequent operations are performed.|
| [int32_t OH_UsbSerial_FlushInput(UsbSerial_Device *dev)](#oh_usbserial_flushinput) | Flushes the input buffer. The data in the buffer is flushed immediately. During the communication with the USB serial port device, especially in the debugging phase, disordered data packets or other exceptions may occur. In this case, you can call this API to clear errors at the receive end to restore the communication. This API does not affect the data to be sent in the output buffer.|
| [int32_t OH_UsbSerial_FlushOutput(UsbSerial_Device *dev)](#oh_usbserial_flushoutput) | Flushes the output buffer. The data in the buffer is flushed immediately. During the communication with the USB serial port device, especially in the debugging phase, disordered data packets or other exceptions may occur. You can call this API to clear errors at the transmit end to restore the communication. This API does not affect the received data in the input buffer.|

## Function Description

### OH_UsbSerial_Init()

```c
int32_t OH_UsbSerial_Init(void)
```

**Description**

Initializes the USB Serial DDK. This API must be called before any other USB Serial DDK APIs. It establishes communication with the DDK service and loads necessary driver resources. After using the DDK, call [OH_UsbSerial_Release](#oh_usbserial_release) to release it to avoid resource leaks.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18

**Returns**

| Type| Description                                                                                                                                                                                                                               |
| -- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK initialization fails.|

### OH_UsbSerial_Release()

```c
int32_t OH_UsbSerial_Release(void)
```

**Description**

Releases the USB Serial DDK. This function must be used together with [OH_UsbSerial_Init](#oh_usbserial_init). After the DDK is released, other USB Serial DDK methods cannot be called.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         The [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK is not initialized or has been released. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the device status.|

### OH_UsbSerial_Open()

```c
int32_t OH_UsbSerial_Open(uint64_t deviceId, uint8_t interfaceIndex, UsbSerial_Device **dev)
```

**Description**

Opens the USB serial port device based on the specified **deviceId** and **interfaceIndex**. This API establishes a connection with the specified USB serial port device and returns the device handle for follow-up procedures. After using the device, call [OH_UsbSerial_Close](#oh_usbserial_close) to close the device. Otherwise, device resources may not be correctly released.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name                             | Description                                        |
|----------------------------------|--------------------------------------------|
| uint64_t deviceId                | ID of the device to be operated, which can be obtained by calling [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices).                            |
| uint8_t interfaceIndex           | Interface index, which corresponds to **bInterfaceNumber** in the USB protocol.|
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) **dev | Device handle, which is an output parameter used to return the handle of the opened USB serial port device. After the handle is used, call [OH_UsbSerial_Close](#oh_usbserial_close) to release it.|

**Returns**

| Type| Description|
| -- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode): The parameter verification fails. The possible cause is that **dev** or ***dev** is null. Check the parameter validity.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK is not initialized. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the parameters and device status.<br>         [USB_SERIAL_DDK_MEMORY_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The memory is insufficient.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): An I/O exception occurs. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_DEVICE_NOT_FOUND](capi-usb-serial-types-h.md#usbserial_ddkretcode): The device or interface is not found.|

### OH_UsbSerial_Close()

```c
int32_t OH_UsbSerial_Close(UsbSerial_Device **dev)
```

**Description**

Closes the USB serial port device. This API releases the resources occupied by the device and must be used together with [OH_UsbSerial_Open](#oh_usbserial_open).

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) **dev | Device handle, which is an input and output parameter. After the device is closed, this pointer is set to null.|

**Returns**

| Type| Description|
| -- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode): The parameter verification fails. The possible cause is that **dev** or ***dev** is null. Check the parameter validity.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK is not initialized. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): An I/O exception occurs. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is invalid. Ensure that the device is properly started.|

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
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, which must be opened and obtained by calling [OH_UsbSerial_Open](#oh_usbserial_open).|
| uint8_t *buff | Buffer for reading data from the USB serial port device. The buffer must be allocated by the caller and its capacity must be greater than or equal to **bufferSize**.|
| uint32_t bufferSize | Buffer size.|
| uint32_t *bytesRead | Number of bytes that are actually read. If the block mode is set, the number of bytes that are actually read is returned only when it is equal to the value of **bufferSize**. If a timeout interval is set, the return value may be less than **bufferSize**.<br>                  For details, see [OH_UsbSerial_SetTimeout](#oh_usbserial_settimeout).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode): The parameter verification fails. Possible causes: 1. **dev** is a null pointer. 2. **buff** is a null pointer. 3. **bufferSize** is **0**. 4. **bytesRead** is a null pointer. Check the parameter validity.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK is not initialized. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the parameters and device status.<br>         [USB_SERIAL_DDK_MEMORY_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The buffer address is invalid.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): An I/O exception occurs. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is invalid. Ensure that the device is properly started.|

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
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, which must be opened and obtained by calling [OH_UsbSerial_Open](#oh_usbserial_open).|
| uint8_t *buff | Buffer whose data is written to the USB serial port device. The buffer must be allocated by the caller and its size must be greater than or equal to **bufferSize**.|
| uint32_t bufferSize | Buffer size.|
| uint32_t *bytesWritten | Number of bytes that are actually written. This parameter is valid only when the API returns a success message, and the value may be less than **bufferSize**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode): The parameter verification fails. Possible causes: 1. **dev** is a null pointer. 2. **buff** is a null pointer. 3. **bufferSize** is **0**. 4. **bytesWritten** is a null pointer. Check the parameter validity.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK is not initialized. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the parameters and device status.<br>[USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): An I/O exception occurs. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is invalid. Ensure that the device is properly started.|

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
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, which must be opened and obtained by calling [OH_UsbSerial_Open](#oh_usbserial_open).|
| uint32_t baudRate | Baud rate of the USB serial port device, in bit/s.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode): The parameter verification fails. Possible cause: The input **dev** is a null pointer. Check the parameter validity.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK is not initialized. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): An I/O exception occurs. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is invalid. Ensure that the device is properly started.|

### OH_UsbSerial_SetParams()

```c
int32_t OH_UsbSerial_SetParams(UsbSerial_Device *dev, UsbSerial_Params *params)
```

**Description**

Sets the parameters of the USB serial port device. If the parameters of the USB serial port device are not set to the default values (the data bit is **8**, the stop bit is **1**, and parity is disabled for data transfer), you only need to call this API to set the related parameters.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name                                                                    | Description|
|-------------------------------------------------------------------------| -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, which must be opened and obtained by calling [OH_UsbSerial_Open](#oh_usbserial_open).|
| [UsbSerial_Params](capi-serialddk-usbserial-params.md) *params                                            | USB serial port device parameters. For details, see [UsbSerial_Params](capi-serialddk-usbserial-params.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode): The parameter verification fails. Possible causes: 1. **dev** is a null pointer.<br>         2. **params** is a null pointer. Check the parameter validity.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK is not initialized. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): An I/O exception occurs. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is invalid. Ensure that the device is properly started.|

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
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, which must be opened and obtained by calling [OH_UsbSerial_Open](#oh_usbserial_open).|
| int timeout | Timeout interval for reading data from a USB serial port device. If the value range is (0, 25500] in milliseconds, the value is rounded off to the nearest 100 milliseconds and used as the actual timeout interval. For example, if the input value is **12321**, the effective timeout interval is 12300 milliseconds. If the value is **0**, data is returned immediately without waiting. If the value is **-1**, data is read in blocking mode. That is, data is returned only after the data of the specified length is read. For details, see [OH_UsbSerial_Read](#oh_usbserial_read). The value **0** is recommended in polling scenarios, the value range (0, 25500] is recommended when timeout control is required, and the value **-1** is recommended when all integer data must be read.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode): The parameter verification fails. Possible causes: 1. **dev** is a null pointer.<br>         2. **timeout** is less than **-1** or greater than **25500**. Check the parameter validity and timeout interval.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK is not initialized. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): An I/O exception occurs. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is invalid. Ensure that the device is properly started.|

### OH_UsbSerial_SetFlowControl()

```c
int32_t OH_UsbSerial_SetFlowControl(UsbSerial_Device *dev, UsbSerial_FlowControl flowControl)
```

**Description**

Sets flow control parameters. Flow control is used to manage the data transfer rate during communication with the USB serial port device to ensure that the sender does not send data that exceeds the processing capability of the receiver. If flow control is required, call this API to set flow control parameters. If this API is not called, flow control is disabled by default.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name                                                                                  | Description|
|---------------------------------------------------------------------------------------| -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev               | Device handle, which must be opened and obtained by calling [OH_UsbSerial_Open](#oh_usbserial_open).|
| [UsbSerial_FlowControl](capi-usb-serial-types-h.md#usbserial_flowcontrol) flowControl | Flow control mode. For details, see [UsbSerial_FlowControl](capi-usb-serial-types-h.md#usbserial_flowcontrol).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode): The parameter verification fails. Possible cause: The input **dev** is a null pointer. Check the parameter validity.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK is not initialized. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): An I/O exception occurs. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is invalid. Ensure that the device is properly started.|

### OH_UsbSerial_Flush()

```c
int32_t OH_UsbSerial_Flush(UsbSerial_Device *dev)
```

**Description**

Flushes the input and output buffers. The system waits until all data in the output buffer is sent. If a large amount of data is to be transmitted to the USB serial port device, the data may be buffered in the kernel for transmission. If the app closes the device or exits before all data is sent out, some data may be lost. You can call this API to ensure that all data is sent before subsequent operations are performed.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, which must be opened and obtained by calling [OH_UsbSerial_Open](#oh_usbserial_open).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode): The parameter verification fails. Possible cause: The input **dev** is a null pointer. Check the parameter validity.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK is not initialized. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): An I/O exception occurs. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is invalid. Ensure that the device is properly started.|

### OH_UsbSerial_FlushInput()

```c
int32_t OH_UsbSerial_FlushInput(UsbSerial_Device *dev)
```

**Description**

Flushes the input buffer. The data in the buffer is flushed immediately. During the communication with the USB serial port device, especially in the debugging phase, disordered data packets or other exceptions may occur. In this case, you can call this API to clear errors at the receive end to restore the communication. This API does not affect the data to be sent in the output buffer.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, which must be opened and obtained by calling [OH_UsbSerial_Open](#oh_usbserial_open).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode): The parameter verification fails. Possible cause: The input **dev** is a null pointer. Check the parameter validity.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK is not initialized. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): An I/O exception occurs. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is invalid. Ensure that the device is properly started.|

### OH_UsbSerial_FlushOutput()

```c
int32_t OH_UsbSerial_FlushOutput(UsbSerial_Device *dev)
```

**Description**

Flushes the output buffer. The data in the buffer is flushed immediately. During the communication with the USB serial port device, especially in the debugging phase, disordered data packets or other exceptions may occur. You can call this API to clear errors at the transmit end to restore the communication. This API does not affect the received data in the input buffer.

**Required permissions**: ohos.permission.ACCESS_DDK_USB_SERIAL

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) *dev | Device handle, which must be opened and obtained by calling [OH_UsbSerial_Open](#oh_usbserial_open).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_SERIAL_DDK_SUCCESS](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is successful.<br>         [USB_SERIAL_DDK_NO_PERM](capi-usb-serial-types-h.md#usbserial_ddkretcode): The permission verification fails. Check whether you have obtained the **ohos.permission.ACCESS_DDK_USB_SERIAL** permission.<br>         [USB_SERIAL_DDK_INVALID_PARAMETER](capi-usb-serial-types-h.md#usbserial_ddkretcode): The parameter verification fails. Possible cause: The input **dev** is a null pointer. Check the parameter validity.<br>         [USB_SERIAL_DDK_INIT_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): The DDK is not initialized. Call [OH_UsbSerial_Init](#oh_usbserial_init) to initialize the DDK first.<br>         The [USB_SERIAL_DDK_SERVICE_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode) DDK service fails to be executed. Check the parameters and device status.<br>         [USB_SERIAL_DDK_IO_ERROR](capi-usb-serial-types-h.md#usbserial_ddkretcode): An I/O exception occurs. Check the device specifications and parameters.<br>         [USB_SERIAL_DDK_INVALID_OPERATION](capi-usb-serial-types-h.md#usbserial_ddkretcode): The operation is invalid. Ensure that the device is properly started.|
