# OH_UsbManager_UsbInterface

```c
typedef struct OH_UsbManager_UsbInterface {...} OH_UsbManager_UsbInterface
```

## Overview

Defines a USB interface. One [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) can contain <br>multiple OH_UsbManager_UsbInterface instances, each providing a specific function.

**Since**: 26.1.0

**Related module**: [UsbManager](capi-usbmanager.md)

**Header file**: [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t id | Unique ID of the USB interface.<br>**Since**: 26.1.0 |
| uint8_t protocol | Interface protocol.<br>**Since**: 26.1.0 |
| uint8_t clazz | Interface class.<br>**Since**: 26.1.0 |
| uint8_t subClass | Interface subclass.<br>**Since**: 26.1.0 |
| uint8_t alternateSetting | Alternate setting number of this USB interface, as defined in the USB <br>interface descriptor. Value 0 indicates the default alternate setting.<br>**Since**: 26.1.0 |
| const char *name | Interface name.<br>**Since**: 26.1.0 |
| [OH_UsbManager_UsbEndpoint](capi-usbmanager-oh-usbmanager-usbendpoint.md) *endpoints | Endpoints that belong to the USB interface.<br>**Since**: 26.1.0 |
| uint32_t endpointCount | Number of endpoints in the interface.<br>**Since**: 26.1.0 |


