# OH_UsbManager_UsbConfig

```c
typedef struct OH_UsbManager_UsbConfig {...} OH_UsbManager_UsbConfig
```

## Overview

Defines a USB configuration. One {@link OH_UsbManager_UsbDevice} can contain multiple <br>**OH_UsbManager_UsbConfig** instances.

**System capability**: SystemCapability.USB.USBManager

**Since**: 26.0.1

**Related module**: [UsbManager](capi-usbmanager.md)

**Header file**: [ohusb_manager.h](capi-ohusb-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t id | Unique ID of the USB configuration.<br>**Since**: 26.0.1 |
| uint8_t attributes | Configuration attributes.<br>**Since**: 26.0.1 |
| uint8_t maxPower | Maximum power consumption. Unit: mA.<br>**Since**: 26.0.1 |
| const char *name | Configuration name, which can be left empty.<br>**Since**: 26.0.1 |
| bool isRemoteWakeup | Whether remote wakeup is supported. true indicates that remote wakeup is supported; <br>false indicates the opposite.<br>**Since**: 26.0.1 |
| bool isSelfPowered | Whether an independent power supply is supported. true indicates that an independent <br>power supply is supported; false indicates the opposite.<br>**Since**: 26.0.1 |
| [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md) *interfaces | Supported interface attributes.<br>**Since**: 26.0.1 |
| uint32_t interfaceCount | Number of interfaces in the configuration.<br>**Since**: 26.0.1 |


