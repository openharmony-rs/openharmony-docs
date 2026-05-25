# Usb_NonRootHubArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct Usb_NonRootHubArray {...} Usb_NonRootHubArray
```

## Overview

Non-root hub list, which is used to store the non-root hub IDs and quantity obtained using **OH_Usb_GetNonRootHubs**.

**Since**: 26.0.0

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t* nonRootHubIds | Start address of the non-root hub ID array. It is recommended that the number of non-root hub IDs do not exceed 128 to prevent excessive memory usage. The device ID of a non-root USB hub is contructed by left-shifting its bus number by 32 bits and adding it to its device address.|
| uint32_t num | Number of returned non-root hubs. The system traverses **nonRootHubIds** to obtain the non-root hub ID based on the number. If the value is **0**, no non-root hub exists.|
