# OH_UsbManager_UsbEndpoint

```c
typedef struct OH_UsbManager_UsbEndpoint {...} OH_UsbManager_UsbEndpoint
```

## Overview

Defines the USB endpoint from which data is sent or received. An endpoint <br>is obtained from [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md).

**Since**: 26.1.0

**Related module**: [UsbManager](capi-usbmanager.md)

**Header file**: [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t address | Endpoint address.<br>**Since**: 26.1.0 |
| uint8_t attributes | Endpoint attributes.<br>**Since**: 26.1.0 |
| uint8_t interval | Endpoint interval for data transfers. For interrupt endpoints, the value <br>is in milliseconds. For isochronous endpoints, the unit depends on the <br>device speed.<br>**Since**: 26.1.0 |
| uint16_t maxPacketSize | Maximum size of data packets on the endpoint. Unit: bytes.<br>**Since**: 26.1.0 |
| [OH_UsbManager_RequestDirection](capi-ohusb-manager-h.md#oh_usbmanager_requestdirection) direction | Endpoint direction.<br>**Since**: 26.1.0 |
| uint8_t number | Endpoint number.<br>**Since**: 26.1.0 |
| uint8_t type | Endpoint type.<br>**Since**: 26.1.0 |
| uint8_t interfaceId | Unique ID of the interface to which the endpoint belongs.<br>**Since**: 26.1.0 |


