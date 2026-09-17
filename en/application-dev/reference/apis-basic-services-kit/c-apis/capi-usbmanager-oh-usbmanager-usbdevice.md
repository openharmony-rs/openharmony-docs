# OH_UsbManager_UsbDevice

```c
typedef struct OH_UsbManager_UsbDevice {...} OH_UsbManager_UsbDevice
```

## Overview

Defines a flat representation of a USB device.

**Since**: 26.1.0

**Related module**: [UsbManager](capi-usbmanager.md)

**Header file**: [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t busNum | Bus number of the USB device.<br>**Since**: 26.1.0 |
| uint8_t devAddress | Device address on the bus.<br>**Since**: 26.1.0 |
| const char *name | Device name, in the format of <bus number>-<device address>.<br>**Since**: 26.1.0 |
| const char *manufacturerName | Manufacturer name.<br>**Since**: 26.1.0 |
| const char *productName | Product name.<br>**Since**: 26.1.0 |
| const char *version | Device version.<br>**Since**: 26.1.0 |
| uint16_t vendorId | Vendor ID.<br>**Since**: 26.1.0 |
| uint16_t productId | Product ID.<br>**Since**: 26.1.0 |
| uint8_t clazz | Device class.<br>**Since**: 26.1.0 |
| uint8_t subClass | Device subclass.<br>**Since**: 26.1.0 |
| uint8_t protocol | Device protocol.<br>**Since**: 26.1.0 |
| [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) *configs | Device configuration descriptor information.<br>**Since**: 26.1.0 |
| uint32_t configCount | Number of configurations in the device.<br>**Since**: 26.1.0 |


