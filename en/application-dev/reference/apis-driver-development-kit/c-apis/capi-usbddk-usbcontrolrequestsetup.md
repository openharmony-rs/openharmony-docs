# UsbControlRequestSetup

```c
struct UsbControlRequestSetup {...}
```

## Overview

Setup data for control transfer. It corresponds to <b>Setup Data</b> in the USB protocol.

<!--Device-struct UsbControlRequestSetup {...}--><!--Device-struct UsbControlRequestSetup {...}-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t bmRequestType | Request type.<br><!--Device-uint8_t bmRequestType--><!--Device-uint8_t bmRequestType-End--> |
| uint8_t bRequest | Specific request.<br><!--Device-uint8_t bRequest--><!--Device-uint8_t bRequest-End--> |
| uint16_t wValue | Value corresponding to **wValue** in the USB protocol. Its meaning varies according to the request.<br><!--Device-uint16_t wValue--><!--Device-uint16_t wValue-End--> |
| uint16_t wIndex | Index corresponding to **wIndex** in the USB protocol. It is usually used to pass the index or offset. Its meaning varies according to the request.<br><!--Device-uint16_t wIndex--><!--Device-uint16_t wIndex-End--> |
| uint16_t wLength | Data length corresponding to **wLength** in the USB protocol. If data is transferred, this field indicates the number of transferred bytes.<br><!--Device-uint16_t wLength--><!--Device-uint16_t wLength-End--> |


