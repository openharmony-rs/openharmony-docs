# usb_serial_types.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-04T04:00:50.002Z pushedAt=2026-11-04T10:12:50.031Z nl=1 -->

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
| [UsbSerial_Params](capi-serialddk-usbserial-params.md) | UsbSerial_Params | Defines the USB serial port parameters for the USB Serial DDK, which are used for configuring the communication parameters of the USB-to-serial device. The parameter configuration must be consistent with that of the target communication device. Otherwise, the communication may fail. It is commonly used in scenarios where communication with devices through the USB serial port is required, such as industrial control devices, debugging tools, and sensor data collection. |
| [UsbSerial_Device](capi-serialddk-usbserial-devicehandle.md) | UsbSerial_Device | Defines the data structures for the USB serial port device (opaque), which is used to indicate the USB serial port device. You can obtain this structure instance by calling the [OH_UsbSerial_Open](capi-usb-serial-api-h.md#oh_usbserial_open) API. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [UsbSerial_DdkRetCode](#usbserial_ddkretcode) | UsbSerial_DdkRetCode | Defines the return codes used by the USB Serial DDK.|
| [UsbSerial_FlowControl](#usbserial_flowcontrol) | UsbSerial_FlowControl | Enumerates the flow control modes in the USB Serial DDK. When using a USB serial port for data transmission, select an appropriate flow control mode based on the communication scenario. For example, in high-speed, large-volume data transmission scenarios, hardware flow control is recommended to avoid data loss; in low-speed scenarios or scenarios with low real-time requirements, software flow control can be used; in short-distance, reliable point-to-point communication scenarios, no flow control can be selected. |
| [UsbSerial_Parity](#usbserial_parity) | UsbSerial_Parity | Enumerates the parity parameters used by the USB Serial DDK. When configuring USB serial port communication parameters, select an appropriate parity mode based on the reliability requirements of data transmission. For example, in industrial control scenarios with high data integrity requirements, odd parity or even parity is recommended to detect transmission errors; in high-noise interference environments, parity helps identify erroneous data; in short-distance, reliable communication scenarios, no parity can be selected to improve transmission efficiency. |

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
| USB_SERIAL_DDK_NO_PERM = 201 | Permission denied. Ensure that the application has declared the required permission in the module.json5 file. |
| USB_SERIAL_DDK_INVALID_PARAMETER = 401 | Invalid parameter. Ensure that the passed parameter value is within the valid range. For details, see the parameter description of the related API. |
| USB_SERIAL_DDK_SUCCESS = 31600000 | Operation success.|
| USB_SERIAL_DDK_INVALID_OPERATION = 31600001 | Invalid operation, for example, an invalid device handle is used. Check and ensure that the device is in the normally opened state. |
| USB_SERIAL_DDK_INIT_ERROR = 31600002 | Initialization failed. Initialize the DDK service first. |
| USB_SERIAL_DDK_SERVICE_ERROR = 31600003 | Service error. Check whether the DDK service status and the API call logic are normal. |
| USB_SERIAL_DDK_MEMORY_ERROR = 31600004 | Memory-related error, for example, insufficient memory, memory data copy failure, or memory allocation failure. Optimize the memory parameters and release the resources that are no longer needed in a timely manner. |
| USB_SERIAL_DDK_IO_ERROR = 31600005 | I/O error. Check whether the device connection is normal, whether the transmission cable is intact, and whether the device is in the normal working state. |
| USB_SERIAL_DDK_DEVICE_NOT_FOUND = 31600006 | Device not found. Check the parameters and the device connection status. |

### UsbSerial_FlowControl

```c
enum UsbSerial_FlowControl
```

**Description**

Defines the flow control in the USB Serial DDK. When using a USB serial port for data transmission, select an appropriate flow control mode based on the communication scenario. For example, in high-speed, large-volume data transmission scenarios, hardware flow control is recommended to avoid data loss; in low-speed scenarios or scenarios with low real-time requirements, software flow control can be used; in short-distance, reliable point-to-point communication scenarios, no flow control can be selected.

**Since**: 18

| Enum| Description|
| -- | -- |
| USB_SERIAL_NO_FLOW_CONTROL = 0 | No flow control. Suitable for low-speed transmission or scenarios where flow control is not required, but may cause data loss. |
| USB_SERIAL_SOFTWARE_FLOW_CONTROL = 1 | Software flow control. Uses XON/XOFF characters for control, suitable for devices that do not support hardware flow control. |
| USB_SERIAL_HARDWARE_FLOW_CONTROL = 2 | Hardware flow control. Uses RTS/CTS signal lines, suitable for high-speed data transmission with high reliability. |

### UsbSerial_Parity

```c
enum UsbSerial_Parity
```

**Description**

Defines the parity parameter enumeration used by the USB Serial DDK. When configuring USB serial port communication parameters, select an appropriate parity mode based on the reliability requirements of data transmission. For example, in industrial control scenarios with high data integrity requirements, odd parity or even parity is recommended to detect transmission errors; in high-noise interference environments, parity can help identify erroneous data; in short-distance, reliable communication scenarios, no parity can be selected to improve transmission efficiency.

**Since**: 18

| Enum| Description|
| -- | -- |
| USB_SERIAL_PARITY_NONE = 0 | No verification. In short-distance and reliable communication scenarios, no verification can be selected to improve transmission efficiency. |
| USB_SERIAL_PARITY_ODD = 1 | Odd parity. Applicable to scenarios that require high data integrity. |
| USB_SERIAL_PARITY_EVEN = 2 | Even parity. Applicable to scenarios that require high data integrity. |


