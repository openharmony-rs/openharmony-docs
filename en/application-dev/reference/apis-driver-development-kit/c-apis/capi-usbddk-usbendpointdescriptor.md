# UsbEndpointDescriptor

```c
struct UsbEndpointDescriptor {...}
```

## Overview

Defines standard endpoint descriptors, which correspond to **Standard Endpoint Descriptor** in the USB protocol.

<!--Device-struct UsbEndpointDescriptor {...}--><!--Device-struct UsbEndpointDescriptor {...}-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t bLength | Size of this descriptor, in bytes.<br><!--Device-uint8_t bLength--><!--Device-uint8_t bLength-End--> |
| uint8_t bDescriptorType | Descriptor type.<br><!--Device-uint8_t bDescriptorType--><!--Device-uint8_t bDescriptorType-End--> |
| uint8_t bEndpointAddress | Endpoint address, including the endpoint number and endpoint direction.<br><!--Device-uint8_t bEndpointAddress--><!--Device-uint8_t bEndpointAddress-End--> |
| uint8_t bmAttributes | Endpoint attributes, including the transfer type, synchronization type, and usage type.<br><!--Device-uint8_t bmAttributes--><!--Device-uint8_t bmAttributes-End--> |
| uint16_t wMaxPacketSize | Maximum packet size supported by an endpoint, in bytes.<br><!--Device-uint16_t wMaxPacketSize--><!--Device-uint16_t wMaxPacketSize-End--> |
| uint8_t bInterval | Interval for polling endpoints for data transfer.<br><!--Device-uint8_t bInterval--><!--Device-uint8_t bInterval-End--> |
| uint8_t bRefresh | Refresh rate for audio devices.<br><!--Device-uint8_t bRefresh--><!--Device-uint8_t bRefresh-End--> |
| uint8_t bSynchAddress | Endpoint synchronization address for audio devices.<br><!--Device-uint8_t bSynchAddress--><!--Device-uint8_t bSynchAddress-End--> |


