# OH_UsbManager_UsbEndpoint

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4783193a2c38a164702de1ebb6fd94773c15aff1 translatedAt=2026-11-09T10:21:23.403Z pushedAt=2026-11-09T10:56:23.517Z nl=1 -->

```c
typedef struct OH_UsbManager_UsbEndpoint {...} OH_UsbManager_UsbEndpoint
```

## Overview

Defines a USB endpoint used to send or receive data. The endpoint is obtained from [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md).

**Since:** 26.0.1

**Related module:** [UsbManager](capi-usbmanager.md)

**File to include:** [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint8_t address | Endpoint address.<br>**Since:** 26.0.1 |
| uint8_t attributes | Endpoint attributes.<br>**Since:** 26.0.1 |
| uint8_t interval | Data transfer interval of the endpoint. For an interrupt endpoint, the unit is millisecond. For an isochronous endpoint, the unit depends on the device speed.<br>**Since:** 26.0.1 |
| uint16_t maxPacketSize | Maximum size of a data packet on the endpoint, in bytes.<br>**Since:** 26.0.1 |
| [OH_UsbManager_RequestDirection](capi-ohusb-manager-h.md#oh_usbmanager_requestdirection) direction | Endpoint direction.<br>**Since:** 26.0.1 |
| uint8_t number | Endpoint number.<br>**Since:** 26.0.1 |
| uint8_t type | Endpoint type.<br>**Since:** 26.0.1 |
| uint8_t interfaceId | Unique identifier of the interface to which the endpoint belongs.<br>**Since:** 26.0.1 |


