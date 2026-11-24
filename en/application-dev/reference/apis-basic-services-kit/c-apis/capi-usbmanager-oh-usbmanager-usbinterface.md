# OH_UsbManager_UsbInterface

```c
typedef struct OH_UsbManager_UsbInterface {...} OH_UsbManager_UsbInterface
```

## Overview

Defines a USB interface. One [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) can contain <br>multiple OH_UsbManager_UsbInterface instances, each providing a specific function.

<!--Device-struct OH_UsbManager_UsbInterface {...}--><!--Device-struct OH_UsbManager_UsbInterface {...}-End-->

**System capability**: SystemCapability.USB.USBManager

**Since**: 26.0.1

**Related module**: [UsbManager](capi-basic-services-kit-usbmanager.md)

**Header file**: [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t id | Unique ID of the USB interface.<br>**Since**: 26.0.1<br><!--Device-uint8_t id--><!--Device-uint8_t id-End--> |
| uint8_t protocol | Interface protocol.<br>**Since**: 26.0.1<br><!--Device-uint8_t protocol--><!--Device-uint8_t protocol-End--> |
| uint8_t clazz | Interface class.<br>**Since**: 26.0.1<br><!--Device-uint8_t clazz--><!--Device-uint8_t clazz-End--> |
| uint8_t subClass | Interface subclass.<br>**Since**: 26.0.1<br><!--Device-uint8_t subClass--><!--Device-uint8_t subClass-End--> |
| uint8_t alternateSetting | Alternate setting number of this USB interface, as defined in the USB <br>interface descriptor. Value 0 indicates the default alternate setting.<br>**Since**: 26.0.1<br><!--Device-uint8_t alternateSetting--><!--Device-uint8_t alternateSetting-End--> |
| const char *name | Interface name.<br>**Since**: 26.0.1<br><!--Device-const char *name--><!--Device-const char *name-End--> |
| [OH_UsbManager_UsbEndpoint](capi-usbmanager-oh-usbmanager-usbendpoint.md) *endpoints | Endpoints that belong to the USB interface.<br>**Since**: 26.0.1<br><!--Device-OH_UsbManager_UsbEndpoint *endpoints--><!--Device-OH_UsbManager_UsbEndpoint *endpoints-End--> |
| uint32_t endpointCount | Number of endpoints in the interface.<br>**Since**: 26.0.1<br><!--Device-uint32_t endpointCount--><!--Device-uint32_t endpointCount-End--> |


