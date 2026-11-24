# OH_UsbManager_UsbConfig

```c
typedef struct OH_UsbManager_UsbConfig {...} OH_UsbManager_UsbConfig
```

## Overview

Defines a USB configuration. One [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) can contain multiple <br>**OH_UsbManager_UsbConfig** instances.

<!--Device-struct OH_UsbManager_UsbConfig {...}--><!--Device-struct OH_UsbManager_UsbConfig {...}-End-->

**System capability**: SystemCapability.USB.USBManager

**Since**: 26.0.1

**Related module**: [UsbManager](capi-basic-services-kit-usbmanager.md)

**Header file**: [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t id | Unique ID of the USB configuration.<br>**Since**: 26.0.1<br><!--Device-uint8_t id--><!--Device-uint8_t id-End--> |
| uint8_t attributes | Configuration attributes.<br>**Since**: 26.0.1<br><!--Device-uint8_t attributes--><!--Device-uint8_t attributes-End--> |
| uint8_t maxPower | Maximum power consumption. Unit: mA.<br>**Since**: 26.0.1<br><!--Device-uint8_t maxPower--><!--Device-uint8_t maxPower-End--> |
| const char *name | Configuration name, which can be left empty.<br>**Since**: 26.0.1<br><!--Device-const char *name--><!--Device-const char *name-End--> |
| bool isRemoteWakeup | Whether remote wakeup is supported. true indicates that remote wakeup is supported; <br>false indicates the opposite.<br>**Since**: 26.0.1<br><!--Device-bool isRemoteWakeup--><!--Device-bool isRemoteWakeup-End--> |
| bool isSelfPowered | Whether an independent power supply is supported. true indicates that an independent <br>power supply is supported; false indicates the opposite.<br>**Since**: 26.0.1<br><!--Device-bool isSelfPowered--><!--Device-bool isSelfPowered-End--> |
| [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md) *interfaces | Supported interface attributes.<br>**Since**: 26.0.1<br><!--Device-OH_UsbManager_UsbInterface *interfaces--><!--Device-OH_UsbManager_UsbInterface *interfaces-End--> |
| uint32_t interfaceCount | Number of interfaces in the configuration.<br>**Since**: 26.0.1<br><!--Device-uint32_t interfaceCount--><!--Device-uint32_t interfaceCount-End--> |


