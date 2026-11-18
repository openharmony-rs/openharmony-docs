# OH_UsbManager_UsbInterface

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=9b03c9c06e8d7c4e9f878cb9f5b9f6ff2c1dfdd5 translatedAt=2026-11-04T01:49:32.852Z pushedAt=2026-11-04T03:10:43.216Z nl=1 -->

```c
typedef struct OH_UsbManager_UsbInterface {...} OH_UsbManager_UsbInterface
```

## Overview

Defines a USB interface. An [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) can contain multiple OH_UsbManager_UsbInterface instances, each providing a specific function.

**Since:** 26.0.1

**Related module:** [UsbManager](capi-usbmanager.md)

**File to include:** [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint8_t id | Unique identifier of the USB interface.<br>**Since:** 26.0.1 |
| uint8_t protocol | Interface protocol.<br>**Since:** 26.0.1 |
| uint8_t clazz | Interface class.<br>**Since:** 26.0.1 |
| uint8_t subClass | Interface subclass.<br>**Since:** 26.0.1 |
| uint8_t alternateSetting | Alternate setting number of this USB interface, defined by the USB interface descriptor. The value 0 indicates the default alternate setting.<br>**Since:** 26.0.1 |
| const char *name | Interface name.<br>**Since:** 26.0.1 |
| [OH_UsbManager_UsbEndpoint](capi-usbmanager-oh-usbmanager-usbendpoint.md) *endpoints | Endpoints that belong to this USB interface.<br>**Since:** 26.0.1 |
| uint32_t endpointCount | Number of endpoints in the interface.<br>**Since:** 26.0.1 |


