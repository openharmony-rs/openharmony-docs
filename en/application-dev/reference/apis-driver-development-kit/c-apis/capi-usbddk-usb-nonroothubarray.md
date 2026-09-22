# Usb_NonRootHubArray

```c
typedef struct Usb_NonRootHubArray {...} Usb_NonRootHubArray
```

## Overview

The list of non-root hubs, which is used to store the non-root hub IDs and quantity obtained using {@link OH_Usb_GetNonRootHubs}.

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 26.0.0

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t* nonRootHubIds |  |
| uint32_t num |  |


