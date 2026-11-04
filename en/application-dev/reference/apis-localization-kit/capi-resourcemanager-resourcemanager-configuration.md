# ResourceManager_Configuration

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-04T04:08:33.272Z pushedAt=2026-11-04T10:13:14.908Z nl=1 -->

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
| [ResourceManager_Direction](capi-resmgr-common-h.md#screendensity) direction | Screen direction. |
| char* locale | Language, script, country, or region, for example, zh_Hans_CN. |
| [ResourceManager_DeviceType](capi-resmgr-common-h.md#resourcemanager_devicetype) deviceType | Device type. |
| [ScreenDensity](capi-resmgr-common-h.md#screendensity) screenDensity | Screen density. |
| [ResourceManager_ColorMode](capi-resmgr-common-h.md#resourcemanager_direction) colorMode | Color mode. |
| uint32_t mcc | Mobile country code (MCC).|
| uint32_t mnc | Mobile network code (MNC).|
| uint32_t reserved[20] | Reserved.|


