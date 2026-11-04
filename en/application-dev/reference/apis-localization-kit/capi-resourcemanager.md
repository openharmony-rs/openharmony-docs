# resourcemanager

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-03T13:37:42.770Z pushedAt=2026-11-04T08:47:59.728Z nl=1 -->

## Overview

The resourcemanager module allows developers to obtain application resources or system resources on the native layer by resource ID or resource name, implementing resource adaptation for multiple languages, devices, and screen densities. Specifically, it includes the following:<br> - Obtaining basic type resources: obtains basic type resources such as color values (in ARGB format), integers, floating-point numbers, and Boolean values.<br> - Obtaining string resources: obtains ordinary strings, formatted strings (supporting %d, %s, and %f placeholders), string arrays, and plural strings.<br> - Obtaining media resources: obtains the raw binary data or Base64 encoding of media resources.<br> - Resource overriding: dynamically loads and removes overlay resources at runtime to implement theme switching or resource overriding.<br> This module depends on the rawfile module. You need to first obtain the [NativeResourceManager](capi-rawfile-nativeresourcemanager.md) object through the rawfile module.

**Since**: 12
## Files

| Name| Description|
| -- | -- |
| [resmgr_common.h](capi-resmgr-common-h.md) | Provides the enum types and struct definitions required by the resourcemanager module.<br> This header file defines the enums such as error codes, screen orientation, color mode, device type, and screen density, as well as the device configuration struct, providing data type support for the resource acquisition functions in ohresmgr.h. |
| [ohresmgr.h](capi-ohresmgr-h.md) | Provides the capability of acquiring resources at the native layer of resource management. |