# resourcemanager

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-04T04:09:07.434Z pushedAt=2026-11-04T10:13:14.910Z nl=1 -->

## Overview

With the resourcemanager module, developers can obtain application resources or system resources on the native layer by resource ID or resource name, adapting resources to multiple languages, devices, and screen densities. Specifically, it includes the following:<br> - Obtaining basic resources: obtains basic resources such as color values (in ARGB format), integers, floating-point numbers, and Boolean values.<br> - Obtaining string resources: obtains ordinary strings, formatted strings (supporting the %d, %s, and %f placeholders), string arrays, and plural strings.<br> - Obtaining media resources: obtains the raw binary data or Base64 encoding of media resources.<br> - Resource overlay: dynamically loads and removes overlay resources at runtime to implement theme switching or resource overriding.<br> This module depends on the rawfile module. You must first obtain a [NativeResourceManager](capi-rawfile-nativeresourcemanager.md) object through the rawfile module.

**Since**: 12
## Files

| Name| Description|
| -- | -- |
| [resmgr_common.h](capi-resmgr-common-h.md) | Provides the enum types and struct definitions required by the resourcemanager module.<br> This header file defines enums such as error codes, screen orientation, color mode, device type, and screen density, as well as the device configuration struct, providing data type support for the resource obtaining functions in ohresmgr.h. |
| [ohresmgr.h](capi-ohresmgr-h.md) | Provides the capability of obtaining resources on the native layer of resource management. |