# Print_Property
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=cfbd32eaf8f6889081f1f689234b5a5bcadff8c8 translatedAt=2026-11-23T01:13:22.266Z pushedAt=2026-11-23T10:57:55.945Z nl=1 -->

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


