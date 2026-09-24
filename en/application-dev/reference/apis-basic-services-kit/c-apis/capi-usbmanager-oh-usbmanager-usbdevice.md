# OH_UsbManager_UsbDevice

```c
typedef struct OH_UsbManager_UsbDevice {...} OH_UsbManager_UsbDevice
```

## Overview

Defines a flat representation of a USB device.

**System capability**: SystemCapability.USB.USBManager

**Since**: 26.0.1

**Related module**: [UsbManager](capi-usbmanager.md)

**Header file**: [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t busNum | Bus number of the USB device.<br>**Since**: 26.0.1 |
| uint8_t devAddress | Device address on the bus.<br>**Since**: 26.0.1 |
| const char *name | Device name, in the format of <bus number>-<device address>.<br>**Since**: 26.0.1 |
| const char *manufacturerName | Manufacturer name.<br>**Since**: 26.0.1 |
| const char *productName | Product name.<br>**Since**: 26.0.1 |
| const char *version | Device version.<br>**Since**: 26.0.1 |
| uint16_t vendorId | Vendor ID.<br>**Since**: 26.0.1 |
| uint16_t productId | Product ID.<br>**Since**: 26.0.1 |
| uint8_t clazz | Device class.<br>**Since**: 26.0.1 |
| uint8_t subClass | Device subclass.<br>**Since**: 26.0.1 |
| uint8_t protocol | Device protocol.<br>**Since**: 26.0.1 |
| [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) *configs | Device configuration descriptor information.<br>**Since**: 26.0.1 |
| uint32_t configCount | Number of configurations in the device.<br>**Since**: 26.0.1 |


