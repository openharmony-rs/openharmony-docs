# Print_Property
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=8ee0eefda2c8f7c51afc8d61427d4e7289d6c89f translatedAt=2026-11-12T03:59:22.292Z pushedAt=2026-11-12T12:12:09.327Z nl=1 -->

```cpp
typedef struct {...} Print_Property
```

## Overview

Describes the printer properties in key-value pair format. You can use this struct to obtain or set printer properties.

**Since**: 12

**Related module**: [Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *key | Property key, which identifies the type of a printer property. The value must be a valid property name defined in the [Print](capi-oh-print.md) module. |
| char *value | Property value, which corresponds to the property key. The format and valid range of the value depend on the corresponding property key. |


