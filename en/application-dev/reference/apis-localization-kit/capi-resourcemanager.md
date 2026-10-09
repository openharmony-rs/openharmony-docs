# resourcemanager

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:22:16.684Z pushedAt=2026-07-17T03:17:03.525Z -->

## Overview

Through the `resourcemanager` module, you can obtain application resources or system resources by resource ID or resource name at the Native layer, enabling resource adaptation for multilingual, multi-device, and multi-screen-density scenarios. Specifically:<br> - Obtaining basic type resources: Obtain basic type resources such as color values (in ARGB format), integers, floating-point numbers, and boolean values.<br> - Obtaining string resources: Obtain plain strings, formatted strings (supporting %d, %s, and %f placeholders), string arrays, and plural strings.<br> - Obtaining media resources: Obtain raw binary data or Base64 encoding of media resources.<br> - Resource overlay: Dynamically load and remove overlay resources at runtime to implement theme switching or resource overlay.<br> This module depends on the `rawfile` module. You must first obtain a [NativeResourceManager](capi-rawfile-nativeresourcemanager.md) object through the `rawfile` module.

**Since**: 12

## Files

| Name| Description|
| -- | -- |
| [resmgr_common.h](capi-resmgr-common-h.md) | Provides definitions of the enumerated types and structures required by the `resourcemanager` module.<br> This header file defines enumerations such as error codes, screen orientations, color modes, device types, and screen densities, as well as device configuration structures, offering data type support for the resource retrieval functions in `ohresmgr.h`. |
| [ohresmgr.h](capi-ohresmgr-h.md) | Provides the capability to retrieve resources at the native layer of resource management. |