# OH_UsbManager_UsbDevice

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=896f616b521b29ce2a6a860c2853d35f282f1252 translatedAt=2026-11-04T01:48:24.767Z pushedAt=2026-11-04T03:10:43.213Z nl=1 -->

```c
typedef struct OH_UsbManager_UsbDevice {...} OH_UsbManager_UsbDevice
```

## Overview

Defines the flattened representation of a USB device.

**Since:** 26.0.1

**Related module:** [UsbManager](capi-usbmanager.md)

**File to include:** [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint8_t busNum | Bus number of the USB device.<br>**Since:** 26.0.1 |
| uint8_t devAddress | Address of the device on the bus.<br>**Since:** 26.0.1 |
| const char *name | Device name, in the format of \< bus number \>-\< device address \>.<br>**Since:** 26.0.1 |
| const char *manufacturerName | Manufacturer name.<br>**Since:** 26.0.1 |
| const char *productName | Product name.<br>**Since:** 26.0.1 |
| const char *version | Device version.<br>**Since:** 26.0.1 |
| uint16_t vendorId | Vendor ID.<br>**Since:** 26.0.1 |
| uint16_t productId | Product ID.<br>**Since:** 26.0.1 |
| uint8_t clazz | Device class.<br>**Since:** 26.0.1 |
| uint8_t subClass | Device subclass.<br>**Since:** 26.0.1 |
| uint8_t protocol | Device protocol.<br>**Since:** 26.0.1 |
| [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) *configs | Pointer to the device configuration descriptor information.<br>**Since:** 26.0.1 |
| uint32_t configCount | Number of configurations in the device.<br>**Since:** 26.0.1 |


