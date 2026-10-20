# Print_Property
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=f172f47675a58f89bb693013f28ad2465486c311 translatedAt=2026-10-09T11:44:05.762Z pushedAt=2026-10-10T03:46:22.271Z -->

```cpp
typedef struct {...} Print_Property
```

## Overview

Describes the printer properties in key-value pair format. You can use this struct to obtain or set printer properties.

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *key | Property key, which identifies the type of a printer property. The value must be a valid property name defined in the [OH_Print](capi-oh-print.md) module. |
| char *value | Property value, which corresponds to the property key. The format and valid range of the value depend on the corresponding property key. |


