# Usb_NonRootHubArray

```c
typedef struct Usb_NonRootHubArray {...} Usb_NonRootHubArray
```

## Overview

Defines the non-root hub array, which is used to store the non-root hub IDs and quantity obtained using [OH_Usb_GetNonRootHubs](capi-usb-ddk-api-h.md#oh_usb_getnonroothubs). After using the structure, you must release the memory allocated for the non-root hub ID array. Otherwise, resource leaks may occur.

<!--Device-struct Usb_NonRootHubArray {...}--><!--Device-struct Usb_NonRootHubArray {...}-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 26.0.0

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t* nonRootHubIds | Start address of the non-root hub ID array. It is recommended that the number of non-root hub IDs not exceed 128 to prevent excessive memory usage. The device ID of a non-root USB hub is constructed by left-shifting its bus number by 32 bits and adding it to its device address. |
| uint32_t num | Number of returned non-root hubs. The system traverses **nonRootHubIds** to obtain the non-root hub ID based on the number. If the value is **0**, no non-root hub exists. |


