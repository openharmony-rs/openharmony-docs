# Usb_NonRootHubArray

```c
struct Usb_NonRootHubArray {...}
```

## Overview

The list of non-root hubs, which is used to store the non-root hub IDs and quantity obtained using [OH_Usb_GetNonRootHubs](capi-usb-ddk-api-h.md#oh_usb_getnonroothubs).

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 26.0.0

**Related module**: [UsbDdk](capi-others-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t* nonRootHubIds | Array of non-root hub device IDs. The non-root USB hub device ID is constructed by left-shifting the bus number by 32 bits and adding the device address.<br>**Since**: 26.0.0 |
| uint32_t num | Number of non-root hubs. If the value is 0, no non-root hubs are present.<br>**Since**: 26.0.0 |


