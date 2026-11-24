# OH_UsbManager_UsbDevice

```c
typedef struct OH_UsbManager_UsbDevice {...} OH_UsbManager_UsbDevice
```

## Overview

Defines a flat representation of a USB device.

<!--Device-struct OH_UsbManager_UsbDevice {...}--><!--Device-struct OH_UsbManager_UsbDevice {...}-End-->

**System capability**: SystemCapability.USB.USBManager

**Since**: 26.0.1

**Related module**: [UsbManager](capi-basic-services-kit-usbmanager.md)

**Header file**: [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t busNum | Bus number of the USB device.<br>**Since**: 26.0.1<br><!--Device-uint8_t busNum--><!--Device-uint8_t busNum-End--> |
| uint8_t devAddress | Device address on the bus.<br>**Since**: 26.0.1<br><!--Device-uint8_t devAddress--><!--Device-uint8_t devAddress-End--> |
| const char *name | Device name, in the format of <bus number>-<device address>.<br>**Since**: 26.0.1<br><!--Device-const char *name--><!--Device-const char *name-End--> |
| const char *manufacturerName | Manufacturer name.<br>**Since**: 26.0.1<br><!--Device-const char *manufacturerName--><!--Device-const char *manufacturerName-End--> |
| const char *productName | Product name.<br>**Since**: 26.0.1<br><!--Device-const char *productName--><!--Device-const char *productName-End--> |
| const char *version | Device version.<br>**Since**: 26.0.1<br><!--Device-const char *version--><!--Device-const char *version-End--> |
| uint16_t vendorId | Vendor ID.<br>**Since**: 26.0.1<br><!--Device-uint16_t vendorId--><!--Device-uint16_t vendorId-End--> |
| uint16_t productId | Product ID.<br>**Since**: 26.0.1<br><!--Device-uint16_t productId--><!--Device-uint16_t productId-End--> |
| uint8_t clazz | Device class.<br>**Since**: 26.0.1<br><!--Device-uint8_t clazz--><!--Device-uint8_t clazz-End--> |
| uint8_t subClass | Device subclass.<br>**Since**: 26.0.1<br><!--Device-uint8_t subClass--><!--Device-uint8_t subClass-End--> |
| uint8_t protocol | Device protocol.<br>**Since**: 26.0.1<br><!--Device-uint8_t protocol--><!--Device-uint8_t protocol-End--> |
| [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) *configs | Device configuration descriptor information.<br>**Since**: 26.0.1<br><!--Device-OH_UsbManager_UsbConfig *configs--><!--Device-OH_UsbManager_UsbConfig *configs-End--> |
| uint32_t configCount | Number of configurations in the device.<br>**Since**: 26.0.1<br><!--Device-uint32_t configCount--><!--Device-uint32_t configCount-End--> |


