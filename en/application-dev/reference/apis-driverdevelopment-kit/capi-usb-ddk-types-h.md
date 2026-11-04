# usb_ddk_types.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-04T03:58:55.915Z pushedAt=2026-11-04T10:12:50.029Z nl=1 -->

## Overview

Provides the enumeration types and structures used in USB DDK APIs, including core data structures such as USB device description, control transfer, and request pipe, to facilitate driver development.

**File to include**: <usb/usb_ddk_types.h>

**Library**: libusb_ndk.z.so

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md) | UsbControlRequestSetup | Setup data for control transfer. It corresponds to **Setup Data** in the USB protocol. |
| [UsbDeviceDescriptor](capi-usbddk-usbdevicedescriptor.md) | UsbDeviceDescriptor | Standard device descriptor, which corresponds to **Standard Device Descriptor** in the USB protocol. |
| [UsbConfigDescriptor](capi-usbddk-usbconfigdescriptor.md) | UsbConfigDescriptor | Standard configuration descriptor, which corresponds to **Standard Configuration Descriptor** in the USB protocol. |
| [UsbInterfaceDescriptor](capi-usbddk-usbinterfacedescriptor.md) | UsbInterfaceDescriptor | Standard interface descriptor, which corresponds to **Standard Interface Descriptor** in the USB protocol. |
| [UsbEndpointDescriptor](capi-usbddk-usbendpointdescriptor.md) | UsbEndpointDescriptor | Standard endpoint descriptor, which corresponds to **Standard Endpoint Descriptor** in the USB protocol. |
| [UsbDdkEndpointDescriptor](capi-usbddk-usbddkendpointdescriptor.md) | UsbDdkEndpointDescriptor | Describes the endpoint descriptor, including the standard endpoint descriptor and unparsed descriptor information. |
| [UsbDdkInterfaceDescriptor](capi-usbddk-usbddkinterfacedescriptor.md) | UsbDdkInterfaceDescriptor | Describes the interface descriptor, including the standard interface descriptor and endpoint descriptors. |
| [UsbDdkInterface](capi-usbddk-usbddkinterface.md) | UsbDdkInterface | USB DDK API, which is a collection of alternate settings for a particular USB interface.|
| [UsbDdkConfigDescriptor](capi-usbddk-usbddkconfigdescriptor.md) | UsbDdkConfigDescriptor | Describes the configuration descriptor, including the standard configuration descriptor and interface descriptors. |
| [UsbRequestPipe](capi-usbddk-usbrequestpipe.md) | UsbRequestPipe | Defines a request pipe, which is actually a USB data transfer request. It describes the basic configuration parameters for USB data transfer, including the interface handle, endpoint address, and timeout interval. This API applies to scenarios where USB data transfer is required. |
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) | UsbDeviceMemMap | Defines the device memory map created by calling [OH_Usb_CreateDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_createdevicememmap). A buffer using the device memory map can provide better data transfer performance. |
| [Usb_DeviceArray](capi-usbddk-usb-devicearray.md) | Usb_DeviceArray | Defines the device ID array, which is used to store the device IDs and device quantity obtained using [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices). After using the structure, you must release the memory allocated for the device ID array. Otherwise, resource leaks may occur. |
| [Usb_NonRootHubArray](capi-usbddk-usb-nonroothubarray.md) | Usb_NonRootHubArray | Defines the non-root hub array, which is used to store the non-root hub IDs and quantity obtained using [OH_Usb_GetNonRootHubs](capi-usb-ddk-api-h.md#oh_usb_getnonroothubs). After using the structure, you must release the memory allocated for the non-root hub ID array. Otherwise, resource leaks may occur. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [UsbDdkErrCode](#usbddkerrcode) | UsbDdkErrCode | Enumerates the USB DDK error code definitions.|

## Enum Description

### UsbDdkErrCode

```c
enum UsbDdkErrCode
```

**Description**

Enumerates the USB DDK error code definitions.

**Since**: 10

| Enum| Description|
| -- | -- |
| USB_DDK_SUCCESS = 0 | Operation succeeded.|
| USB_DDK_FAILED = -1 | Operation failed.<br> **Deprecated from**: 16|
| USB_DDK_NO_PERM = 201 | No permission. Check that the application has obtained the ohos.permission.ACCESS_DDK_USB permission.<br> **Since:** 14 |
| USB_DDK_INVALID_PARAMETER = 401 | Invalid parameter. Check the validity of the input parameters, including whether the pointer is null and whether the value range is valid. Before API version 16, the value is -2. |
| USB_DDK_MEMORY_ERROR = 27400001 | Memory-related error, including insufficient memory, memory data copy failure, and memory allocation failure. Check whether the available system memory is sufficient and whether the memory operation parameters are correct. Before API version 16, the value is -3. |
| USB_DDK_INVALID_OPERATION = 27400002 | Invalid operation, such as calling an API before the device is initialized or performing an operation in an incorrect state. Check whether the DDK is initialized and whether the API handle is valid. Before API version 16, the value is -4. |
| USB_DDK_NULL_PTR = -5 | Null pointer exception, such as an empty pointer parameter passed in. Check whether the input pointer parameter is valid. <br> **Deprecated Since:** 16 |
| USB_DDK_DEVICE_BUSY = -6 | The device is busy, for example, the device is performing another operation or its resources are occupied. Wait until the device is idle and retry, or release the occupied device resources. <br> **Deprecated Since:** 16 |
| USB_DDK_IO_FAILED = 27400003 | Device I/O operation failed. Check whether the device connection is normal and whether the device supports the operation.<br> **Since:** 14 |
| USB_DDK_TIMEOUT = 27400004 | Transfer timed out. Check whether the device response is normal or increase the timeout period appropriately. Before API version 16, the value is -7. |


