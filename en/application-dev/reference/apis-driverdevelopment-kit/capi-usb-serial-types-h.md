# usb_serial_types.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

## Overview

Provides the enumeration types and structures used in USB Serial DDK APIs. It is used for USB serial port driver development, simplifying operations such as parameter configuration, return code processing, and flow control for serial port devices, and improving driver development efficiency.

**File to include**: <usb_serial/usb_serial_types.h>

**Library:** libusb_serial_ndk.z.so

**System capability**: SystemCapability.Driver.UsbSerial.Extension

**Since**: 18

**Related module**: [USBSerialDDK](capi-serialddk.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [UsbSerial_Params](capi-serialddk-usbserial-params.md) | UsbSerial_Params | Defines the USB serial port parameters for the USB Serial DDK, which are used for configuring the communication parameters of the USB-to-serial device. The parameter configuration must be consistent with that of the target communication device. Otherwise, the communication may fail. It is commonly used in scenarios where communication with devices through the USB serial port is required, such as industrial control devices, debugging tools, and sensor data collection.|
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) | UsbSerial_Device | Defines the data structures for the USB serial port device (opaque). You can obtain this structure instance by calling the [OH_UsbSerial_Open](capi-usb-serial-api-h.md#oh_usbserial_open) API.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [UsbSerial_DdkRetCode](#usbserial_ddkretcode) | UsbSerial_DdkRetCode | Defines the return codes used by the USB Serial DDK.|
| [UsbSerial_FlowControl](#usbserial_flowcontrol) | UsbSerial_FlowControl | Defines the flow control mode for the USB Serial DDK. When using the USB serial port for data transfer, you need to select a proper flow control mode based on the communication scenario. For example, in high-speed and large-volume data transmission scenarios, hardware flow control is recommended to avoid data loss. In low-speed or scenarios that do not require high real-time performance, software flow control can be used. In short-range and reliable point-to-point communication scenarios, no flow control can be selected.|
| [UsbSerial_Parity](#usbserial_parity) | UsbSerial_Parity | Defines the enums of the parity parameter used by the USB Serial DDK. When configuring the USB serial port communication parameters, you need to select a proper parity mode based on the reliability requirements of data transmission. For example, in industrial control scenarios that require high data integrity, it is recommended that odd or even parity be used to detect transfer errors. In environments with high noise interference, parity can help recognize error data. In short-range and reliable communication scenarios, no parity can be selected to improve transfer efficiency.|

## Enum Description

### UsbSerial_DdkRetCode

```c
enum UsbSerial_DdkRetCode
```

**Description**

Defines the return codes used by the USB Serial DDK.

**Since**: 18

| Enum| Description|
| -- | -- |
| USB_SERIAL_DDK_NO_PERM = 201 | No access permission. Ensure that the required permissions are declared in the **module.json5** file of the app.|
| USB_SERIAL_DDK_INVALID_PARAMETER = 401 | Invalid parameter. Ensure that the input parameter value is within the valid range. For details, see the parameter description of the related API.|
| USB_SERIAL_DDK_SUCCESS = 31600000 | Operation success.|
| USB_SERIAL_DDK_INVALID_OPERATION = 31600001 | Invalid operation. For example, an invalid device handle is used. Ensure that the device is properly opened.|
| USB_SERIAL_DDK_INIT_ERROR = 31600002 | Initialization error. Initialize the DDK service first.|
| USB_SERIAL_DDK_SERVICE_ERROR = 31600003 | Service error. Check whether the DDK service status and API calling logic are normal.|
| USB_SERIAL_DDK_MEMORY_ERROR = 31600004 | Memory-related errors, such as insufficient memory, memory data replication failure, or memory request failure. You are advised to optimize memory parameters and release unnecessary resources in a timely manner.|
| USB_SERIAL_DDK_IO_ERROR = 31600005 | I/O error. Check whether the device connection is normal, whether the transmission cable is intact, and whether the device is working properly.|
| USB_SERIAL_DDK_DEVICE_NOT_FOUND = 31600006 | Device not found. Check the parameters and device connection status.|

### UsbSerial_FlowControl

```c
enum UsbSerial_FlowControl
```

**Description**

Defines the flow control mode for the USB Serial DDK. When using the USB serial port for data transfer, you need to select a proper flow control mode based on the communication scenario. For example, in high-speed and large-volume data transmission scenarios, hardware flow control is recommended to avoid data loss. In low-speed or scenarios that do not require high real-time performance, software flow control can be used. In short-range and reliable point-to-point communication scenarios, no flow control can be selected.

**Since**: 18

| Enum| Description|
| -- | -- |
| USB_SERIAL_NO_FLOW_CONTROL = 0 | No flow control. This mode is applicable to low-speed data transfer or scenarios where flow control is not required. However, data loss may occur.|
| USB_SERIAL_SOFTWARE_FLOW_CONTROL = 1 | Software flow control. XON/XOFF control is applicable to devices that do not support hardware flow control.|
| USB_SERIAL_HARDWARE_FLOW_CONTROL = 2 | Hardware flow control. RTS/CTS signal lines are used, which are applicable to high-speed data transfer and provide high reliability.|

### UsbSerial_Parity

```c
enum UsbSerial_Parity
```

**Description**

Defines the enums of the parity parameter used by the USB Serial DDK. When configuring the USB serial port communication parameters, you need to select a proper parity mode based on the reliability requirements of data transmission. For example, in industrial control scenarios that require high data integrity, it is recommended that odd or even parity be used to detect transfer errors. In environments with high noise interference, parity can help recognize error data. In short-range and reliable communication scenarios, no parity can be selected to improve transfer efficiency.

**Since**: 18

| Enum| Description|
| -- | -- |
| USB_SERIAL_PARITY_NONE = 0 | No parity. In short-range and reliable communication scenarios, no parity can be selected to improve transfer efficiency.|
| USB_SERIAL_PARITY_ODD = 1 | Odd parity. This mode is applicable to scenarios that require high data integrity.|
| USB_SERIAL_PARITY_EVEN = 2 | Even parity. This mode is applicable to scenarios that require high data integrity.|
