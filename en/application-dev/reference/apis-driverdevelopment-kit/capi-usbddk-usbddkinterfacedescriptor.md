# UsbDdkInterfaceDescriptor
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-10T01:11:48.451Z pushedAt=2026-11-10T01:49:04.026Z nl=1 -->

```c
typedef struct UsbDdkInterfaceDescriptor {...} UsbDdkInterfaceDescriptor
```

## Overview

Interface descriptor, which contains information such as the standard interface descriptor and endpoint descriptors.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [struct UsbInterfaceDescriptor](capi-usbddk-usbinterfacedescriptor.md) interfaceDescriptor | Standard USB interface descriptor.|
| [struct UsbDdkEndpointDescriptor](capi-usbddk-usbddkendpointdescriptor.md)* endPoint | Pointer to the endpoint descriptor contained in this interface. A null pointer indicates that there is no endpoint (excluding control endpoint 0). |
| const uint8_t* extra | Pointer to the unparsed descriptor, which contains class-specific or vendor-specific descriptors. |
| uint32_t extraLength | Length of the unresolved descriptor.|


