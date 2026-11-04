# OH_UsbManager_UsbPipe

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-11-04T01:49:36.706Z pushedAt=2026-11-04T03:10:43.218Z nl=1 -->

```c
typedef struct OH_UsbManager_UsbPipe {...} OH_UsbManager_UsbPipe
```

## Overview

Defines a USB device pipe used to communicate with an opened device.

**Since:** 26.0.1

**Related module:** [UsbManager](capi-usbmanager.md)

**File to include:** [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint8_t busNum | Bus number of the connected device.<br>**Since Version:** 26.0.1 |
| uint8_t devAddress | Device address of the connected device.<br>**Since Version:** 26.0.1 |


