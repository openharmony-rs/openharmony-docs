# Print_PropertyList
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=8ee0eefda2c8f7c51afc8d61427d4e7289d6c89f translatedAt=2026-11-12T03:59:48.516Z pushedAt=2026-11-12T12:12:17.557Z nl=1 -->

```cpp
typedef struct {...} Print_PropertyList
```

## Overview

Defines a printer property list, which is used to store and manage printer properties. You can access and operate printer properties in batches by using the property count and the pointer to the property array. **count** indicates the number of properties, and **list** is a pointer to the property array. The two parameters together indicate a complete set of printer properties, which is applicable to scenarios where multiple printer properties need to be queried or set.

**Since**: 12

**Related module**: [Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t count | Number of properties. The value must be the same as the actual number of elements in the property array to which **list** points. |
| [Print_Property](capi-oh-print-print-property.md) \*list | Pointer to the property array, which is used to store printer properties. This parameter must be used together with **count**. The array length is specified by **count**. |


