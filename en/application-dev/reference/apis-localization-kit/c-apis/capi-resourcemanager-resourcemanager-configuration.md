# ResourceManager_Configuration

```c
typedef struct ResourceManager_Configuration {...} ResourceManager_Configuration
```

## Overview

Structure of the device status.

<!--Device-struct ResourceManager_Configuration {...}--><!--Device-struct ResourceManager_Configuration {...}-End-->

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 12

**Related module**: [resourcemanager](capi-localization-kit-resourcemanager.md)

**Header file**: [resmgr_common.h](capi-resmgr-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [ResourceManager_Direction](capi-resmgr-common-h.md#resourcemanager_direction) direction | Screen orientation.<br><!--Device-ResourceManager_Direction direction--><!--Device-ResourceManager_Direction direction-End--> |
| char* locale | Language, script, country or region, for example, `zh_Hans_CN`.<br><!--Device-char* locale--><!--Device-char* locale-End--> |
| [ResourceManager_DeviceType](capi-resmgr-common-h.md#resourcemanager_devicetype) deviceType | Device type.<br><!--Device-ResourceManager_DeviceType deviceType--><!--Device-ResourceManager_DeviceType deviceType-End--> |
| [ScreenDensity](capi-resmgr-common-h.md#screendensity) screenDensity | Screen density.<br><!--Device-ScreenDensity screenDensity--><!--Device-ScreenDensity screenDensity-End--> |
| [ResourceManager_ColorMode](capi-resmgr-common-h.md#resourcemanager_colormode) colorMode | Color mode.<br><!--Device-ResourceManager_ColorMode colorMode--><!--Device-ResourceManager_ColorMode colorMode-End--> |
| uint32_t mcc | Mobile country code (MCC).<br><!--Device-uint32_t mcc--><!--Device-uint32_t mcc-End--> |
| uint32_t mnc | Mobile network code (MNC).<br><!--Device-uint32_t mnc--><!--Device-uint32_t mnc-End--> |
| uint32_t reserved[20] | Reserved attributes.<br><!--Device-uint32_t reserved[20]--><!--Device-uint32_t reserved[20]-End--> |


