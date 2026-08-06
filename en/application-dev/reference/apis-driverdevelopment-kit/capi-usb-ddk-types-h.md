# usb_ddk_types.h

<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a30d46aa87725f954a8669c5a6106a0f5fa2de6d translatedAt=2026-06-22T10:49:18.997Z pushedAt=2026-06-22T11:21:11.420Z -->

## Overview

Provides the enumerated variables, structures, and macros used in USB DDK APIs.

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
| [UsbDdkEndpointDescriptor](capi-usbddk-usbddkendpointdescriptor.md) | UsbDdkEndpointDescriptor | Endpoint descriptors.|
| [UsbDdkInterfaceDescriptor](capi-usbddk-usbddkinterfacedescriptor.md) | UsbDdkInterfaceDescriptor | USB interface descriptors.|
| [UsbDdkInterface](capi-usbddk-usbddkinterface.md) | UsbDdkInterface | USB DDK API, which is a collection of alternate settings for a particular USB interface.|
| [UsbDdkConfigDescriptor](capi-usbddk-usbddkconfigdescriptor.md) | UsbDdkConfigDescriptor | Configuration descriptors.|
| [UsbRequestPipe](capi-usbddk-usbrequestpipe.md) | UsbRequestPipe | Request pipe. |
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) | UsbDeviceMemMap | Device memory map created by calling [OH_Usb_CreateDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_createdevicememmap). A buffer using the device memory map can provide better performance.|
| [Usb_DeviceArray](capi-usbddk-usb-devicearray.md) | Usb_DeviceArray | Device ID list, which is used to store the device IDs and device quantity obtained using [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices).|
| [Usb_NonRootHubArray](capi-usbddk-usb-nonroothubarray.md) | Usb_NonRootHubArray | Non-root hub list, which is used to store the non-root hub IDs and quantity obtained using [OH_Usb_GetNonRootHubs](capi-usb-ddk-api-h.md#oh_usb_getnonroothubs).|

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
| USB_DDK_NO_PERM = 201 | No permission.<br> **Since**: 14|
| USB_DDK_INVALID_PARAMETER = 401 | Invalid parameter. The value is **-2** before API version 16.|
| USB_DDK_MEMORY_ERROR = 27400001 | Memory errors, such as insufficient memory, memory data copy failure, or memory allocation failure. The value is **-3** before API version 16.|
| USB_DDK_INVALID_OPERATION = 27400002 | Invalid operation. The value is **-4** before API version 16.|
| USB_DDK_NULL_PTR = -5 | Null pointer.<br> **Deprecated from**: 16|
| USB_DDK_DEVICE_BUSY = -6 | Device busy.<br> **Deprecated from**: 16|
| USB_DDK_IO_FAILED = 27400003 | Device I/O operation failure.<br> **Since**: 14|
| USB_DDK_TIMEOUT = 27400004 | Transmission timeout. The value is **-7** before API version 16.|