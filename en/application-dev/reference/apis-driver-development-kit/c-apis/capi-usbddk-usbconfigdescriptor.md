# UsbConfigDescriptor

```c
struct UsbConfigDescriptor {...}
```

## Overview

Defines standard configuration descriptors, which correspond to **Standard Configuration Descriptor** in the USB protocol.

<!--Device-struct UsbConfigDescriptor {...}--><!--Device-struct UsbConfigDescriptor {...}-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t bLength | Size of the descriptor, in bytes.<br><!--Device-uint8_t bLength--><!--Device-uint8_t bLength-End--> |
| uint8_t bDescriptorType | Descriptor type.<br><!--Device-uint8_t bDescriptorType--><!--Device-uint8_t bDescriptorType-End--> |
| uint16_t wTotalLength | Total length of the configuration descriptor, in bytes, including the configuration, interface, endpoint, and class- or vendor-specific descriptors.<br><!--Device-uint16_t wTotalLength--><!--Device-uint16_t wTotalLength-End--> |
| uint8_t bNumInterfaces | Number of interfaces supported by the configuration.<br><!--Device-uint8_t bNumInterfaces--><!--Device-uint8_t bNumInterfaces-End--> |
| uint8_t bConfigurationValue | Configuration index, which is used to select the configuration.<br><!--Device-uint8_t bConfigurationValue--><!--Device-uint8_t bConfigurationValue-End--> |
| uint8_t iConfiguration | Index of the string descriptor that describes the configuration.<br><!--Device-uint8_t iConfiguration--><!--Device-uint8_t iConfiguration-End--> |
| uint8_t bmAttributes | Configuration attributes, including the power mode and remote wakeup.<br><!--Device-uint8_t bmAttributes--><!--Device-uint8_t bmAttributes-End--> |
| uint8_t bMaxPower | Maximum power consumption of the bus-powered USB device, in 2 mA.<br><!--Device-uint8_t bMaxPower--><!--Device-uint8_t bMaxPower-End--> |


