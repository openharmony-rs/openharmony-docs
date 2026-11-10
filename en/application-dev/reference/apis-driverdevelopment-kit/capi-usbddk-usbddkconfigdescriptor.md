# UsbDdkConfigDescriptor
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-10T01:11:39.096Z pushedAt=2026-11-10T01:48:15.376Z nl=1 -->

```c
typedef struct UsbDdkConfigDescriptor {...} UsbDdkConfigDescriptor
```

## Overview

Configuration descriptor, which contains information such as the standard configuration descriptor and interface descriptor.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [struct UsbConfigDescriptor](capi-usbddk-usbconfigdescriptor.md) configDescriptor | Standard configuration descriptor.|
| [struct UsbDdkInterface](capi-usbddk-usbddkinterface.md)* interface | Interfaces contained in the configuration.|
| const uint8_t* extra | Pointer to the unparsed descriptor, which contains class-specific or vendor-specific descriptors. |
| uint32_t extraLength | Length of the unresolved descriptor.|


