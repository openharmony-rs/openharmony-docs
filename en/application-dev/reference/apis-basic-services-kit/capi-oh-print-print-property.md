# Print_Property
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=aba42e15abed86996b578549f00ed4ce1a370af8 translatedAt=2026-09-01T03:09:44.879Z pushedAt=2026-09-03T11:38:28.547Z -->

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


