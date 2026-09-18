# ResourceManager_Configuration

```c
typedef struct ResourceManager_Configuration {...} ResourceManager_Configuration
```

## Overview

Structure of the device status.

**Since**: 12

**Related module**: [resourcemanager](capi-resourcemanager.md)

**Header file**: [resmgr_common.h](capi-resmgr-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [ResourceManager_Direction](capi-resmgr-common-h.md#resourcemanager_direction) direction | Screen orientation. |
| char* locale | Language, script, country or region, for example, `zh_Hans_CN`. |
| [ResourceManager_DeviceType](capi-resmgr-common-h.md#resourcemanager_devicetype) deviceType | Device type. |
| [ScreenDensity](capi-resmgr-common-h.md#screendensity) screenDensity | Screen density. |
| [ResourceManager_ColorMode](capi-resmgr-common-h.md#resourcemanager_colormode) colorMode | Color mode. |
| uint32_t mcc | Mobile country code (MCC). |
| uint32_t mnc | Mobile network code (MNC). |
| uint32_t reserved[20] | Reserved attributes. |


