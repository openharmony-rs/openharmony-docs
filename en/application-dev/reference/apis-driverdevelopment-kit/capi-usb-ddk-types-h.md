# usb_ddk_types.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

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
| [UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md) | UsbControlRequestSetup | Setup data for control transfer. It corresponds to **Setup Data** in the USB protocol.|
| [UsbDeviceDescriptor](capi-usbddk-usbdevicedescriptor.md) | UsbDeviceDescriptor | Defines standard device descriptors, which correspond to **Standard Device Descriptor** in the USB protocol.|
| [UsbConfigDescriptor](capi-usbddk-usbconfigdescriptor.md) | UsbConfigDescriptor | Defines standard configuration descriptors, which correspond to **Standard Configuration Descriptor** in the USB protocol.|
| [UsbInterfaceDescriptor](capi-usbddk-usbinterfacedescriptor.md) | UsbInterfaceDescriptor | Defines standard interface descriptors, which correspond to **Standard Interface Descriptor** in the USB protocol.|
| [UsbEndpointDescriptor](capi-usbddk-usbendpointdescriptor.md) | UsbEndpointDescriptor | Defines standard endpoint descriptors, which correspond to **Standard Endpoint Descriptor** in the USB protocol.|
| [UsbDdkEndpointDescriptor](capi-usbddk-usbddkendpointdescriptor.md) | UsbDdkEndpointDescriptor | Defines endpoint descriptors, including standard endpoint descriptors and descriptors that are not parsed.|
| [UsbDdkInterfaceDescriptor](capi-usbddk-usbddkinterfacedescriptor.md) | UsbDdkInterfaceDescriptor | Defines interface descriptors, including standard interface descriptors and endpoint descriptors.|
| [UsbDdkInterface](capi-usbddk-usbddkinterface.md) | UsbDdkInterface | Defines a USB DDK API, which is a collection of alternate settings for a particular USB interface.|
| [UsbDdkConfigDescriptor](capi-usbddk-usbddkconfigdescriptor.md) | UsbDdkConfigDescriptor | Defines configuration descriptors, including standard configuration descriptors and interface descriptors.|
| [UsbRequestPipe](capi-usbddk-usbrequestpipe.md) | UsbRequestPipe | Defines a request pipe, which is actually a USB data transfer request. It describes the basic configuration parameters for USB data transfer, including the interface handle, endpoint address, and timeout interval. This API applies to scenarios where USB data transfer is required.|
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) | UsbDeviceMemMap | Defines the device memory map created by calling [OH_Usb_CreateDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_createdevicememmap). A buffer using the device memory map can provide better data transfer performance.|
| [Usb_DeviceArray](capi-usbddk-usb-devicearray.md) | Usb_DeviceArray | Defines the device ID array, which is used to store the device IDs and device quantity obtained using [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices). After using the structure, you must release the memory allocated for the device ID array. Otherwise, resource leaks may occur.|
| [Usb_NonRootHubArray](capi-usbddk-usb-nonroothubarray.md) | Usb_NonRootHubArray | Defines the non-root hub array, which is used to store the non-root hub IDs and quantity obtained using [OH_Usb_GetNonRootHubs](capi-usb-ddk-api-h.md#oh_usb_getnonroothubs). After using the structure, you must release the memory allocated for the non-root hub ID array. Otherwise, resource leaks may occur.|

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
| USB_DDK_NO_PERM = 201 | No permission. Ensure that you have obtained the **ohos.permission.ACCESS_DDK_USB** permission.<br> **Since**: 14|
| USB_DDK_INVALID_PARAMETER = 401 | Invalid parameter. Check the validity of the input parameter, including whether the pointer is null and whether the value range is valid. The value is **-2** in versions earlier than API version 16.|
| USB_DDK_MEMORY_ERROR = 27400001 | Memory-related error, for example, insufficient memory, memory data copy failure, or memory application failure. Check whether the available system memory is sufficient and whether the memory operation parameters are correct. The value is **-3** in versions earlier than API version 16.|
| USB_DDK_INVALID_OPERATION = 27400002 | Invalid operation, for example, calling an API before the device is initialized or performing an operation when the device is in an incorrect state. Check whether the DDK has been initialized and whether the API handle is valid. The value is **-4** in versions earlier than API version 16.|
| USB_DDK_NULL_PTR = -5 | Null pointer error. For example, the input pointer parameter is null. Check whether the input pointer parameter is valid.<br> **Deprecated from**: 16|
| USB_DDK_DEVICE_BUSY = -6 | The device is busy. For example, the device is performing other operations or the device resources are occupied. Wait until the device is idle and try again, or release the occupied device resources.<br> **Deprecated from**: 16|
| USB_DDK_IO_FAILED = 27400003 | Device I/O operation failure. Check whether the device connection is normal and whether the device supports the operation.<br> **Since**: 14|
| USB_DDK_TIMEOUT = 27400004 | Transfer timed out. Check whether the device response is normal or increase the timeout interval. The value is **-7** in versions earlier than API version 16.|
