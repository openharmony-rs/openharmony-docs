# usb_ddk_types.h

## Overview

Provides the enumerated variables, structures, and macros used in USB DDK APIs.

**Library**: libusb_ndk.z.so

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md) | \_\_attribute\_\_((aligned(8))) UsbControlRequestSetup | Setup data for control transfer. It corresponds to <b>Setup Data</b> in the USB protocol. |
| [UsbDeviceDescriptor](capi-usbddk-usbdevicedescriptor.md) | \_\_attribute\_\_((aligned(8))) UsbDeviceDescriptor | Defines standard device descriptors, which correspond to **Standard Device Descriptor** in the USB protocol. |
| [UsbConfigDescriptor](capi-usbddk-usbconfigdescriptor.md) | \_\_attribute\_\_((packed)) UsbConfigDescriptor | Defines standard configuration descriptors, which correspond to **Standard Configuration Descriptor** in the USB protocol. |
| [UsbInterfaceDescriptor](capi-usbddk-usbinterfacedescriptor.md) | \_\_attribute\_\_((packed)) UsbInterfaceDescriptor | Defines standard interface descriptors, which correspond to **Standard Interface Descriptor** in the USB protocol. |
| [UsbEndpointDescriptor](capi-usbddk-usbendpointdescriptor.md) | \_\_attribute\_\_((packed)) UsbEndpointDescriptor | Defines standard endpoint descriptors, which correspond to **Standard Endpoint Descriptor** in the USB protocol. |
| [UsbDdkEndpointDescriptor](capi-usbddk-usbddkendpointdescriptor.md) | UsbDdkEndpointDescriptor | Defines endpoint descriptors. |
| [UsbDdkInterfaceDescriptor](capi-usbddk-usbddkinterfacedescriptor.md) | UsbDdkInterfaceDescriptor | Defines USB interface descriptors. |
| [UsbDdkInterface](capi-usbddk-usbddkinterface.md) | UsbDdkInterface | Defines a USB DDK API, which is a collection of alternate settings for a particular USB interface. |
| [UsbDdkConfigDescriptor](capi-usbddk-usbddkconfigdescriptor.md) | UsbDdkConfigDescriptor | Defines configuration descriptors. |
| [UsbRequestPipe](capi-usbddk-usbrequestpipe.md) | \_\_attribute\_\_((aligned(8))) UsbRequestPipe | Defines a USB request pipe. |
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) | UsbDeviceMemMap | Device memory map created by calling {@link OH_Usb_CreateDeviceMemMap}. A buffer using the device memory map can improve data transmission performance. |
| [Usb_DeviceArray](capi-usbddk-usb-devicearray.md) | Usb_DeviceArray | Defines the device ID list, which is used to store the device IDs and device quantity obtained using {@link OH_Usb_GetDevices}. |
| [Usb_NonRootHubArray](capi-usbddk-usb-nonroothubarray.md) | Usb_NonRootHubArray | The list of non-root hubs, which is used to store the non-root hub IDs and quantity obtained using {@link OH_Usb_GetNonRootHubs}. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [UsbDdkErrCode](#usbddkerrcode) | UsbDdkErrCode | USB DDK error code definitions. |

## Enum type description

### UsbDdkErrCode

```c
enum UsbDdkErrCode
```

**Description**

USB DDK error code definitions.

**Since**: 10

| Enum item | Description |
| -- | -- |
| USB_DDK_SUCCESS = 0 | Operation succeeded. |
| USB_DDK_FAILED = -1 |  |
| USB_DDK_NO_PERM = 201 |  |
| USB_DDK_INVALID_PARAMETER = 401 | Invalid parameter. The value is **-2** before API version 16. |
| USB_DDK_MEMORY_ERROR = 27400001 | Memory errors, such as insufficient memory, memory data copy failure, or memory allocation failure. The value is **-3** before API version 16. |
| USB_DDK_NULL_PTR = -5 |  |
| USB_DDK_DEVICE_BUSY = -6 |  |
| USB_DDK_INVALID_OPERATION = 27400002 | Invalid operation. The value is **-4** before API version 16. |
| USB_DDK_IO_FAILED = 27400003 |  |
| USB_DDK_TIMEOUT = 27400004 | Transmission timeout. The value is **-7** before API version 16. |


