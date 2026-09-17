# resourcemanager

## Overview

Through the `resourcemanager` module, you can obtain application resources or system resources by resource ID or resource name at the Native layer, enabling resource adaptation for multilingual, multi-device, and multi-screen- density scenarios. Specifically: <br>- Obtaining basic type resources: Obtain basic type resources such as color values (in ARGB format), integers, floating-point numbers, and boolean values. <br>- Obtaining string resources: Obtain plain strings, formatted strings (supporting %d, %s, and %f placeholders), string arrays, and plural strings. <br>- Obtaining media resources: Obtain raw binary data or Base64 encoding of media resources. <br>- Resource overlay: Dynamically load and remove overlay resources at runtime to implement theme switching or resource overlay. <br>This module depends on the `rawfile` module. You must first obtain a **NativeResourceManager** object through the `rawfile` module.

**Since**: 12

## Files

| Name | Description |
| -- | -- |
| [ohresmgr.h](capi-ohresmgr-h.md) | Provides the capability of obtaining resources in the resource management native layer. |
| [resmgr_common.h](capi-resmgr-common-h.md) | Provides the enumeration and structure definitions required by the `resourcemanager` module. <br>This header file defines enumerations such as error codes, screen orientations, color modes, device types, and screen densities, as well as the device configuration structure, providing data type support for the resource retrieval functions in `ohresmgr.h`. |
