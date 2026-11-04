# ResourceManager_Configuration

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-03T13:34:36.484Z pushedAt=2026-11-04T08:47:59.725Z nl=1 -->

```c
typedef struct ResourceManager_Configuration {...} ResourceManager_Configuration
```

## Overview

Describes the device status.

**Since**: 12

**Related module**: [resourcemanager](capi-resourcemanager.md)

**Header file**: [resmgr_common.h](capi-resmgr-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [ResourceManager_Direction](capi-resmgr-common-h.md#screendensity) direction | Indicates the screen direction. |
| char* locale | Indicates the language, script, country, or region, for example, zh_Hans_CN. |
| [ResourceManager_DeviceType](capi-resmgr-common-h.md#resourcemanager_devicetype) deviceType | Indicates the device type. |
| [ScreenDensity](capi-resmgr-common-h.md#screendensity) screenDensity | Indicates the screen density. |
| [ResourceManager_ColorMode](capi-resmgr-common-h.md#resourcemanager_direction) colorMode | Indicates the color mode. |
| uint32_t mcc | Mobile country code (MCC).|
| uint32_t mnc | Mobile network code (MNC).|
| uint32_t reserved[20] | Reserved.|


