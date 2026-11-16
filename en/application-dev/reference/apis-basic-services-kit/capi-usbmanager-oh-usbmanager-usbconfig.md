# OH_UsbManager_UsbConfig

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=9b03c9c06e8d7c4e9f878cb9f5b9f6ff2c1dfdd5 translatedAt=2026-11-04T01:48:33.539Z pushedAt=2026-11-04T03:10:43.215Z nl=1 -->

```c
typedef struct OH_UsbManager_UsbConfig {...} OH_UsbManager_UsbConfig
```

## Overview

Defines a USB configuration. An [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) can contain multiple<br>**OH_UsbManager_UsbConfig** instances.

**Since:** 26.0.1

**Related module:** [UsbManager](capi-usbmanager.md)

**File to include:** [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint8_t id | Unique ID of the USB configuration.<br>**Since:** 26.0.1 |
| uint8_t attributes | Configuration attributes.<br>**Since:** 26.0.1 |
| uint8_t maxPower | Maximum power consumption, in mA.<br>**Since:** 26.0.1 |
| const char *name | Configuration name, which can be empty.<br>**Since:** 26.0.1 |
| bool isRemoteWakeup | Whether remote wakeup is supported. The value true means remote wakeup is supported, and false means the opposite.<br>**Since:** 26.0.1 |
| bool isSelfPowered | Whether self-powered is supported. The value true means self-powered is supported, and false means the opposite.<br>**Since:** 26.0.1 |
| [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md) *interfaces | Supported interface attributes.<br>**Since:** 26.0.1 |
| uint32_t interfaceCount | Number of interfaces in the configuration.<br>**Since:** 26.0.1 |


